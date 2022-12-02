# CasparCG-Lottie-Template
I wanted to create a simple way to use CasparCG as a Realtime-Grafic-Playout for lower-thirds, titles, etc. Since I have low exprerience in HTML/CSS I tried to use LottieFiles animation, exported with AfterEffects. The skript in this template update/replace the textdata in the LottieFile (e.g. name and subtitle) , befor CasparCG plays the template.

This solution works for me and my use cases, let me know if you have another idea to improve the code or add further functionality to it.


## How to use
To play this expamle template with CasparCG you need to:
1. Copy the "example_lower-third-template.html" and the "lottie.js" (lottie player from Bodymovin-Plugin) into your CasparCG template Folder. 
2. Set the checkbox "Data as JSON", small, but important!
3. Add the keys: "_name" and "_subtitle" with your new values. Now you can use the "play" "stop" and "update" commands from CasparCG.


![image](https://user-images.githubusercontent.com/87117653/205102045-e0954b19-9e22-42ae-9f35-8b5b6624d511.png)


## How it works
As you play the template, the js-skript in the template replaces the keys in the animation with your values and plays the lower-thrid. It simply changes the text within your LottieFile code and plays a part of the animation.




# Getting Started with your own template:

## Creating the LottieFile 
To use the templates with your own animation you need to create a LottieFile where the text isn't converted to shapes (in Bodymovin - Disable Glyphs in the Settings) and the textslayer in the animation should have an unique value (e.g. _name, _title, _subtitle, _function, ...). 
It's about the value of the layer NOT the name of the layer!
You can have as many texts as you like in your animation. 

Add 3 markers to your animation. They all need to have a length.
Name the markers: 
```

{"name":"start"}    //part thats should play on "play" Command
{"name":"still"}    //part thats should play on "update" Command
{"name":"stop"}     //part thats should play on "stop" Command

```

Now you can export the LottieFiles and copy the whole JSON Code.


## Add your Animation to the template
Open the html file with your code editor and paste and replace the LottieFile JSON code to the varible "lottieTemplate" in Line 24

```javascript
let lottieTemplate =  /*paste your LottieFile code here */
```

This might be way bigger than my example, depending on your animation.



## Try your templates
Now you should be able to playout your own template with CasparCG by adding the key and values in the Client and send it to CasparCG.



## About CasparCG
I always tried this with CasparCG LTS 2-3-3 


