####Store Number Validation
######Written By jhayslett
___
####Purpose
To validate a field that had 2 digits in it. This value was also being used to create an email, so the number had to be 2 digits which meant; if the number was a single digit (1-9) then it needed to export with a leading 0. ex: 01,02,03...

####SG Features
On the input field I used the following RegEx (^\d{2}$)
> (Extra Notes)
> This simple regex performs the following  
> ^ - begin the regex string  
> \d - counts a digit  
> {2} - counts how many of the previous statement  
> $ - end the regex string

####Code
This code should be inserted at the end of the page containing the field that you want to use this on.
____
>$("**input-selector**").change(function(){  
>	var $input = $(this).val();  
>	if ( $input >= 1 && $input <= 9) {  
>		$(this).val("0" + $input);  
>    }  
> })  
___


'''
what does this do
jacob
'''
