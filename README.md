# Dwaynes-Tours

This is my free to use repo of Drupal 8 tours.  

Are they "official" ones?  

No.  

Are they free to use and contribute to? 

Yep.  


## About this repo

The [Tour module](https://www.drupal.org/docs/8/core/modules/tour/overview) is already in core and is enabled by default.  But other than the ["Edit Views" pages](https://www.drupal.org/docs/8/core/modules/views/give-a-custom-name-to-a-field-in-the-views-edit-screen) Tour none are included or turned on by default.  It is us as the site builder to implement these specific to our audience.  

These are meant to be Tours you can implement as is, if you like the tone of my voice and trust me to explain things correctly.  What I hope is that you will use this repository to get a quick start on making your own Tours for your users.  

I am happy to take pull requests


## Adding the Tours to your site

To use Tours, you just import the .yml into your configuration.  There are multiple ways up the mountain and you should really read the docs on [Configuration Management](https://www.drupal.org/docs/8/configuration-management/managing-your-sites-configuration).  

How _I_ do it is one at a time, using the Configuration Single Import found at /admin/config/development/configuration/single/import.  Simply select Tour as the Configuration type and paste in the contents of the file, and confirm import.  Quick and easy.

You can also zip up all the .yml in the 'tour' folder into a bundle and bulk import.  Or you can add to the file system and [synchronize](https://www.drupal.org/docs/8/configuration-management/workflow-using-the-drupal-ui).



### Building your own.

**Before you begin:**

It is a really good idea to go read all the options and proper docs at the [Tour API overview on Drupal.org](https://www.drupal.org/docs/8/api/tour-api/overview).  I using things like `location` and `data-class` are options I am not going to dig into here.  

Building your tour

1. Copy the `tour.tour.TEMPLATE.yml` file into a new file called `tour.tour.<new-tour-name>.yml` 

2. Find these 2 variables which we will replace: 
	1. `<MODULE_PAGE>` - This is the name of this tour as the machine will understand it.  I am suggesting that we use the same name for both the `ID` and the `label`, though they can differ if you have good cause.

	2. `<module>` - This is the module where we want to display the Tour.  If you globally replace this, it will show you were to find routing and give you a jumping off point for naming the pieces.  


3. Write your Introduction tip.  
This one just requires replacing the `label` and the `body` text.  Most basic HTML elements can be inserted here. You can write multiline yaml using the `>` or `|` notation, but to get multi-line breaks you will need to use `<br>`. 

> Note: All individual screens that are displayed when using the Tour are called 'tips'.  

4. Write the rest of the tips.  

The name of the tip (which I called `<module>-THING-YOU-ARE-EXPLAINING:` in tour.tour.TEMPLATE.yml) is the human readable name, it does not actually show up in the Tour itself.

`id` - the element id you want to tie this tip to. For example, if I wanted to explain how to use a password edit field, I would inspect element and find that the `input id="edit-mail"` and set my id to `edit-mail`

`plugin: text` - This should be left alone for now.  Core only ships with the TipPluginInterface text plugin.  If you want to display other things, you can, but you need to work with the API directly and is out of scope for this project

`label` and `body` - Most basic HTML elements can be inserted here. You can write multiline yaml using the `>` or `|` notation, but to achieve line breaks when displayed, you will need to use `<br>`. 

`weight` - This is the order you want to display the tips. If not set, it will not display the tip.

`attributes:` - Where the tip literally points to on the page.  You set the `data-id:` OR `data-class:` under it.  For my examples I am assuming the id from earlier will match but you can point anywhere.  If this is missing the tour just hovers over center of the page  

5. Repeat step 4 until you have explained the entire admin experience to your liking

6. Write your "Continuing on" conclusion

I think this is an awesome chance to tell folks where they can find more information and give tips about using the module that didn't fit in elsewhere in the tour.  No hard requirement on having this though.  Just make sure you are setting the correct `weight` because setting it to "N", as I do in the TEMPLATE makes it not show up


## Thanks for making Tours and for using the ones we are writing here

