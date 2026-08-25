# Groupies

**A group decision tool that never holds a vote.**

Live: https://groupies.vercel.app

Majority vote picks the option most people mildly like, which is usually somebody's
worst night. Groupies does the opposite. Options get **ruled out** by a named person's
stated limit, survivors rank by **who suffers most**, and it is not finished until
**every single person signs**.

## The mechanism

1. **Nobody votes options down.** Each person marks every option `great` / `fine` /
   `can't`. A `can't` is a hard limit and requires a stated reason, which the whole
   group sees. An option dies because it broke a limit somebody actually named, not
   because it lost a popularity contest. That is checkable and impersonal, so nobody
   has to argue anyone down.

2. **Survivors rank by the worst-off person.** `great` costs 0, `fine` costs 1. An
   option's score is its unhappiest person, not its average. The winner is the option
   whose worst-off person is least badly off (minimax regret). Groups accept that as
   fair because it protects whoever drew the short straw.

3. **Deadlock resolves with one question to one person.** If everything is blocked, it
   finds the option blocked by exactly **one** person and asks only them, showing what
   it would reopen. Nobody else is asked to move, and nobody is asked twice. "No" is a
   legitimate answer that ends the round honestly rather than a loss condition.

4. **It is not decided until everyone taps in.** Refusing to sign is not a dead end:
   say what is wrong, it becomes a new limit, and the whole thing re-runs. Unanimity,
   not four out of five.

## Using it

One device, passed around. Each person answers privately and the screen clears before
it reaches the next pair of hands. No accounts, no server, no data leaves the browser.

## Izzy

The companion in the corner is [Izzy](https://auny.media), an existing character whose
canon locks her face permanently behind flowers. Her three canonical stages map onto
the decision: **lost** while limits are still being collected or when no path remains,
**anchor** once a path exists, **empowered** only at true unanimity.

She is an ambient witness, never an arbiter. She reacts to the state of the process and
never to a person, stays calm when somebody holds a boundary, and never celebrates an
elimination. Nothing critical is encoded only in her pose, and she can be hidden.
That framing came out of an adversarial design consult with Codex, kept in
[`docs/codex-izzy-consult.md`](docs/codex-izzy-consult.md) along with
[the brief](docs/izzy-pet-brief.md) it answered.

## Build

One file, no dependencies, no build step. The 3D scene is a hand-rolled perspective
projection on a 2D canvas (about 120 lines: rotate, project, depth-sort, draw) rather
than a 3D library, so the whole app stays a single self-contained HTML file.

Interface design follows the three.js example chrome: viewport first, chrome as raw
overlay, monospace, hard edges, no cards, grid floor.

`demo.html` is a scripted walkthrough of the mechanism on fixed data, for anyone who
wants to see the whole arc without assembling a group.
