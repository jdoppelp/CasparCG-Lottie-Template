# CasparCG-Lottie-Template
I wanted to create a simple way to use CasparCG for Realtime Grafics like lower-thirds, titles, tables, charts, bars, etc. Since I have low exprerience in HTML/CSS I tried to use LottieFile animations, exported with AfterEffects. The skript in this template updates/replaces the data in the LottieFile (e.g. name and subtitle), before CasparCG plays the template.

This solution works for me and my use cases, let me know if you have any other ideas to improve the code or add further functions to it.


## How to use
To play these expamle templates with CasparCG you need to:
1. Copy all files of this repository into your CasparCG template Folder. 
2. In the Caspar Client - set the checkbox "Send Data as JSON", small, but important!
3.1 For "example_lower-third-template.html": 
Add the keys: 
```
"_firstLine", "_secondLine"
```
with your new values. You can now use the "play", "stop" commands from CasparCG.
3.2 For "example_PieChart-template.html": 
Add the keys: 
```
"_headline", "_subheadline", "_value1", "_value2", "_value3" 
```
with your new values. Use "play" command for playing the beginning (or "load" to stop on first frame) and use "next" to trigger the next part of the Piechart animation.

![LottieTemplate_Example_Image](https://user-images.githubusercontent.com/87117653/231723213-12637e81-30ae-498e-8298-a8c1994b5034.png)

## How it works
First of all: I used the same script for both templates. So its universal for different usecases. As you play the template, the js-skript in the template replaces the keys in the animation with your values and plays the lower-third. It simply changes the text within your LottieFile code and plays a part of the animation. 

# Getting Started with your own template:

## Creating the LottieFile 
To use the templates with your own animation you need to create a LottieFile where the text isn't converted to shapes (in Bodymovin - Disable Glyphs in the Settings) and the textlayers in the animation should have unique names - e.g.:
```
_firstLine, _headLine, _value1, ...
```

I recommend using this type of naming convention with the underscore " _ " at the beginning.
Remember that the script only updates text layers. If you want to change data for an animation you have to make sure that the data is stored in a text layer, not in a slider. If you don't wanna see the textlayer, just make it invisible.


Add these markers to your animation timeline. They will splitt the animation into parts, so you can play the parts step by step in CasparCG. Every marker needs to have a duration. After playing the part, Caspar will stop on the last frame of the marker.
This is how you name them. The "start" marker is 100% necessary: 
```
start   //part thats should play on "play" Command
```
the other markers are optional, use them as needed for your animation: 

```
stop   //part that shall play on "stop" Command
next1 , next2, [...]   //part that shall play on "next" Command.
```

 The first time you trigger the "next" command in CasparCG, the template will play the "next1" marker. The secound time - "next2". ... 


Now you can use the Bodymovin plugin to export your animation as a lottie/JSON file like this: 
1. Make sure you disable Glyphs in the settings
2. Add the Font Path and the Font Family - The Fontpath is relative to your HTML-Template. So that the Template knows where to find the font to display your text properly. Therefore I created the "fonts" folder next to the template.


![LottieTemplate_Bodymovin_Font_Image](https://user-images.githubusercontent.com/87117653/231740645-99fe55e6-1f3c-4a7b-b9e2-a7d7051c7ddf.png)



## Add your animation to the template
Open the "raw-template.html" file with your code editor and paste the LottieFile JSON code from your exported file to the variable "lottieTemplate" in Line 39

```javascript
let lottieTemplate =  /*paste your LottieFile code here */
```

This might be way bigger than my example, depending on your animation.



## Try your templates
Now you should be able to playout your own template with CasparCG by adding the keys and values in the client and sending it to CasparCG.

## Debugging
As you play around with different templates in development, you may forget the excact keys you need for your data. Therefore I created a "secret" info key. 
By sending the key 
```
"_templateInfo"
```
(the value doesn't matter) the CG Server shows a list of every layer starting with an underscore " _ " .
Thats how you can check the right keys for your textlayers easily if you're using the naming convention with the underscore. 

![LottieTemplate__templateInfo_Image](https://user-images.githubusercontent.com/87117653/231729716-b7107805-1918-43bd-8059-419c981ad5e8.png)


Further you get a notification on your CasparCG Output if you forget to send data as JSON.

![LottieTemplate_JSON_Image](https://user-images.githubusercontent.com/87117653/231729132-526047f9-7e4c-49dc-bbce-6a8c40a8b6be.png)




## About CasparCG
I always tried this with CasparCG LTS 2-3-3 


## Credits
Thanks to  [HeineFro](https://github.com/HeineFro) for solving the Font problems.
Thanks to [PeterNicos](https://github.com/PeterNicos) for creating the example templates and playing around with expressions in AE. 
More templates can be found on his github page.
