---
layout: blog
title: "How to Test Django Locally on a Mobile Device"
---

I'm currently working on a mobile oriented web application in Django. To test the application as I develop locally, I use my iPhone and Android tablet. Since these devices are connected to the same local network, with some simple configuration, I can use them to access the Django dev server running on my laptop, with some simple configuration.  I'm using Ubuntu 13.04, but the concepts here will be similar for all operating systems.

## Step 1: Open port in firewall
The first step is to open up port 8000 on your dev machine's firewall.  In Ubuntu, this looks like this:

{% highlight sh %}
$ sudo ufw enable 
$ sudo ufw allow 8000
{% endhighlight %}

And that's it!  To learn more about ufw, checkout out the [docs](https://help.ubuntu.com/community/UFW).

## Step 2: Determine local IP address
You'll need know what the IP of your dev machine is on your local network.  If you don't know this already, you can find out using the 'ifconfig' command:

{% highlight sh %}
$ ifconfig
{% endhighlight %}

Look for your "inet_addr" for the appropriate network adapter.  For this example, I'm on 192.168.0.5.

## Step 3: Start Django development server

This is where I went wrong the first time I tried to do this. Typically, I start my dev server as follows:

{% highlight sh %}
$ python manage.py runserver
{% endhighlight %} 

This starts the dev server running on localhost port 8000.  However, if you try to access the server from another device, it won't work, even with port 8000 open.  Instead, note your IP address from before, and start the server using your IP address as a parameter:

{% highlight sh %}
$ python manage.py runserver 192.168.0.5:8000
{% endhighlight %}

This will make the dev server accessible to your local network by.

## Step 4: Access site on mobile browser

The key here is to make sure that your mobile device is connected to your local wi-fi network.  This obviously won't work if the device is connected to the cellular network without a VPN or some other trickery.  Once you're on wi-fi, you can point your mobile browser to '192.168.0.5:8000' and access your app!

## Final Thoughts

Not a complicated workflow here, but hopefully these instructions save someone a few minutes of head scratching. There is no reason not to test on mobile during development, so be sure to try this out.