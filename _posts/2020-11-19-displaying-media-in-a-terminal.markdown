---
layout: post
title:  "Displaying Media in a Terminal"
date:   2020-11-19 21:31:31 -0500
categories: [Python, Terminal] 
---

This blog post came from the old jmkdev blog. [View the original post here.](https://blog.jmksite.dev/2020/11/displaying-media-in-terminal.html)
I haven't been able to transfer over the videos from the old post yet, so you'll have to go there to see them. Sorry about that!

**Note: If you just want to see a video being played in a command prompt, scroll down to the videos!**  
A little while ago I was messing around with Python and Pillow and wrote a little program to dump an image to a command prompt. It used the 4 shade characters and the space key plus the 8x8 raster font.

![](https://lh3.googleusercontent.com/-6hkRl4tYPEA/X7aNeKEg5aI/AAAAAAAAI_M/xBG8srENdjEG24NbkPZK6Q0Bata-pVJsgCLcBGAsYHQ/w299-h320/image.png)  

This worked quite well, and I was pretty proud of how it turned out, but it needed some color to really make it shine. 

![](https://lh3.googleusercontent.com/-oRmgO_80SYI/X7aN7XP2RKI/AAAAAAAAI_Y/wWZy_Q_A9poAR_3vr2c1-9ELgMj-e2T3QCLcBGAsYHQ/w311-h320/image.png)

The first attempt did not come out very well. This happened because the 256-color adaptive palette used by Pillow does not match up with the xterm color palette.

![](https://lh3.googleusercontent.com/-oRmgO_80SYI/X7aN7XP2RKI/AAAAAAAAI_Y/wWZy_Q_A9poAR_3vr2c1-9ELgMj-e2T3QCLcBGAsYHQ/w311-h320/image.png)

After trying again with the "web" palette, it looked better, but something was definitely wrong. This is supposed to be white.  

For the meantime, I stopped working on the colors and worked on black and white.
I manually went through the xterm 256-color palette to pick out the grey shades and put them in a Python list, then used that list as the image palette. 

![](https://lh3.googleusercontent.com/-F_VL2-iXn1w/X7aOYfVt8VI/AAAAAAAAI_o/3PkNMeninoMBlSsJ3hHQ8VNviJurkgrmwCLcBGAsYHQ/w311-h320/image.png)

At this point, it looks a lot smoother and more aliased. I thought I would manually have to create a converter for the rest of the colors, but instead I began to use the python library "blessed" to convert between full color to the limited 256-color palette used by terminals. Here's the result of that:

![](https://1.bp.blogspot.com/-RI5IILyf26Q/X7aQvcQpeHI/AAAAAAAAJAQ/Dlbd6Nx-Pt8LZBayJv6dO9WQvRsNu99mwCLcBGAsYHQ/w640-h637/pyimgterm.png)

I was pretty proud of this. It could display any image I could put into Pillow, which is very neat. But I wanted to go one step further and display __full video__.

If you think this through, it seems fairly easy. All you have to do is split up the video into individual frames, display each frame the same way we displayed our images, and then wait 1/fps seconds.  

The issue now is that the drawing routines (the functions that take a frame and draw them onto the screen) take time to run, and we must time how long they run and subtract that from the delay for a smooth output. Another issue is that different terminal interfaces vary in speed, and we may not be able to track that via a timer, which means we'll need to subtract a bit of time depending on the terminal. (I especially noticed this on ConEmu, which displayed the frames so slow that my program was calculating negative wait times)

The first attempt to display the video showed all the frames, but it displayed them too slowly, which resulted in lag and an incorrect FPS. 

VIDEO 1 HERE

After that, I shrunk the video down to a more reasonable size (keep in mind that the pixels are eight times as wide as they should be!) and things were working a bit better. You could already make out movement, but the video kept scrolling while it was playing.

VIDEO 2 HERE

After making a few small tweaks, things were working a bit better and the flicker was faster due to speed improvements. This didn't mitigate the flicker by any means, just improved the general quality.

VIDEO 3 HERE 

After that, I was able to improve the video artifacts significantly.

VIDEO 4 HERE

And finally, I reduced the flicker and artifacts to a simple vertical wiggle. Still annoying to watch, but much better than before.

VIDEO 5 HERE

And at last, the flicker and artifacts were completely gone. FPS was working properly, and if the lag got too slow the system would skip all wait time.

VIDEO 6 HERE

As an added bonus, this entire module is object oriented, so the code to display this video is as simple as this:

```py
import player
import display
video = player.TerminalVideo(r"PATH\TO\VIDEO", display)  # Opens the video.
video.play()  # Plays the video.
```

This will open a video file and play it in the console. Simple.
Of course, we might want to add a bit more code to make the program a bit nicer:

```py
import player
import display

video = player.TerminalVideo(r"PATH\TO\VIDEO", display)  # Opens the video.

video.fit_frame()  # Resizes the terminal window to the video resolution.
try:
    video.play()  # Plays the video.
except KeyboardInterrupt:
    display.clear()  # Clears terminal display
    display.home()  # Moves cursor home
    print(u"\u001b[0m", end="")  # Resets the colors.
    pass
```

And we're all set now!
This will open a video file and resize the terminal to the size of the video (plus 1 vertical, due to a bug) and also catches KeyboardInterrupt (Control+C) and binds it to clearing the display, resetting the cursor position, and resetting the colors.

Thanks for reading this post, and I will make another for future updates! Although each "pixel" is 8 times as big as normal pixels, I think I have found a way to at least double the horizontal resolution. Stay tuned!

