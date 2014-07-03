
# Using BeforeUpload To Generate Per-File Amazon S3 Upload Policies Using Plupload

by [Ben Nadel][bennadel] (on [Google+][googleplus])

One of the really exciting things about [Plupload][plupload] is that you can use it upload files
directly to Amazon S3 from the user's browser. Of course, doing so requires an upload "Policy" 
that Amazon S3 can use to validate the uploaded file. In the past, I've somewhat hard-coded that 
policy on page-load, which has all kinds of drawbacks and security considerations.

As such, I wanted to look at Plupload to see how we could generate per-file Amazon S3 upload 
policies that could be used, on the fly, to upload a file without leaving the "upload window" open
for too long. After digging through the code, I found out that you could return "False" from the
"BeforeUpload" event handler. Doing so pauses the queue processing, which provides us with a hook
to talk to our application-server and get an Amazon S3 upload policy for the specific file.


[bennadel]: http://www.bennadel.com
[googleplus]: https://plus.google.com/108976367067760160494?rel=author
[plupload]: http://plupload.com
[angularjs]: http://angularjs.org
