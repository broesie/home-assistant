# Tasker: Setting Global variables
The reason why you have to create a configuration file, is because you can work with global variables, so you have to put 1 time all your configuration, and all the tasks in the future can use those... If something change, example a entity ID, you have to change it only in 1 task.

## Requirements:
- An android phone
- Tasker

### Step 1: Create your configuration task

So a config task would be like this in tasker:
- **Variable set: %HASS_PSW** To **?api_password=xxxxx**
- **Variable set: %HASS_SERVICE** to **http://xxxx:8123/api/services/** (if you use SSL and Let's Encrypt: then use https://yourdomainname/api/services/)
- **Variable set: %HASS_STATE** to **http://xxxx:8123/api/states/** (if you use SSL and Let's Encrypt: then use https://yourdomainname/api/states/)

Add then your devices with your correct ID of HASS below eg:
- **Variable set: %HASS_WOL** to **switch.wol**
- **Variable set: %HASS_TOPLIGHT** to **light.living_toplight**
- **Variable set: %HASS_SIDELIGHT** to **light.living_sidelight**
- etc...

After creating this, you need to run this task, so Tasker knows all the variables and remember it.
