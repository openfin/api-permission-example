# api-permission-example
Example of setting OpenFin API permissions

Example security policies for OpenFin API are defined in permissions.json.  To enable the policies, 

1. Create the following key in Registry:

HKEY_CURRENT_USER\Software\OpenFin\RVM\Settings\DesktopOwnerSettings="http://localhost:8080/permissions.json"

2. Add " --enable-strict-api-permissions " to runtime->arguments in app manifest.

Naviation policies can defined in app manifest as followings:

    "startup_app": {
        ....
        "contentNavigation": {
            "whitelist": [ "https://www.apple.com/", "http://localhost:8080/*"],
            "blacklist": [ "https://www.facebook.com", "https://cnn.com"]
          }  

whitelist takes precedence.

To run the example

1. host the repo at localhost:8080
2. run
    OpenFinRVM.exe --config=http://localhost:8080/app.json
3. open devtools to check result of launchExternalProcess and executeJavaScript
4. try window.open with URls that are listed in whitelist and blacklist    