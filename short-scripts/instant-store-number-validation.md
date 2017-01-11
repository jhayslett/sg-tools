###Instant Store Number Validation
#####Written By jhayslett
#####Last Updated: 01/11/2017
___
####Purpose
To change the value of the Store Number input field to match specific formatting. 

####Thought Process

1. Use javascript and jquery to watch a text input field so when the value changes it will adjust to have 3 capital region number with a space and 2 digits proceeding.


####Javascript Action
Insert a Javascript Action at the end of the page containing the text input field that you would like to perform this step of the validation.
```javascript
$('input selector').change(function(){  // insert your selector for the text input field in the bold
  var input = $(this).val();
  input = input.replace(/ /g,'').replace(/[^a-z0-9\s]/gi, '');
  var region = input.substring(0,3).toUpperCase();
  var number = input.substring(3);
  var $long = number.length;
  if(number >= 1 && number <= 9) {
  	if($long == "1") {
    	number = "0"+number;  
}
  }
  $(this).val(region+" "+number);
})
```  

**Parameters need to edit**

$('input selector') - You will need to add a CSS Class Name to the Text Input Field you would like to apply this formatting to. To do so you will need to:
  1. Access the Question Properties Panel
  2. Navigate to Layout and add "store" to CSS Class Name
  3. Edit the $('input selector') in your JavaScript. If you use "store" in the previous step, you will use the following selector: $('.store input').


####Regex  
Access the Question Properties Panel for the Textbox Input Field you would like to validate. Inside the panel, navigate to Validation and set Answer Format to RegEx with the following statement: **[A-Z]{3}[WZAHXN ]?\d{2}**  
```  
Full Regex Statement - ^[A-Z]{3}[WZAHXN ]?\d{2}$
^ - begin the regex string  
[A-Z] - counts each Uppercase Character A through Z  
{3} - counts how many of the previous statement  
  [WZAHXN ] - counts each Uppercase W  
? - allows for 0 or 1 of one of the characters in the previous statement
\d - count each integer
{2} - counts how many of the previous statement
$ - end of the regex string  
```  
