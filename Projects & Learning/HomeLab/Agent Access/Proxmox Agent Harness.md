
So I want to give you some more ideas on from my vision of what this will look like. So the goal isn't
  to like just be able to do things like configuring my home lab and all the other things the Proxmox API
  lets one do. The goal, because that goal can just be dubbed like Codex. You know, I have Codex
  installed in each node and it kind of does that for me anyways. Like Codex can do a bunch of my
  configurations, do whatever this harness can probably do. Codex and Claude by themselves can do that by
  just installing it on there. The goal is to be able to do the same things, but with way less token
  usage, because there is a script of exactly what needs to be done. All the information of the home lab
  is like organized and easy to access for any agent that might need to. So it doesn't have to do
  discovery. It doesn't have to do all these things. And like those documents are like about the
  configuration and status of the home lab as a whole, like what VMs are running, nodes, different things
  that you may need when you're like doing configurations, like one is how's the storage, whatever it
  may be, how's the storage set up, lives in a place that is the source of truth. So, and it's like
  deterministic for that information to be going into the place where the status goes. So the agent
  doesn't have to do discovery and all that. The logs of the home lab of the different nodes are easily
  accessible, so it doesn't have to go running commands to do logs and stuff. And the GUI of the
  interface as its own thing is optimized for Proxmox usage. So there's like buttons for like switching,
  like a side menu for like which node I want to look at, or looking basically all the same things that
  the Proxmox GUI in the web does. This would kind of replace it, but with the addition of AI wiring. So
  like there's like MCPs, there's like documentation for Proxmox that's easily accessible to any agent.
  There's like system prompts that like tell it how to act and like how to do certain things. There's
  like scripts in there that are for running certain things in Proxmox. So the agent doesn't have to
  figure these things out every single time that things need to be done. You know, everything is
  observable. If something goes wrong in the home lab, it can be tracked down and figured out what went
  wrong, whether there's something wrong in like a script or like the agent was wrong. It's extendable.
  So like if let's say I wanted to add a widget there on my one of my screens, the agent doesn't have to like create the HTML and the CSS all for that widget all over again every time I want a new widget. It
  just takes the existing template and wires up the back end of it however it needs to be to achieve my
  goal. If I want like a status thing to show somewhere in the corner, it doesn't have to like figure out
  what things it needs to call, where it's going to get the information. There's already a source for
  where it would exactly need to go to get certain information. It knows what already exists, so it can
  reuse existing things. It builds widgets and scripts and extensions to the harness in a way that that's
  reusable, and like if there's something on the next widget that can just be reused from the one
  before, it can do that because it builds things in a way that's reusable and doesn't produce like slop
  and just bloat in the system. I want this harness to replace Proxmox web UI for me. And kind of be like
  a AI slash custom UI layer on top of the Proxmox API, and maybe I need to create like an MCP for
  stuff. But the harness itself should be like built for Proxmox and like Cloudflare use and any other
  things that are in this like home lab ecosystem and like common technologies and practices should be
  built around that as its main focus.