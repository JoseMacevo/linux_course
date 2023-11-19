### Wildcards

*We can look for a file name using wildcards.*

1. ? -> Matches with any single carachter.
2. \* -> Matches with any carachter chain.   
3. [set] -> Matches with any group of carachters, for example [adf] will match with any occurrence of a, d or f.
4. [!set] -> Matches with any carachter that isn't inside the carachters group.

To locate files with ? wildcard, we've to change any unknown character for ?. For example, if we now that only the
first two letters are 'ba' of three letters with an extension .out, we only need to write **ls ba?.out**.

To locate files with * wildcard, we've to change he unknown chain for *. For example, if we only remember that the 
extension was .out, we only have to write **ls *.out**.

Examples:

- du -sh a* -> We can locate all files with the letter a in the name.
- du -sh a \*log* -> We can locate all files with the .log on it's name.
- du -sh a[p-z]* -> We can locate the files that starts in between the p and z letter.
- du \*.?.* -> We can locate the files with a unknown character in between two points.

We can use the same wildcards with the ls command.

