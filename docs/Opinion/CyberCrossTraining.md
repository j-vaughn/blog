# Why Cross-Training, Homelabs, and Hands-On Learning Matter for Security

March 4, 2025

It’s easy to get locked into the OT world—focused on uptime, legacy systems, and the constraints that make industrial environments different from IT. And for good reason. IT security strategies don’t always map cleanly to OT, and the risks we manage (safety, reliability, physical consequences) mean we can’t afford to blindly adopt IT’s approach.

But here’s the thing: OT security doesn’t exist in a vacuum. IT security is evolving rapidly, and those changes will eventually impact us—whether it’s through enterprise-driven mandates, emerging threats, or new technologies entering industrial environments.

If we wait to adapt only when we’re forced to, we’ll always be in reactive mode. That’s why cross-training, hands-on learning, and homelabs aren’t just professional development exercises—they’re key to staying ahead.

## **Strengthening OT Security Through IT Awareness**

A common refrain in OT security is “IT doesn’t understand OT.” And that’s true in many cases—IT professionals often don’t deal with real-time constraints, industrial process risks, or the long life cycles of OT assets.

But the other side of that statement is just as important: How well do we understand IT?

The IT security world has largely solved problems that OT still struggles with—like identity management, multi-factor authentication (MFA), and endpoint protection. No, we can’t take IT’s solutions and apply them to OT as-is, but if we understand why they work in IT, we can adapt those principles in a way that makes sense for our environments.

The more fluent we are in IT security, the better positioned we are to:

- Collaborate effectively with enterprise security teams instead of fighting over security models that don’t fit OT
- Push back on IT-driven mandates in an informed way, rather than simply saying, “That won’t work in OT"
- Recognize opportunities to apply IT security principles to OT in ways that improve security without disrupting operations

Security needs to be a shared effort—when we make an effort to understand IT, it becomes a lot easier to get to a productive solution.

## Anticipating Business Needs Before They Arrive

For years, OT has been built around manual processes, scheduled audits, and static reporting. But business leaders increasingly expect real-time operational data, continuous monitoring, and integrated performance dashboards.

If we’re only thinking about the OT world when those demands reach us, we’re already behind. A better approach is to anticipate these shifts and start working on OT-friendly solutions now.

That could mean:

- Exploring architectures that allow safe, read-only operational data flows from OT to IT
- Identifying security challenges early so we’re not scrambling to retrofit protections later
- Understanding what’s feasible before leadership asks for it, so we can guide the conversation rather than react to it

This isn’t about forcing IT-driven models onto OT—it’s about making sure we’re prepared for the security challenges that will come with increased connectivity and data access expectations.

## Thinking Ahead Instead of Reacting

One of the worst positions to be in is trying to solve a security problem at the exact moment it becomes urgent.

Let’s say the business pushes for a modernization of remote access to OT environments. If we’ve already explored different security models and tools—like just-in-time access controls, strong multi-factor authentication, and segmented access paths—we can bring well-informed alternatives to the table. If we haven’t? We’re stuck reacting to whatever gets pushed down from above.

This is why hands-on experimentation matters. Having a safe environment to test architectures, break things, and work through security controls before they’re needed gives us a serious advantage.

Should we immediately move a large pipeline SCADA system to the cloud? Of course not. But if we’ve already thought through secure architectures for remote monitoring, cloud-adjacent data analytics, or layered access models, we’ll be in a much better position to respond when leadership starts asking about those options.

## Learning from IT Without Blindly Copying It

IT security has developed mature, well-tested security models that OT can learn from—if we adapt them properly. Some key examples:

- Just-in-time privilege elevation → Reducing always-on admin access in OT
- Multi-factor authentication (MFA) → Strengthening remote access without disrupting operations
- Advanced endpoint protections → Expanding visibility on HMIs and engineering workstations
- Strong account lifecycle processes → Reducing stale accounts and improving identity hygiene

We can’t simply copy-paste IT security models into OT, but instead of rejecting them outright, we should ask:

- What’s the core security principle behind this?
- How does it conflict with OT constraints?
- How could we modify it to work in an OT environment?

By learning from IT without blindly adopting it, we can make OT security stronger while respecting operational realities.

## Going Beyond Concepts to Build Depth

This isn’t just a theoretical exercise for me—I actively test these ideas in my own homelab. At home, I run an environment that provides IT functions for my “business users” (my family) and OT functions through my home automation system, which I treat like a process control network.

I’ve applied security principles from both IT and OT, and in the process, I’ve found ways to secure my home automation system while maintaining an easy-to-use experience for my family—on top of typical IT services.

Did I make some exceptions from what’s typically allowed in OT, like control from "business" devices? Yes.

Did I learn how to secure this kind of access, mitigate risks, and start to prepare for the possibility that this could become a norm in business at some point in the future? Also yes.

Why does this matter?

Designing security architectures on paper is one thing—actually implementing them, troubleshooting them, and dealing with the nuance of real-world configurations is something else entirely.

In my homelab, I:

- Use network segmentation to isolate my automation system like an industrial control network
- Apply access control layers so management interfaces are protected behind a jump host and MFA
- Test security models hands-on to understand how they work beyond just the conceptual level

The value of this approach? I don’t just read about security—I build, break, and fix things in a controlled environment. That experience gives me a deeper understanding of what works, what doesn’t, and where challenges emerge in implementation.

For OT professionals, homelabs aren’t just an IT thing—they’re one of the best ways to gain real, practical security experience before applying it in production environments.

## The Value of Cross-Training

My career has spanned both IT and OT security, and that cross-training has fundamentally shaped how I approach security. I started in SCADA network engineering, where I learned firsthand the constraints of ICS networks, process control, and industrial operations. Later, I moved into enterprise identity and access management (IAM), working on authentication, access governance, and scalable security solutions. Now, I apply both perspectives to securing OT environments, leading identity security efforts in critical infrastructure.

That experience has made one thing clear: OT security professionals benefit from having some IT experience. IT-driven security mandates will continue to impact OT, and understanding the IT side of the house makes it easier to push back productively—not just saying something won’t work, but explaining why and offering alternatives that do. It also makes collaboration smoother, ensuring OT security needs aren’t overlooked when IT-driven initiatives reach industrial environments.

At the same time, IT security doesn’t always have the right answers for OT, and the strongest OT security professionals are the ones who can critically evaluate security models from both sides. Learning IT security doesn’t mean abandoning OT principles—it means having a broader perspective to help OT security evolve on our own terms.

## Conclusion

OT security is evolving, whether we like it or not. IT-driven trends, business demands, and emerging threats will continue shaping how security is approached in industrial environments.

If we wait for those shifts to force changes on us, we’ll always be reacting instead of leading.

Hands-on learning, cross-training, and homelabs aren’t optional—they’re critical for staying ahead. The more we engage with security concepts outside OT, experiment with architectures in controlled environments, and proactively think through how new technologies could (or couldn’t) apply, the more effective we’ll be at shaping practical, OT-friendly security strategies that actually work.