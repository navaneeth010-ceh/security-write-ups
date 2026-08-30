# Lab: Web shell upload via Content-Type restriction bypass

**Vulnerability**

Unrestricted File Upload / Content-Type Validation Bypass to Remote Code Execution

**Overview:**

The application restricts avatar uploads by checking the MIME type supplied in the upload request. However, this validation relies on the client-controlled Content-Type value and does not properly verify the actual contents or extension of the uploaded file.

By modifying the Content-Type of a malicious PHP file to an allowed image MIME type, it is possible to bypass the upload restriction and upload a web shell.

**Steps:**
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE>. Send this request to Burp Repeater.

3. On your system, create a file called exploit.php, containing a script for fetching the contents of Carlos's secret. For example:
<?php echo file_get_contents('/home/carlos/secret'); ?>
4. Attempt to upload this script as your avatar. The response indicates that you are only allowed to upload files with the MIME type image/jpeg or image/png.
5. In Burp, go back to the proxy history and find the POST /my-account/avatar request that was used to submit the file upload. Send this to Burp Repeater.
6. In Burp Repeater, go to the tab containing the POST /my-account/avatar request. In the part of the message body related to your file, change the specified Content-Type to image/jpeg.
7. Send the request. Observe that the response indicates that your file was successfully uploaded.
8. Switch to the other Repeater tab containing the GET /files/avatars/<YOUR-IMAGE> request. In the path, replace the name of your image file with exploit.php and send the request. Observe that Carlos's secret was returned in the response.
9. Submit the secret to solve the lab. 

**Impact:**

- An attacker who can bypass the upload restriction may be able to upload and execute arbitrary server-side code.
Potential consequences include:

- Reading sensitive files
- Accessing application credentials and configuration
- Modifying or deleting server-side data
- Executing commands with the privileges of the web server
- Potential compromise of the underlying application server