###Phone Number Validation
#####Written By jhayslett
#####Last Updated: 01/25/2017
___
####Purpose
To change the value of the Phone Number input field to match a specific formatting.  
**Example**  
661-979-1234  
OR  
979-1234  

####Thought Process  
1. Use JavaScript to oversee all text input fields that require a phone number. When the value changes, make it a specific formatting with dashes to provide clean reporting with consistent formatting.  
2. Use RegEx inside SurveyGizmo question properties as a backup to ensure the correct format phone number is being submitted.

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
  console.log(items);
  console.log(itemAmount);
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

**Parameters need to edit**

####Regex  
