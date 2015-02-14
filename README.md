# AndroidBrowser
![alt tag](https://www-s.acm.illinois.edu/sigmobile/sig_mobile-01.png)

Tutorial for SiGMobile to create a functional Android browser with Javascript and HTML.

This tutorial will run you through learning the tools you need to create a browser application with a URL navigator

#Step 1

Open up Android Studio and create a new project. Create a Blank Activity. Set the minimum API to KitKat.

![alt tag](http://i.imgur.com/VeQyOZJ.png)
![alt tag](http://i.imgur.com/muncqjk.png)


#Step 2

Create a WebView in your activity_main.xml the Text way. A WebView is a generic Android view that shows web pages.

![alt tag](http://i.imgur.com/fXnfy1p.png)

in order for your Activity to access the Internet and load web pages in a WebView, you must add the INTERNET permissions
to your Android Manifest file:

![alt tag](http://i.imgur.com/i1H2nRI.png)

#Step 3

Instantiate a WebView object in your Main Activity, and find the WebView you created in your activity with the
findViewByID Method.
Enable Javascript with the setJavaScriptEnabled(boolean x) method, and load a URL.

![alt tag](http://i.imgur.com/xgmzAkI.jpg)

#Step 4

Run your code:

![alt tag](http://i.imgur.com/k28D4Ws.png)


#Step 5

Now that you have a working web browser, lets set up a URL navigator so you can go to different websites.
Go to the Design tab of your activity_main.xml. Locate "Plain Text" under Text Fields on your palette. 

![alt tag](http://i.imgur.com/CDxfNhQ.jpg)

Drag it over to your Device Screen and position it above your WebView. Also, delete the Hello World TextView.

![alt tag](http://i.imgur.com/B6z1LCq.jpg)

Go back to your text tab of your activity_main and locate the EditText that was generated. You want to add two additional
lines to specify that the text field will be taking URL's. One sets it to a URL field, and the other adds an option to
set up a reaction when the send button is pressed:

![alt tag](http://i.imgur.com/KqXTyAa.jpg)

#Step 6

Same as you did with the WebView, instantiate the EditText object and link it with the View in your main activity XML

![alt tag](http://i.imgur.com/1CMKbLv.jpg)


#Step 7

When you type in a URL and hit enter, you want Android to take the URL and load the website in your WebView.
You can do that with an Activity Listener.

You want to create a Listener that will execute an action (loading the webpage) when a button (the enter key) is pressed.

![alt tag](http://i.imgur.com/4k8xM3p.jpg)


In your listener, you are Overriding the onEditorAction method to listen for the enter key (ActionID=IME_ACTION_SEND),
and loading the URL currently typed into the EditText when the key is pressed.


#Step 8

If you run your app at this time, you'll notice that when you load a new URL, the default Browser app in Android opens.
This happens because when the Intent to load the page is created, Android uses the default loader to load the webpage.
For the page to load in your WebView, you want to override the intent to open the Browser.
To do this, create a new Java Class that extends the WebViewClient class:

![alt tag](http://i.imgur.com/pPtAT6j.jpg)
![alt tag](http://i.imgur.com/ANi6FTA.png)


In this class, you want to override one method in the WebViewClient class called shouldOverrideUrlLoading(Webview, String)
You want to return false if you are creating an Intent to load a webpage, so that it loads in your
Webview and not the default Browser:

![alt tag](http://i.imgur.com/XRmq1V2.png)


#Step 9

The last thing you need to do in your Main Activity class is to set the client to your child class instead of the
generic WebViewClient class so that your code uses the overriden method you created in your class:

![alt tag](http://i.imgur.com/Ynir2Rt.jpg)


#Step 10
Run your App!



#Step 11 (Optional add-on)

You might notice if you press the back button, the app will exit. Traditionally, when you press the back button
in a browser, it should go to the previous page. There is an easy way to set up this functionality in Android

To do this, Override the system method, onBackPressed(). Make it such that if your WebView can go back, it will
go to the previous page. Else the method will call its super, or parent method in the Android system

![alt tag](http://i.imgur.com/mHiYIfU.jpg)

Once you override the method, see Step 10!


#Congratulations, you created a functional Android browser!
