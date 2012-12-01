#ColorPicker

This is **yet another colorpicker** plugin for jQuery since most of them are not on GitHub nor being mantained at the moment.

The plugin is a fork of the one developed by Stefan Petre who seems not to be interested in it anymore. I needed a powerfull colorpicker for one of my projects so I updated it and then thought it would be nice if it would were freely available.

You can see the [demo][] now.

##Features

- Flat model - as element in page, attached to an input and custom widget.
- Powerful controls for color selection  
- Easy to customize the look by changing some images  
- Fits into the viewport  
- Powerful callback system to totally control the way it works

##License

The plugin is currently dual licensed under the MIT and GPL licenses.

##Implement

Attach the Javascript and CSS files to your document. Edit CSS file and fix the paths to images and change colors to fit your site theme.

        <link rel="stylesheet" media="screen" type="text/css" href="css/colorpicker.css" />  
        <script src="js/colorpicker.js"></script>

##How to use

All you have to do, is to select the elements in a jQuery way and call the plugin over them.

        $('input').ColorPicker(options); 

##Options
An object containing parameters. Please, note that all parameters are optional. 

>  **eventName** (*string*): This is the desired event to trigger the colorpicker. Default: 'click'  

> **color** (*string* or *object*): The default color. String for hex color or hash for RGB and HSB ({r:255, r:0, b:0}) . Default: 'ff0000'

> **flat**	(*boolean*):  Whether if the color picker is appended to the element or triggered by an event. Default false

> **livePreview** (*boolean*): Whether if the color values are filled in the fields while changing values on selector or a field. If false it may improve speed. Default true

> **onShow** (*function*): Callback function triggered when the colorpicker is shown

> **onBeforeShow** (*function*) Callback function triggered before the colorpicker is shown

> **onHide** (*function*): Callback function triggered when the colorpicker is hidden

> **onChange** (*function*): Callback function triggered when the color is changed

> **onSubmit** (*function*): Callback function triggered when the color is chosen

##Methods

If you want to set a new color.

        $('input').ColorPickerSetColor(color);  

The 'color' argument is the same format as the option color, string for hex color or object for RGB and HSB ({r:255, r:0, b:0}).

##Examples

###Flat mode

        $('#colorpickerholder').ColorPicker({flat: true});  

Custom skin and using flat mode to display the color picker in a custom widget.

        $('#colorpickerholder2').ColorPicker({  
        	flat: true,  
        	color: '#EFEFEF',  
        	onSubmit: function(hsb, hex, rgb) {  
        		$('#colorselector div').css('backgroundColor', '#' + hex);  
        	}  
        });  


Attached to a text field and using callback functions to update the color with field's value and set the value back in the field by submiting the color.

        $('#colorpickerfield').ColorPicker({  
        	onSubmit: function(hsb, hex, rgb, el, parent) {  
        		$(el).val(hex);  
        		$(el).ColorPickerHide();  
        	},  
        	onBeforeShow: function () {  
        		$(this).ColorPickerSetColor(this.value);  
        	}  
        })  
        .bind('keyup', function(){  
        	$(this).ColorPickerSetColor(this.value);  
        });  

Attached to DOM and using callbacks to live preview the color and adding animation.

        $('#colorselector2').ColorPicker({  
        	color: '#EFEFEF',  
        	onShow: function (colpkr) {  
        		$(colpkr).fadeIn(500);  
        		return false;  
        	},  
        	onHide: function (colpkr) {  
        		$(colpkr).fadeOut(500);  
        		return false;  
        	},  
        	onChange: function (hsb, hex, rgb) {  
        		$('#colorselector2 div').css('backgroundColor', '#' + hex);  
        	}  
        });
[demo]: http://belelros.github.com/jQuery-ColorPicker/ "View the demo now!"

##Thanks

I would like to thank to everybody that keeps mantaining this ColorPicker. By far, these people have been added/fixed something to this:

- [Colin Viebrock](https://github.com/cviebrock)
- [Fabian Mücke](https://github.com/fabianmuecke)
- Ken Thomson (sorry, couldn't find it's profile)
- [Daniel Macedo](https://github.com/dm)