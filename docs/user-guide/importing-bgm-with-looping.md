This guide will show you the basic steps for looping and importing your own music into Final Fantasy XIII games using the Nova Chrysalia tool.

## Step 1 encoding your audio file
- First, the audio you are going to import needs to be in the .OGG format with stream encoded using NCVE. If you try to work with .mp3 file or even .OGG file not encoded as described, you will get an error and Nova Chrysalia will abort the process. To get an audio file in the required format, you simply need to run the VorbisEncode.exe that you can find in the same folder as NovaChrysalia.exe.

- After running the program, browse for your audio track (to make things easier you could put all the audio files you want to use into one dedicated folder). Then click "Encode Selected File to VORBIS" and a .OGG file of the same name will be generated next to your selected audio file.

## Step 2 converting the audio file
- Run Nova Chrysalia and navigate to the Mod Tools tab. In the third column called: File Format Conversion you can see two buttons - "Convert SCD File" and "Convert Audio File". The former is used when you need to convert audio that is already in the game into .OGG. The latter is the one we need. Click it and a new windows will appear. Here you can edit your audio. You can set the preferred volume and make the audio loop if necessary.
(Note that the highest volume you can set the audio to is 1.0. Anything higher will have no effect. The lowest is 0.1)

If you don't need to loop the audio, simply click "confirm", a .SCD file will be generated next to the file you selected, and skip to step 4.

## Step 3 looping your audio

For this part you will need a good audio editing software. I recommend using Audacity.
- Open your .OGG file in the software of your choice then set the timing (the second) you want your loop point to be at, in the track display. Now, music in Final Fantasy XIII series is a bit tricky, so seconds themselves won't be enough to determine your loop points.

- You need to find a way to see the samples. Audacity shows a big seconds counter at the bottom of the window, which can be switched to show samples by clicking the dropbox next to it and selecting "samples". It will show you the number which you need to copy and paste into Nova Chrysalia, into the box Loop Start (Sample), or Loop End (Sample), without any commas. If you did everything correctly, then as soon as the song gets to the Loop End you set, it will cut to the Loop Start you set.

- Nova Chrysalia will place your loop points as best as it can, but if you are not happy with the result, you can offset the calculated loop before converting the file.

- If you don't want the audio to loop, then you can leave the loop points at 0.

- When you have everything set as you want, click "Confirm" and Nova Chrysalia will generate an .SCD file for you, next to your .OGG file.

### The math behind it (info. for programmers):
For anyone would be interested in how to calculate the audio track samples from scratch:
- Multiply the number of seconds by the number of the track's sample rate in Hz.

- e.g. Let's say my file has a sample rate of 44100 Hz and I want the loop point to be at 1 minute and 20 seconds. That is, at 80th second. So I need to multiply 80 x 44100. I will get 3528000 and this is the number I need to put into Nova Chrysalia, into the Loop Start (Sample) box, or Loop End (Sample) box.

## Step 4 putting your audio in game, replacing the game's files
- Now there are more ways to do this, but the easiest and safest is to use Nova Chrysalia of course. Under the "Game Launcher" tab, see the 4th column. There on the bottom you can see two buttons: "Unpack Game Data (EN Audio)" and "Unpack Game Data (JP Audio)". Select one, depending on which audio version you want to import your music to, and wait till the process is done. It can take some time.

- Once the process is finished navigate to "Your Steam Installation Path \Steam\steamapps\common\FINAL FANTASY XIII\white_data\sound\pack\8000". In here you can see all the games background music.

- Here you need to locate the music track you want to replace, give your .SCD file the exact same name and... well, replace it.

- That's it. You can listen to your custom music ingame now.

N.B.To identify which audio you are replacing, you can simply use Nova Chrysalia's mod tools to "Convert SCD File" to .OGG or use foobar with the vgmstream plugin.
