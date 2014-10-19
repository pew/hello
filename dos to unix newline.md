### convert dos newline to unix (perl)
	perl -pi -e 's/\r\n/\n/g' input.file
	
#### using sed
	sed 's/^M$//'
	
**beware:** instead of ^M type: control-V followed by control-M (you should see a special character in your terminal)