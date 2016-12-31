pimatic-pushbullet
=======================

A plugin for sending [pushbullet](https://www.pushbullet.com/) notifications in pimatic.

Configuration
-------------
You can load the backend by editing your `config.json` to include:

    {
      "plugin": "pushbullet",
      "apikey": "xxxxxxxxxxxxxxxxxxxxxxxxxx"
    }

in the `plugins` section. You can indicate which Device or E-Mail or Channel should be pushed to. For all configuration options see [pushbullet-config-schema](pushbullet-config-schema.coffee)

Currently you can send pushbullet notifications via action handler within rules:

    if X then push title:"title of the push notification" message:"message for the notification" type:"note|file" channel:"channeltag" (email|device):"device or email"

The channel setting will overwrite the device setting.

Example:
--------
By default if the type is not specified it sends a note notification

    if it is 08:00 push title:"Good morning!" message:"Good morning Dave!"

if you want to send a file you need to specify 'file' as type and in the message the location of the file like:

    if it is 10:00 push title:"Good morning!" message:"/home/pi/photo.jpg" type:"file"

if you want to send a file or note to a specific channel you can add channel to your rule:

    if it is 8:00 push title:"Good morning!" message:"Good morning to all of you" channel:"my_flatmates"

if you want to send a note to a specific device:

    if it is 8:00 push message:"Good morning to all of you" device:"your_device"

if you want to send a note to another pushbullet user:

    if it is 8:00 push message:"Good morning to all of you" email:"another.user@gmail.com"
