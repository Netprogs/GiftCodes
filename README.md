GiftCodes
=========

Download:

https://github.com/Netprogs/GiftCodes/downloads


On your Minecraft server, you need to edit server.properties to ensure the following is set:

* enable-rcon=true
* rcon.port=25575
* rcon.password=Password


Commands:

* /giftcodes  		 		- Request a gift
* /giftcodes give <token>		- Push someone's token through for them (also called by web to do the redeem)
* /giftcodes reload 			- Reload the configurations
* /giftcodes help 			- Help page

Alias: /giftme


Permissions:

* giftcodes.giftme	- Ability to request a gift.
* giftcodes.give		- Ability to use give command.
* giftcodes.reload	- Ability to use reload command.
