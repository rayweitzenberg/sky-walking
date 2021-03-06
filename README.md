# Sky Walking

![Twilight Pink Screenshot](twilight.png)

### Personal: https://neoneon.one/sky-walking

### Glitch: https://sky-walking.glitch.me/

### GitHub: https://github.com/rayweitzenberg/sky-walking

## The Hell is This?

Goofy, yes. Messing around in a time of crisis.

Watching governor's livestream. Cuomo's brother is infected. Found out earlier this morning. Personal side of the governor. This shit's intense.

"Sweet guy. But now he's quarantined in the basement."

### So, yeah ...

A sketch I did while not sleeping ... initially because I was stressed out about the armageddon we're currently inhabiting, but also because I wanted to get back to work. So I did.

My first step into the A-Frame universe. For those who don't know:

https://github.com/aframevr/aframe

WebXR it is. It's a full on VR space running on your desktop, or phone, or headset. It doesn't really care.

And I'm not coding this in C#.

### What I was trying to do ...

... was to get randomly placed elements arranged programmatically in space.

Started out just playing with the aframe particle-system, then moved to objects based off some design i came across while working.

It wasn't at all interesting, so i had to add some animation. And when those animations were identical across all elements, I had to add still more randomness to the mix. And Voila! Agitated pink things twitching over an oil slick with ping pong electrons flitting about. Whatever.

Fun, though.

Please don't take this too seriously. There's already enough serious shit out there right now. Wait with me for Godot in Sarajevo.

## Working Notes

### Audio Reactivity

#### Thursday, April 9, 2020 at 12:47:38 PM

Have audio reactivity working, but it's really crude.

Playing the audio currently happens via a click on the page. This is great on desktop, but doesn't work in the Quest. The element that triggers the audio isn't shown in VR. Looking for a way of placing the trigger somewhere in VR where I can get to it.

Also looking for a way of playing the audio automatically, as for some reason it currently plays twice on load.

ATM taking quite a bit of horsepower to loop through the entire array of elements and adjusting them. It's handled using the afame tick() function to update the cubes' scales. Because of the massive resource hit, I've customized the update's frequency down from 90 frames/sec to something more manageable like every 50ms. Will need to refactor the code or find a new and better solution all together.

### Customizing look-controls

#### Friday, April 3, 2020 at 11:09:38 PM

https://aframe.io/docs/1.0.0/components/look-controls.html#customizing-look-controls

While A-Frame’s look-controls component is primarily meant for VR with sensible defaults to work across platforms, many developers want to use A-Frame for non-VR use cases (e.g., desktop, touchscreen). We might want to modify the mouse and touch behaviors.

The best way to configure the behavior is to copy and customize the current look-controls component code. This allows us to configure the controls how we want (e.g., limit the pitch on touch, reverse one axis). If we were to include every possible configuration into the core component, we would be left maintaining a wide array of flags.

The component lives within a Browserify/Webpack context so you’ll need to replace the require statements with A-Frame globals (e.g., AFRAME.registerComponent, window.THREE), and get rid of the module.exports.
