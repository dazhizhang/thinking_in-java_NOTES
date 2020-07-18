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
<br>
http://www.psxia.com/news/show-7-1590.html
<br>
 In Java, there are restrictions on the way that Java generics can be used with exception specifications.
<br>
On top of this, there are very significant productivity benefits to reducing the compile-time constraints upon the programmer. Indeed, reflection and generics are 
<br>
required to compensate for the overconstraining nature of static typing, as you shall see in a number of examples throughout the book.
<br>

Converting checked to unchecked exceptions
Throwing an exception from main( ) is convenient when you’re writing simple programs for your own consumption, but is not generally useful. The real problem is when you are writing an ordinary method body, and you call another method and realize, "I have no idea what to do with this exception here, but I don’t want to swallow it or print some banal message." With chained exceptions, a new and simple solution prevents itself. You simply "wrap" a checked exception inside a RuntimeException by passing it to the RuntimeException constructor, like this:
<br>
try{
 // ... to do something useful
} catch(IDontKnowWhatToDoWithThisCheckedException e) {
  throw new RuntimeException(e);
}
<br>
Use exceptions to:<br>
1. Handle problems at the appropriate level. (Avoid catching exceptions unless you know what to do with them.)<br>
2. Fix the problem and call the method that caused the exception again.<br>
3. Patch things up and continue without retrying the method.<br>
4. Calculate some alternative result instead of what the method was supposed to produce.<br>
5. Do whatever you can in the current context and rethrow the same exception to a higher context.<br>
6. Do whatever you can in the current context and throw a different exception to a higher context.<br>
7. Terminate the program.<br>
8. Simplify. (If your exception scheme makes things more complicated, then it is painful<br>
and annoying to use.)<br>
9. Make your library and program safer. (This is a short-term investment for debugging, and a long-term investment for application robustness.)<br>

