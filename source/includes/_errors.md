# Errors


The Judi Imaging and Form API uses the following error codes:

<aside class="notice">
	If a user is unauthorized user, system will automatically transfer to the log in page. Thus, there is no error report for unauthrorized user.
</aside>

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
404 | Not Found -- The requested recource is not available.
406 | Not Acceptable -- You requested a format that isn't json.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
