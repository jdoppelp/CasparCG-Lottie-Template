# CasparCG-Lottie-Template
I wanted to create a simple way to use CasparCG as a Realtime-Grafic-Playout for lower-thirds, titles, etc. Since I have low exprerience in HTML/CSS I tried to use LottieFiles animation, exported with AfterEffects. The skript in this template update/replace the data in the LottieFile (e.g. name and subtitle) , befor CasparCG plays the template.

This solution works for me and my use cases, let me know if you have another idea to improve the code or add further functionality to it.


## How to use
To play this expamle templates with CasparCG you need to:
1. Copy the all files of this reposotory into your CasparCG template Folder. 
2. In  the Caspar Client - set the checkbox "Data as JSON", small, but important!
3.1 For "example_lower-third-template.html": Add the keys: "_firstLine" and "_secondLine" with your new values. Now you can use the "play" "stop" commands from CasparCG.
3.2 For "example_PieChart-template.html": Add the keys: "_headline", "_subheadline", "_value1", "_value2", "_value3" with your new values. Use "play" command for playing the beginning (or "load" to stop on first frame) and use "next" to trigger the next part of the Piechart animation.

//Example Images


## How it works
First of all I used the same script for both templates. So its universal for different usecases. As you play the template, the js-skript in the template replaces the keys in the animation with your values and plays the lower-thrid. It simply changes the text within your LottieFile code and plays a part of the animation. 

# Getting Started with your own template:

## Creating the LottieFile 
To use the templates with your own animation you need to create a LottieFile where the text isn't converted to shapes (in Bodymovin - Disable Glyphs in the Settings) and the textslayer in the animation should have an unique names (e.g. _firstLine, _headLine, _value1, ...). 
I recommend to use this type of naming convention with the "_" at the start.
Remember that the script only updates text layers. If you want to change data for an animation you have to make sure that the data is stored in a text layer, not in a slider. If you dont wanna see the textlayer, just make it invisible.

Add your markers to your animation. They will splitt up the animation into parts, so you can play the parts step by step in CasparCG. So every marker need to have a duration. After playing the part, Caspar will stop on the last frame of the marker.
This is how you name them. The "start" marker is 100% nessisary: 
```
start   //part thats should play on "play" Command
```
the other markers are optional as you need them for your animation: 

```
stop   //part thats should play on "stop" Command
next1 , next2, [...]   //part thats should play on "next" Command.

```
 The first time you trigger the "next" command in CasparCG, the template will play the "next1" marker. The secound time - "next2". ... 


Now you can use Bodymovin Plugin to export your animation as a lottie/JSON file lime this: 
1. Make shure you disable Glyphs in the settings
2. Add the Font Path and the Font Family - The Fontpath is relative to your HTML-Template. So that the Template knows where to find the font to display your text properly. Therefore I created the "fonts" folder next to the template.

!!! IMAGE Font export




## Add your Animation to the template
Open the "raw-template.html" file with your code editor and paste the LottieFile JSON code from your exported file to the varible "lottieTemplate" in Line 39

```javascript
let lottieTemplate =  /*paste your LottieFile code here */
```

This might be way bigger than my example, depending on your animation.



## Try your templates
Now you should be able to playout your own template with CasparCG by adding the key and values in the Client and send it to CasparCG.



## About CasparCG
I always tried this with CasparCG LTS 2-3-3 


## Credits
Thanks to @HeineFro https://github.com/HeineFro for solving the Font problems
Thansk to @PeterNicos https://github.com/PeterNicos for creating the example templates and playing around with expressions in AE

