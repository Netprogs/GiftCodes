GiftCodes
=========

### Download:

https://github.com/Netprogs/GiftCodes/downloads


### Requirements

This plug-in requires you to have a MySQL server setup. There is no flat-file option.


### Commands:

* /giftcodes    	 		- Request a gift
* /giftcodes give <token>		- Push someone's token through for them (also called by web to do the redeem)
* /giftcodes reload 			- Reload the configurations
* /giftcodes help 			- Help page

Alias: /giftme


### Permissions:

* giftcodes.giftme	- Ability to request a gift.
* giftcodes.give		- Ability to use give command.
* giftcodes.reload	- Ability to use reload command.


### Installation

There are two files required for the installation:

* GiftCodes-xxx.jar. This is the Minecraft plug-in itself. Place into plugins folder and reload/restart.
* GiftCodesWeb.zip. This is the php/html portions. These must be extracted onto your web server and made publically available.


### Configuration

The web portion also needs to be configured. These settings can be found in the widget_interface.php class.

On your Minecraft server, you need to edit server.properties to ensure the following is set:

* enable-rcon=true
* rcon.port=25575
* rcon.password=Password


### Web Templates

GiftCodes uses templates to load the "look & feel" of the Widget. These can be found in the "templates" folder.

You should modify these as needed to fit your needs. 

DO NOT remove the {field_name} values as they are required to fill in the important responses from the widget_interface.php.


### Debugging

If you run into problems with the web interface not giving a response, you can try to run the URL yourself directly.

To check the validation:

http://WEBSITE/giftcodes/widget_interface.php?gift_token=TOKEN_VALUE_HERE&action=validate

To check the redeem:

http://WEBSITE/giftcodes/widget_interface.php?gift_token=TOKEN_VALUE_HERE&action=redeem


