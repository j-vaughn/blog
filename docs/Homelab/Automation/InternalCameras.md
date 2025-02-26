# Internal Camera Privacy

*February 24, 2025*

My family has gotten on board with the idea of indoor cameras in common areas for checking in on the dog, the kids in other parts of the house, or exceptional situations (alarms, etc...), but prefer not to be recorded 24/7. I set out to implement a solution using [Home Assistant](https://www.home-assistant.io/). Here's my thought process and what I ended up doing.

## Possible Solutions

Initially, I considered a few different options:

- **Leaving the cameras on all the time** – This provided full monitoring but compromised privacy.
- **Using pan/tilt cameras to point away from the main part of the room when "disabled"** – We found that this method wasn't good for the cameras, as two of our Amcrest cameras experienced mechanical failure after about a year and a half.
- **Automating the camera's power via API calls to their switches to turn PoE on/off** – This introduced delays, as we had to wait for the cameras to boot up when we wanted to check in. A similar approach could be used with smart plugs for non-PoE cameras, but it still involved delays.

Each of these options had drawbacks, so I looked for a more practical solution.

## What I Ended Up Doing

I found a compromise by automating the application and removal of a full-screen privacy mask, which allows us to maintain privacy without completely losing the ability to monitor our home when necessary. This approach proved to be more reliable and convenient than physically adjusting camera angles or waiting for them to reboot when power is toggled.

In Home Assistant, I added a helper toggle that triggers an automation to enable or disable privacy on the cameras via a `rest_command` service call. This allows us to view the camera's privacy state on our phones and dashboards and get notified if the privacy state changes manually.

### Controlling the Privacy Masks

To create and enable the mask, I used this API call to our Hikvision cameras (don't worry, they're segmented accordingly!). The `x=704` setting prevents a thin visible line from appearing on the video compared to `x=700`:

```
rest_command:
  hik_privacy_enable_kitchen:
    url: http://192.168.xx.yy/ISAPI/System/Video/inputs/channels/1/privacyMask/
    method: PUT
    headers:
      authorization: "Basic <<AUTH STRING>>"
    payload: >
      <PrivacyMask><enabled>true</enabled>
      <normalizedScreenSize><normalizedScreenWidth>700</normalizedScreenWidth>
      <normalizedScreenHeight>480</normalizedScreenHeight></normalizedScreenSize>
      <PrivacyMaskRegionList>
      <PrivacyMaskRegion xmlns="">
      <id>1</id>
      <enabled>true</enabled>
      <RegionCoordinatesList>
        <RegionCoordinates><positionX>0</positionX><positionY>0</positionY></RegionCoordinates>
        <RegionCoordinates><positionX>704</positionX><positionY>0</positionY></RegionCoordinates>
        <RegionCoordinates><positionX>704</positionX><positionY>480</positionY></RegionCoordinates>
        <RegionCoordinates><positionX>0</positionX><positionY>480</positionY></RegionCoordinates>
      </RegionCoordinatesList>
      </PrivacyMaskRegion>
      </PrivacyMaskRegionList>
      </PrivacyMask>
```

And similarly, to disable, this API call:

```
rest_command:
  hik_privacy_disable_kitchen:
    url: http://192.168.xx.yy/ISAPI/System/Video/inputs/channels/1/privacyMask/
    method: PUT
    headers:
      authorization: "Basic <AUTH STRING>"
    payload: "<PrivacyMask><enabled>false</enabled></PrivacyMask>"
```

Then, so that it was clear that the camera was supposed to be in this state instead of just blacked out, I added a text overlay with `Camera Disabled` in the middle of the screen.

To create and enable the text overlay: 

```yaml
rest_command:
  hik_privacy_enable_text:
    url: http://192.168.xx.yy/ISAPI/System/Video/inputs/channels/1/overlays
    method: PUT
    headers:
      authorization: "Basic <AUTH STRING>"
    payload: >
      <VideoOverlay>
      <TextOverlayList>
      <TextOverlay>
      <id>1</id><enabled>true</enabled><displayText>Camera Disabled</displayText><positionX>228</positionX><positionY>288</positionY>
      </TextOverlay>
      </TextOverlayList>
      </VideoOverlay>
```

And, to disable the text overlay:

```yaml
rest_command:
    hik_privacy_disable_text:
        url: http://192.168.xx.yy/ISAPI/System/Video/inputs/channels/1/overlays
        method: PUT
        headers:
          authorization: "Basic <AUTH STRING>"
        payload: >
          <VideoOverlay>
          <TextOverlayList>
          <TextOverlay>
          <id>1</id><enabled>false</enabled>
          </TextOverlay>
          </TextOverlayList>
          </VideoOverlay>
```



I created these commands for each interior camera and then built a Home Assistant script to globally enable/disable privacy masks and overlay text by calling these RESTful commands.

Putting it all together, this is what it looks like when you try to view a camera that is disabled:

![cams_off](img\cams_off.png)

### Automating Camera Privacy Control

I added an automation that maps the toggle helper to the scripts and sends notifications when privacy is manually disabled to ensure transparency among family members. Initially, there were some challenges in configuring the notifications to trigger only when privacy was manually disabled rather than during automation events, but fine-tuning the conditions resolved this issue.

```
alias: Camera Privacy Control
description: ""
trigger:
  - platform: state
    entity_id:
      - input_boolean.camera_privacy
    id: trigger
condition: []
action:
  - if:
      - condition: state
        entity_id: input_boolean.camera_privacy
        state: "on"
    then:
      - service: script.home_indoor_cameras_privacy_on
        continue_on_error: true
        metadata: {}
        data: {}
    else:
      - service: script.home_indoor_cameras_privacy_off
        continue_on_error: true
        data: {}
      - if:
          - condition: template
            value_template: "{{ trigger.to_state.context.user_id != none }}"
        then:
          - service: script.notify_users_at_home
            metadata: {}
            data:
              message: Indoor camera privacy has been disabled.
mode: single
```

The template `{{ trigger.to_state.context.user_id != none }}` ensures that notifications are only sent when someone manually disables privacy from the Home Assistant UI. This prevents unnecessary alerts when the cameras turn on as part of our automations (leaving, alarm triggered, etc...).

The script `notify_users_at_home` checks for users listed as home and sends notifications accordingly, avoiding unnecessary notifications for people that are not home.



![camera-privacy](img\camera-privacy.png)

## Conclusion

After several months of using this automated privacy mask setup, the results have been excellent. We can check on the house when needed without the cameras feeling intrusive while we’re home. Being able to check the cameras' status in real-time gives us peace of mind while ensuring we can monitor our home when needed.

This setup strikes a perfect balance between security and comfort for us, reducing concerns about constant surveillance, providing greater control over when cameras are active, and integrating into our daily routines.