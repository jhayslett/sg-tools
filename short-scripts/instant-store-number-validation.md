###Instant Store Number Validation
#####Written By jhayslett
#####Last Updated: 02/03/2016
___
####Purpose
To change the value of the Store Number input field to match specific formatting. 

####Thought Process

1. Use javascript and jquery to watch a text input field so when the value changes it will adjust to have 3 capital region number with a space and 2 digits proceeding.


####Javascript Action
Insert a Javascript Action at the end of the page containing the text input field that you would like to perform this step of the validation.
```javascript
$('input selecter').change(function(){  // insert your selector for the text input field in the bold
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
