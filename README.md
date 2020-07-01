# thinking_in-java_NOTES
<br>
# Error Handling with Exceptions
<br>
One of the important guidelines in exception handling is "Don’t catch an exception unless you know what to do with it." 
<br>
Checked exceptions complicate this scenario a bit, because they force you to add catch clauses in places where you may not be ready to handle an error. This results 
<br>
in the "harmful if swallowed" problem:
<br>
try {
// ... to do something useful
} catch(ObligatoryException e) {} // Gulp!
