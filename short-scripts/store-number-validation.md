###Store Number Validation
#####Written By jhayslett
#####Last Updated: 01/14/2016
___
####Purpose
To validate a field that needs to be between 0 and 99 and contain 2 digits (01,02,03).

####Thought Process

1. Use javascript and jquery to watch the value of the input field and adjust it so it contains two digits when necessary.  
2. Use regex to validate the input to the text field. This can be seen as optional step, but I use it to be safe. If the Javascript Action is working, then the Regex should validate properly.

####Javascript Action
Insert a Javascript Action at the end of the page containing the text input field that you would like to perform this step of the validation.
```javascript
 $("**input-selector**").change(function(){  // insert your selector for the text input field in the bold  
	  var $input = $(this).val();  
	  if ( $input >= 1 && $input <= 9) {  
	    $(this).val("0" + $input);  
   }  
 })
```

####Regex
Access the Question Properties Panel for the Textbox Input Field you would like to validate. Inside the panel navigate to Validation and set Answer Format to RegEx with the following statement: **^\d{2}$**
```
^ - begin the regex string  
\d - counts a digit  
{2} - counts how many of the previous statement  
$ - end the regex string
```
