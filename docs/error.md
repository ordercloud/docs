# Errors

The Ordercloud API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request was invalid. Please review the message returned for the cause.
401 | Unauthorized -- You have used incorrect credentials or [X-Ordercloud-Organisation](##X-Ordercloud-Organisation)
403 | Forbidden -- You do not have permissions to make the call
404 | Not Found -- The requested resource was not found. Check the message for more details
405 | Method Not Allowed -- The method is not supported for the endpoint
406 | Not Acceptable -- You requested a format that isn't json
429 | Too Many Requests -- You have hit your rate limit. Slow down or upgrade.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarilly  offline for maintenance. Please try again later.
