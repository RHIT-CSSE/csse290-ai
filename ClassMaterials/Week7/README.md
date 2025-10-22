# Homework Week 7

For this assignment I'd like you to expand you service call system
from the last week with some appropriate error handling.  It's not
hard - but often folks don't think it through OR don't robustly test
and leave bugs to surface in the wild.

Here are the cases you must consider:

1.  Your call to the LLM times out (test this by disconnecting from
    the network)
2.  Your call to the LLM returns an LLM error response (test this by
    editing your key to be invalid)
3.  Your call to the LLM returns something that causes the parse to
    fail (test this by either editing the response string or by
    changing the prompt response template to be invalid json.
4.  Your call to the LLM returns parsable json but it does not have
    the correct fields

In the case of error, your systems behavior should be to retry the
request ONLY 1 TIME with the same parameter, while displaying an
appropriate retry warning message that includes the nature of the
failure AND the full text of the LLM response when possible (trust me,
that's what you'll want to see when you're trying to track down one of
these bugs).  If an error occurs on retry, the system should log again
and rethrow the exception that caused the error which should terminate
your script.

You should use exceptions to implement this behavior and you should
only catch the exceptions in one place (i.e. there should be one
handler that does the behavior for all failure types, not individual
ones for the various types).

In most cases, you should be able to catch the exceptions that the
underlying frameworks throw.  But in some cases (especially 4), you'll
want to check and throw yourself.  Using throw, by the way, is how you
should handle errors in most parts of your system: throw and let the
wider system figure out what to do.

Feel free to use AI to help you solve this problem, BUT please don't
cut and paste my instructions.  Instead, start with some more general
guidance and see how close it gets without detailed prompting.

You are REQUIRED to test for all these cases and verify that your
system works.  But I will allow you to test each case by hand rather
than using mocking and unit tests which is what you really ought to
do.

Submit your script to the dropbox.
