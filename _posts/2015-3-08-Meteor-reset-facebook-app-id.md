---
layout: post
title: Meteor: reset accounts-facebook app id without db reset
tags:
- meteor
- javascript
- facebook
---

It is possible to reset the Facebook App ID and secret without `meteor reset`.

````
meteor mongo
db.meteor_accounts_loginServiceConfiguration.find()  // use _id from here
db.meteor_accounts_loginServiceConfiguration.update({_id:"xxx"},{$set:{"appId" : "<new app id>", "secret" : "<new secret>"}});
````

needed Meteor package:

````
meteor add accounts-facebook
````