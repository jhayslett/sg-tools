####Store Number Validation
######Written By jhayslett
___
####Purpose
To validate a field that had 2 digits in it. This value was also being used to create an email, so the number had to be 2 digits. This meant if the number was a single digit (1-9), then it needed to append a leading 0; ex: 01,02,03...

####SG Features
On the input field I used the following RegEx  **^\d{2}$**
> **(Regex Breakdown)**      
> ^ - begin the regex string  
> \d - counts a digit  
> {2} - counts how many of the previous statement  
> $ - end the regex string

####Code
This code should be inserted at the end of the page containing the text input field that you would like to use this on.
```javascript
 $("**input-selector**").change(function(){  // insert your selector for the text input field in the bold  
	  var $input = $(this).val();  
	  if ( $input >= 1 && $input <= 9) {  
	    $(this).val("0" + $input);  
   }  
 })
```
