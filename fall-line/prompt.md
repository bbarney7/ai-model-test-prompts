Build "Fall Line" - a single self-contained HTML file (three.js and its addons from a CDN are the only dependency): an open-world snowboarding game on a whole mountain. No image, model, texture or audio files and no generated images: everything is built in code.

The mountain

- A big mountain you can ride anywhere. There's no set course and no invisible walls out in the snow: pick a line, see something worth hitting, and go
- Jumps, rails and other things to ride wherever they make sense, plus places worth discovering for people who explore
- What else is on the mountain, how you get back up it, what there is to do and how it all looks are up to you. Make it a place people want to keep exploring and keep finding new things in

The riding (this is the whole point - it has to feel like snowboarding: the edge biting in a carve, the pop off a lip, floating through the air and landing it clean)

- Real speed and real gravity: carving, skidding, popping, spinning, flipping, grabbing, grinding, landing clean, and bailing when you get it wrong
- Riding should be easy to pick up and hard to master

Running

- Opens straight into riding within one click, and teaches its own controls in the game
- Works with a keyboard and on a phone
- Smooth 60fps on a laptop, with no errors in the console

For testing

- `?seed=` makes the mountain repeatable: the same seed gives the same mountain
- Expose a read-only `window.fallLine` with `snapshot()`, taken from the live objects that drive the game: game time, recent frame times, and the rider's position, velocity, heading, the board's yaw, pitch and roll, state (riding, in the air, grinding, bailed, or whatever states your game has), speed and current trick. Also `heightAt(x, z)`, returning the snow surface height there
- Other programs on this machine also run on node and python. Stop any server you start by its process ID or its port (for example `kill <pid>`, or `kill $(lsof -ti tcp:PORT -sTCP:LISTEN)`). Never stop processes by name: no pkill, killall or pkill -f

Make it the snowboarding game you'd want to play all winter.
