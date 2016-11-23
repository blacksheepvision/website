---
layout: post
title: Reversing an encrypted cordova app
date: 2016-11-23 12:00:00
categories: posts
comments: true
en: true
description: Reversing an encrypted cordova app
---

Recently I was asked to extract a web service functionality out of an Android application. A fairly simple task, I ran the application in emulator put the proxy between the app and the internet,
started the app ... but it won't load. Of course I tought ... ssl pinning, will easily bypass using Xposed Framework or Android-SSL-TrustKiller. I played with both, both FAILED.
Then things started to get ugly, I unpacked the apk using apktool, and in assets folder something caught my attention ... a www folder. Wtf is that? Looked trough the java classes most of them
contained the word cordova.
At the time I didn't have any fucking idea what cordova means. Looks like [CORDOVA] is a framework for building cross platform applications. All the action is happening inside a webview.
I tought shit, this is simpler then I first tought. Started looking at the www folder but all could I see were some base64 encoded files. I tried to decode the base64 guess what? 
The shit was encrypted. Googled arround to see if an available decryptor arround, looks like default cordova apps are deployed unencrypted and I was dealing with a plugin. 

## Decrypting the source

Managed to locate the code responsable for decrypting the resources easily, and writen a java tool to decrypt files. Writed a bash script to find and pass to the decryptor all html and js files and voila 
was reading full source code including comments :). That was nice but I didn't give a fuck about the source I just wanted to see the requests that were beeing sent to the server.

## Disabling SSL pinning 

So I located in the code things about SSL pinning commented them out, did another java app to reencrypt the modified source. Writed a bash script to repackage resign deploy to my device as I felt I will have multiple trials and errors.
After 3-4 attempts I gived up it was already 4 in the morning and I started reversing arround 10 PM my patience was gone. So I modified the app to send the request I was interested to my netcat server. Extracted the data and was very happy
until the morning...

## A 5 minute approach vs the road I have taken

In the morning I was still angry that I didn't manage to bypass ssl pinning on this crap, even tried to disable the plugin the app was using to bypass ssl pinning, shure I did some wrong steps in the process but again something was telling me is an easier way to do this.
Playing with the actual app little out of boredom on my king throne, made my realise that this app is actualy a web view and if it is a webview is debuggable using Chrome Dev Tools. So i just needed to enable Debuggable Flag in Android Manifest. Did that repackaged the app,
and there it was all requests available in my chrome browser, no proxy just beautiful raw requests.

You can find all code I writen on this assigment on this [repo].

[CORDOVA]: https://cordova.apache.org/
[repo]: https://github.com/blacksheepvision/reversing-cordova-app
