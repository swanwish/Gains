# "unexpected token <"" exception

Today, I encounter an error on the page, the error message is: unexpected token <
And both Chrome and Safri point to first line, because the first line is <!DOCTYPE html>, and it has no problem.
Later, I find the problem, because I include jquery and bootstrap js file, but the file name was wrong.
But the browser didn't show me that the file not exists, but show me unexpected token < error.
It's really confuse me.
