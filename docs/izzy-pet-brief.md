## Task bundle
**Purpose.** Design consultation for a one-night hackathon build: a group-consensus web app
whose mascot must read as a living screen "pet" while obeying a locked character canon that
forbids visible eyes. I need adversarial, concrete design guidance I can implement tonight,
including a challenge to the premise if the premise is weak.

**Denied actions.** Do NOT create, modify, delete, move or rename any file. Do NOT run git
commands, install packages, start servers, or make network requests. Do NOT write code to
disk. Inline code sketches inside your report are fine. Absence from this list is not
permission: this is a read-and-report task only.

**Report contract.** Hand back prose to stdout answering the five numbered questions in
order, plus the "tension" section and the premise challenge. For each rendering option in
Q5 give a clear pick with the reasoning. State explicitly at the end: (a) that you modified
no files, and (b) anything you were asked about but could not answer, and why.

---

# Brief: design Izzy as a little pet companion

## What is being built
"Nightbloom" is a single-page web app that helps a group reach a UNANIMOUS decision.
Mechanism: people privately state their real limits, an LLM extracts hard limits vs soft
preferences, options are ruled OUT by a named person's stated limit (never voted down),
survivors rank by minimax regret, and if everything dies the app finds the single smallest
flex and asks ONE person a yes/no. It is not finished until every person signs.

One-night hackathon build. Runs in the browser. A self-contained single HTML file is a hard
constraint for the fallback demo; a live version may call a model server-side.

## The ask
The app has a mascot: Izzy. The owner wants her to feel like "a little codex pet": a small
living creature that sits in the corner of the app, has its own idle life, and REACTS to
what the decision engine is doing. Not a static illustration. Not a chat avatar. A pet.

Answer these, concretely:
1. What makes a screen-corner "pet" feel alive rather than decorative? Name the specific
   behavioural mechanics (idle loops, attention, anticipation, latency, imperfection,
   reaction-to-user vs reaction-to-system). Be specific enough to implement.
2. What is the minimum state machine a pet like this needs, and what should drive
   transitions: app events, time, user cursor, or all three?
3. Where do screen pets usually fail and become annoying or cheap? What are the hard rules
   that prevent that?
4. This pet also has to carry MEANING: her emotional state is a readout of how close the
   group is to consensus. How do you make a pet legible as a status indicator without it
   becoming a progress bar with a face?
5. Rendering: hand-authored animated SVG, vs a small WebGL/Three.js 3D character, vs sprite
   frames. Given a one-night build and a self-contained-file constraint, which, and why?
   What is the cheapest path to a genuinely 3D-feeling character?

## Hard character canon that CANNOT be broken
Izzy is an established original character with a locked visual law:
- Her eyes and upper face are ALWAYS obscured by flowers growing up over her face.
  This is absolute. We never see her full face. Only the lower face may show.
- Deep garnet and bruised-violet roses, with exactly ONE saturated red rose as the single
  point of colour in the frame.
- Warm medium brown skin. Long dark brown-black hair past the chest. Thick full dark brows.
  Gold stud on the LEFT nostril. Beauty mark lower-left of the mouth. Full lips.
- Modest, fully covered wardrobe: high-neck, long-sleeve black lace gown. Nothing revealing.
- Motifs: a pale crescent moon behind her head like a halo, a single black moth, bare thorny
  black branches, low ground fog.
- Register: gothic emo storybook. Empowered but delicate. Melancholy that is owned, never
  victimhood. Low-saturation dark pastels, deep blacks.
- Her canonical arc has three stages we are mapping onto the decision flow:
  LOST (turned away, head bowed, deepest shadow, blooms densest and closed) then
  ANCHOR (steadying, beginning to face forward, blooms opening, tones warming) then
  EMPOWERED (upright, chin lifted but face STILL veiled, light breaking gold).

## The tension I want you to attack
A pet is cute, readable, expressive, and usually communicates with its EYES.
Izzy has no visible eyes, ever, and her register is melancholy gothic, not cute.
"Cute little pet" and "face permanently hidden behind flowers" are in direct conflict.

Tell me how to resolve that without breaking the canon. What carries expression when there
are no eyes? Give me a concrete inventory of expressive channels available to this specific
character, ranked by how much emotion each can carry.

Also challenge the premise if it deserves it: is a pet the right device for an app about
resolving conflict fairly, or does a mascot undercut the seriousness of the mechanism?
