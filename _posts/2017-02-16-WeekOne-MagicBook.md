---
title: "Week One: Magic book"
categories: MIX
---
# First week: Magic book!

For our first assignment we had to create an augmented reality reading experience using mobile AR. With this simple assignment, we decided to start with the software that we were both previously experienced with. Unity and Vuforia. Unity being the game engine that I have quite a lot of experience with and Vufoira being the gluing piece providing AR functionality to our expirience.
Let me start by saying that even though I am fairly experienced with Vuforia, using it both at work and in previous projects, I am not entirely a fan. Now don’t get me wrong. Vuforia is great. Performance is better than other competition I used, adn even though it’s not open source it is free to use for development purposes and it’s also fairly easy to get a very simple game up and running in no time (in most cases). My distaste for Vuforia comes more from some of their decision in the past few months and namely their transition away from using simple fiducial markers and to using their own VuMarkers that are difficult to make. And requier Adobe Illustrator to make.
Saying that. We still decided to use it.

## Our idea

Our idea for the project was fairly simple. I am pretty sure most of you are familiar with the book series _"Where's Wally"_ also known as  _"Where's Waldo"_. In case you are not _"Where's Wally"_ is a seris of children book in which you have a simple picture of a crowded or otherwise busy place and your task as a reader is to look thorugh it and find the titular character _Wally_. This is suposedly made easier since Wally is wearing a very noticable red and white striped shirt but even with this knowledge is usually fairly chalanging. Especially since most of the pictures include red herrings in the form of other red and white stripped objects that are not Waldo.
To "Enhance" (_read as: help you cheat_) this book we decided to make an application that will highlight Waldo on the page. Either to confirm that you found the correct Waldo on the page, or more likely. To cheat (As I would).

![Page from _"Where's Wally"_]({{site.url}}/images/MixWeekOneWaldo/waldo_unsolved.jpg)

## Our solution

The solution was very simple. Vuforia, among other things, allows you to do so called **Image targets**. With Image targes you can train Vuforia to track any image you want. As long as it's complexe enought and has enought contrast points. The process for this is very easy. All you need to do is upload the image to their cloud and in return you'll recieve a target pack you can just drop into your Unity/Vuforia app and the app will automatically track the image once the camera sees it.

![Vuforia target manager]({{site.url}}/images/MixWeekOneWaldo/target_manager.JPG)

Once this was done. We simply attached child objects to the marker in unity to show Waldo and other interesting points on the page. Interesting fact: We used characters to display things on the screen. So the circle around Waldo is actaully just an red upper case <font color="red">O</font>

![Project open in Unity]({{site.url}}/images/MixWeekOneWaldo/waldo_unity.png)

Last build time: {{ site.time }}