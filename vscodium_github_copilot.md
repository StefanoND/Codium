# [Original Guide](https://github.com/VSCodium/vscodium/discussions/1487)

## Putting in here for safekeeping

1. Install VSCodium and Copilot extension (you can download the vsix here https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)

2. Edit `VSCODIUM_FOLDER/resources/app/product.json`. Find the `GitHub.copilot` and make it look like this:

       "GitHub.copilot": [
         "inlineCompletions",
         "inlineCompletionsNew",
         "inlineCompletionsAdditions",
         "textDocumentNotebook",
         "interactive",
         "terminalDataWriteEvent"
       ],

5. Open a terminal and send a request to begin Github authorization

       curl https://github.com/login/device/code -X POST -d 'client_id=01ab8ac9400c4e429b23&scope=user:email'

6. You'll see `device_code` and `user_code` in the response (Look for `DEVICECODE` and `USER-CODE`)

       device_code=DEVICECODE&expires_in=899&interval=5&user_code=USER-CODE&verification_uri=https%3A%2F%2Fgithub.com%2Flogin%2Fdevice

7. Go to https://github.com/login/device/ in any browser and enter the `user_code`

8. Return to the terminal and send (Replace `YOUR_DEVICE_ID` with the `device_code` you got earlier)

       curl https://github.com/login/oauth/access_token -X POST -d 'client_id=01ab8ac9400c4e429b23&scope=user:email&device_code=YOUR_DEVICE_ID&grant_type=urn:ietf:params:oauth:grant-type:device_code'

9. You'll see your `access_token` in the response (gho_...). Past it in VSCodium when the Copilot extension requires authorization.

10. Enjoy your freedom!
