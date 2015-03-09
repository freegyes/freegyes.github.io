---
layout: post
title: Meteor: scraping a website outside your domain
tags:
- meteor
- javascript
---

Go out and fetch the title of a website not on your server.

In the `/server/app.js` file:

```javascript
Meteor.startup(function () {

  Meteor.methods({
    scrapeTitle: function(url) {
      check(url, String);

      var result = Meteor.http.get(url);

      var str = result.content;
      var title = str.substring(str.lastIndexOf("<title>")+7,str.lastIndexOf("<\/title>"));

      return title;

    }
  });
});
```

In the corresponding template helper:

```javascript
Template.templateName.created = function() {
  Session.set('title', '');
}

Template.templateName.helpers({
  titleOfPage: function() {
    return Session.get('title');
  }
});

Template.templateName.events({
  'click .callServer': function() {
    Meteor.call('scrapeTitle', url, function(error, result) {
      if (error) return alert(error.reason);
      $('#title').val(result);
      Session.set('title', result);
    });
  }
});
```

In the template:

```html
<button class="callServer" type="button">Suggest title</button>
<input type="text" id="title" name="title" value="">
```

needed Meteor packages:
  - [http](https://atmospherejs.com/meteor/http)
  - [audit-argument-checks](https://atmospherejs.com/meteor/audit-argument-checks)