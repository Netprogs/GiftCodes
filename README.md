GiftCodes
=========

Help drive visits to server websites by giving players in-game gifts for going there.

A player can request a gift using /giftme. They will then receive a token and URL to visit to redeem the token.

Their chat is paused so they can read the token without it scrolling off the page too soon. 
It is activated again after redeem is completed. They can also use /giftme chat to enable their chat sooner should they wish.

Once they visit the website and enter their token, the website will contact back to Minecraft and give the player their gift. 
They *must* be online to receive the gift, if they're not, the redeem won't be completed and will be left to try again until they are online.


### Download:

https://github.com/Netprogs/GiftCodes/downloads


### Requirements

This plug-in requires you to have a MySQL server setup. There is no flat-file option.


### Commands:

* /giftcodes          	 				- Request a gift. 
* /giftcodes give &lt;token&gt;		- Push someone's token through for them (also called by web to do the redeem)
* /giftcodes reload 				- Reload the configurations
* /giftcodes chat			 		- Enables chat again.  
* /giftcodes token			 		- Request their current token again should they need it.  
* /giftcodes help 					- Help page

Alias: /giftme


### Permissions:

* giftcodes.giftme		- Ability to request a gift.
* giftcodes.give		- Ability to use give command.
* giftcodes.reload		- Ability to use reload command.
* giftcodes.chat		- Ability to use chat command.
* giftcodes.token		- Ability to use token command.


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


### API

To use the token/gift features externally to this plug-in, you can use the following API methods.

An example on how to load the GiftCodesApi:

        // If the plugin is soft-depend, check to make sure the server has it loaded
        Plugin plugin = Bukkit.getServer().getPluginManager().getPlugin("GiftCodes");
        if (plugin != null) {

            //
            // If it is "depend", then skip the above check and just use the following code.
            //
            // "this" is the plug-in instance your calling within
            // true/false to indicate if you want GiftCodes to record debug messages in the logs
            //
            GiftCodesApi giftCodesApi = new GiftCodesApi(this, true);
            if (!giftCodesApi.isEnabled()) {

                // If it's not loaded, then disable things as needed.

            } else {
            
                // From here on, you can use the giftCodesApi instance for hooking into GiftCodes
            }

        } else {

            getLogger().info("Could not find GiftCodes; features are disabled.");
        }


Now that you have an instance, you can call the following methods:

    /**
     * Creates a new gift and token.
     * @param playerName The player to receive the gift and token.
     * @return The token string for the gift.
     */
    public String createGiftCode(String playerName);

    /**
     * Load the GiftCode java object from the database using the given token.
     * @param giftToken The gift token to load.
     * @return A GiftCode java object containing the gift details.
     */
    public GiftCode loadGiftCode(String giftToken);

    /**
     * Redeem the gift code and give the player their gift.
     * @param giftCode The gift to redeem.
     * @return True if the player was online and the gift was given. False if the player was not online.
     */
    public boolean redeemGiftCode(GiftCode giftCode);

    /**
     * Deletes the given gift code from the database.
     * @param giftCode The gift code to delete.
     */
    public void deleteGiftCode(GiftCode giftCode);
        
