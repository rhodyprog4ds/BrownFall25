# Common Code Errors


(keyerror)=
## Key Error

If you get a key error for a pandas operation, it means that the column name as you typed it is not in the DataFrame. Check the spelling, leading or trailing whitespace can be especially troubling.


(boundmethod)=
## <bound method> ....

You're probably missing `()` on a method, so Python returned the method itself as an object instead of calling it and returning the output.

