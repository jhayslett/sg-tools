###Phone Number Validation
#####Written By jhayslett
#####Last Updated: 01/25/2017
___
####Purpose
To change the value of the Phone Number input field(s) to match a specific formatting.  

####Examples
| User Input |Value Returned|
|------------|--------------|
| 12345467   | 123-4567     |
| 1234567890 | 123-456-7890 |
| 333        | Not Accepted |
| 555555     | Not Accepted |

####Thought Process  
1. Use JavaScript to oversee all text input fields that require a phone number. When the value changes, make it a specific formatting with dashes to provide clean reporting with consistent formatting.  
2. Use RegEx inside SurveyGizmo question properties as a backup to ensure the correct format phone number is being submitted.

####Question Settings  
1. Create a text input field.  
2. Access Question Properties - Validation and set answer format to RegEx.  
3. Insert the following RegEx in the field that appears: ^(\d{3})?[-]?\d{3}[-]?\d{4}$  
(A deeper dive down of the RegEx is supplied below).
4. Make sure to insert a message in the "Message to display when answer does not pass RegEx" such as, "Please insert phone number as 480-606-6000".
5. While in Question Properties, navigate to Layout - CSS Class Name and add "phoneNumber".

####Javascript Action
Insert a JavaScript action at the end of the page that the phone number text input field will live.

```js
function update(){
	var re = new RegExp("^([0-9]{3})?[-]?[0-9]{3}[-]?[0-9]{4}$");
	console.log(re.test(this.value));
	if(re.test(this.value)) {
		var updatedValue = this.value.replace(/[^0-9]/g,'');
      if(updatedValue.length === 7) {
        var first = updatedValue.substring(0,3);
        var second = updatedValue.substring(3,7);
        this.value = (first+"-"+second);
      } else if (updatedValue.length === 10) {
      	var first = updatedValue.substring(0,3);
        var second = updatedValue.substring(3,6);
        var third = updatedValue.substring(6,10);
        this.value = (first+"-"+second+"-"+third);
      }
	}
};

function addInputFields(a){
  var items = document.querySelectorAll(".phoneNumber input[type=text]");
  var itemAmount = items.length;
  for(var i = 0; i < itemAmount; i++){
  	if(a) {
  	items[i].removeEventListener("change",update)
	}
	items[i].addEventListener("change",update)
	}
}

document.addEventListener("DOMContentLoaded",addInputFields);

document.addEventListener("change",addInputFields(true))
```

####Regex  
Full Regex Statement - ^([0-9]{3})?[-]?[0-9]{3}[-]?[0-9]{4}$  
^ - begin the regex string    
[0-9] - counts each digit    
{3} - counts how many of the previous statement    
()? - allows for 0 or 1 of one of the characters in the previous statement, since the previous statement lives inside the parenthesis it allows 0 or 1 of the 3 digits  
[-] - checks for a dash character  
? - allows for 0 or 1 of one of the characters in the previous statement  
[0-9] - counts each digit    
{3} - requires 3 of the previous statement  
[-] - checks for a dash character  
? - allows for 0 or 1 of one of the characters in the previous statement  
[0-9] - counts each digit    
{4} - requires 4 of the previous statement  
$ - end of the regex string    
```  
