# pushService plugin for Snaphy


###A plugin for adding push service

###This plugin is exposed on  `/pushService` route


for more info : https://docs.strongloop.com/display/public/LB/Push+notifications
```
	$npm install  loopback-component-push --save
	
   //In server/datasources.json
   "db": {
      "connector": "mongodb",
      "url": "mongodb://demo:L00pBack@demo.strongloop.com/demo"
   },
   "push": {
     "name": "push",
     "connector": "loopback-component-push",
     "installation": "installation",
     "notification": "notification",
     "application": "application"
   }


   //Create  models installation, application, notification and push.
   //Now add models and GCM key detail to package.json file

}
```


#Docs
1. Add the following models given in database-format to `common/models/` directory.
2. Now add following configuration to `model-config.json` 
```
  "application": {
    "dataSource": "mongodb",
    "public": true
  },
  "installation": {
    "dataSource": "mongodb",
    "public": true
  },
  "notification": {
    "dataSource": "mongodb",
    "public": true
  },
  "push": {
    "dataSource": "push",
    "public": true
  }
```
3. Go to plugins folder of `pushService` execute at terminal 
```
//Install push service depedencies.
$ yo snaphy:updateNpm
```

4. Now open files `datasource.json`, `datasources.*.json` and add following lines.
```
{
  "push": {
    "name": "push",
    "connector": "loopback-component-push",
    "installation": "installation",
    "notification": "notification",
    "application": "application"
  }
}
```


> `common/settings/pushService/conf.json`
```
"PUSH_SERVICE_ID": "easyPoints-snaphy-push-application",
  "USER_ID": "snaphy",
  "APP_NAME": "PUSH_APP_NAME",
  "GCM_SERVER_API_KEY" : "AAAAOO-vEL8:APA91bGJKAXzK0isqCqNbrml0FRDSgpaLRZsKnJAtzxYlIGAPxf51gleMxMEl-4M9PhM7mo-effCnpNw7qQwFpu8HJAYXALjwzXU8g-J-Cruijv-w4WK7f69YLb6AYnNM80WtnY0FU6e",
  "APPLE_SETTINGS":{
    "apnsCertData":"",
    "apnsKeyData": ""
  },
```
>NOTE: PUSH_SERVICE_ID must be the same in both APP and Backend.

#Future RoadMap
1. Implement support for multiple push for user having multiple active devices logged in. Hint create a seperate model for storing registration id.







####Written by Robins Gupta

