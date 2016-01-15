###Store Number Validation
#####Written By jhayslett
___
####Purpose
To validate a field that needs to be between 0 and 99 and contain 2 digits (01,02,03).

####Thought Process

1. Use javascript & jquery to watch the value of the input field and adjust it so it contains two digits when necessary.  
2. Use regex inside the SurveyGizmo interface to validate the input field value. This can be seen as optional step, but I use it to be safe. If the javascript is working, then the regex should validate properly.

####Code - Javascript & Jquery
This code should be inserted at the end of the page containing the text input field that you would like to use this on.
```javascript
 $("**input-selector**").change(function(){  // insert your selector for the text input field in the bold  
	  var $input = $(this).val();  
	  if ( $input >= 1 && $input <= 9) {  
	    $(this).val("0" + $input);  
   }  
 })
```

####Regex
Using the SurveyGizmo Interface(Textbox Input Field Properties>>Validation) set Answer Format as RegEx with the following code: **^\d{2}$**
```
^ - begin the regex string  
\d - counts a digit  
{2} - counts how many of the previous statement  
$ - end the regex string
```
