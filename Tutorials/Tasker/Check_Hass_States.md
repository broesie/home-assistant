# Check States of Home Assistant Devices
This tutorial will learn you how to check states in tasker of your Home Assistant devices...

## Requirements:
- An android phone
- Tasker
- (option) AutoTools (find it here: https://play.google.com/store/apps/details?id=com.joaomgcd.autotools)

### Description:
The're 2 ways to retrieve information from Home Assistant to your Tasker. You can use HTTP GET or you can use the AutoTools plugin.
Personal I prefer tot use AutoTools, because the programming is cleaner, and you don’t have to use split variables. You can realize it with only 1 action. If you don’t want to use a plugin, you still can realize is with HTTP GET…
I will explain both methods:

#### Method 1: Using HTTP GET
- Do a **HTTP GET**: as port: **yourhost/api/states/yourentity?api_password=xxxx**
In my case I use global variables, so I have it configure it 1 time in my programming. (see also how to configure Tasker for Home Assistant: https://github.com/broesie/Home-Assistant/blob/master/Tutorials/Tasker/Setting_Global_Variables.md).
So mine will be: %HASS_STATE%HASS_TOPLICHT%HASS_PSW
- Do a variable set **%source** to **%HTTPD**
Now you have to split the variables… If you don’t know what variables are, and what you can do, check my tutorial about variables: https://www.youtube.com/watch?v=F2IJJlUGF9E
- Do a variable split: **%source** splitter **“state”**
- Do a variable split: **%source2** splitter **"**
- Do a variable set: **%state** to **%source21**

your result will be in **%source21** (you can use a flash, to check it)
Then you can an if statement if you want… Eg: if **%state ~ off**, do then...

#### Method 2: Using AutoTools
- Do an **AutoTools Json Read**: **Json** is similar like the first step in method 1, **fields: state**. Also I prefer to give this action a label. Eg: **Checking device name**
- Then I do an if statement, just for if it gives a timeout, it will do it again, till it works… (in other word, it will create a loop, if it gives a timeout). You can do it like this:
  - **If %err is set**
    - **Flash: Retrying**
    - **Go to label Checking device name** (or what you have set in step 1) 
  - **End if**

your result will be in **%state** variable
