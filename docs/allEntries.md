# All Blog Entries

## [Repurposing a Commercial Mass Notification Device for Custom Use](/blog/Homelab/Hardware/RepurposingAMassNotificationAppliance/) (April 29, 2025)

*This post documents how I repurposed a commercial mass notification device—originally designed for emergency alerts—into a usable component of my Raspberry Pi–based intercom system. I walk through hardware inspection, offline firmware analysis, and ultimately bootstrapping the unit with a clean TI Linux image. Along the way, I highlight key findings around security posture, GPIO mapping, and system architecture. It’s a hands-on teardown that blends hardware forensics with practical reuse.*

## [Porting My C# Console App to Python Using ChatGPT](/blog/Software/IntercomSystemFlask) (April 10, 2025)

*After retiring a Windows-based C# app that controlled intercom announcements, I challenged myself to rebuild it entirely in Python—without writing a single line of code. This post documents how I used ChatGPT to generate a fully functional Flask web app, handling everything from routing to UI templates through conversational prompts. It highlights the potential (and limitations) of prompt-driven development, and what it taught me about AI-assisted software engineering.*

## [Why Cross-Training, Homelabs, and Hands-On Learning Matter for Security](/blog/Opinion/CyberCrossTraining) (March 3, 2025)

*This post explores why hands-on learning, cross-training, and homelabs are essential for OT security professionals navigating an increasingly IT-influenced landscape. It argues that understanding IT security—without blindly copying it—empowers OT teams to adapt proactively, not reactively, to new threats and business demands. Drawing from personal experience, it makes the case that building and testing security models in a safe environment is one of the best ways to build real-world readiness.*

## [Internal Camera Privacy](/blog/Homelab/Automation/InternalCameras/) (February 24, 2025)

*This post outlines a Home Assistant-based solution for managing indoor camera privacy without sacrificing functionality. Instead of powering cameras on and off or physically redirecting them, I used API-triggered privacy masks and overlays to block video feeds when not needed. The setup integrates with Home Assistant dashboards and automations, giving our family visibility and control while avoiding the feeling of constant surveillance.*

## [Network Segmentation](/blog/Homelab/Security/NetworkSegmentation/) (December 20, 2023)

*This post details the network segmentation strategy behind my homelab, modeled after ISA/IEC 62443 principles and refined through real-world risk assessment. Each zone—from trusted devices to automation systems, guest access, and VoIP—is carefully designed to balance security with usability. I share how segmenting by risk and function allows tighter control over sensitive devices without disrupting daily family life, offering practical takeaways for anyone managing a mixed-use network.*

## [Configuring Intel AMT](/blog/Homelab/Hardware/ConfiguringIntelAMT/) (December 13, 2023)

*This post walks through configuring Intel AMT on a Proxmox host to enable full remote management—even when the machine is powered off or the OS has crashed. I cover setup steps on an HP EliteDesk 800 Mini, highlight security considerations, and show how to enable KVM access without external hardware. The result is a streamlined, cost-effective way to manage a homelab from anywhere.*

## [Timing Attacks on the RSA Cryptosystem](/blog/Archive/TimingAttacksOnRSA/) (April 2011)

*Originally written for a college cryptography course, this paper explores how attackers can exploit the timing of RSA operations to extract private keys—without breaking the math. It explains how implementation shortcuts, like optimization logic or algorithm variations, can inadvertently leak secrets through execution time. The post also covers attack vectors, defenses like blinding, and real-world implications for cryptographic systems like OpenSSL.*