###Store Code Validation  
#####Written by jhayslett  
#####Last Updated: 01/14/2016  
___  
####Purpose  
To validate a text input field that needs to contain 3 letters, any combination, along with 1 optional w at the end. This value also needs to be all uppercase letters.  

####Thought Process  

1. Use javascript and jquery to watch a text input field, so when the value changes it will adjust to all uppercase letters.
2. Use regex to validate the value of the text input field on submission to ensure it starts with 3 characters, A-Z, along with a 4th optional character, W. We will set the regex so it also double checks to make sure the value is all uppercase letters.

####Javascript Action

Insert a Javascript Action at the end of the page containing the text input field that you would like to perform this step of the validation.
```javascript
  $("**input-selector**").change(function () {  
    $(this).value = $(this).value.toUpperCase();  
    }  
  })  
```

####Regex  
Access the Question Properties Panel for the Textbox Input Field you would like to validate. Inside the panel, navigate to Validation and set Answer Format to RegEx with the following statement: **^[A-Z]{3}[W]{0,1}$**  
```  
^ - begin the regex string  
[A-Z] - counts each Uppercase Character A through Z  
{3} - counts how many of the previous statement  
[W] - counts each Uppercase W  
{0,1} - counts how many of the previous statement and allows for either 0 or 1 which makes this portion optional  
$ - end of the regex string  
```  
