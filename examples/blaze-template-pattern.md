```html
<!-- By convention Template Start with Uppercase letter -->
<template name="Example">
  <!--  Access data via helpers  -->
  <h1>{{helperName}}</h1> 
  
  <!--  Each loop through array or cursor  -->
  {{#each helperEachName}}
    <p>{{this.name}}</p>
  {{/each}}
  
  <!--  Each loop through array or cursor with specified context -->
  {{#each exemple in helperEachName}}
    <p>{{exemple.name}}</p>
  {{/each}}
</template>
```


```javascript
import { Template } from 'meteor/templating';
import { Meteor } from 'meteor/meteor';
import './examples.html';

// Before template is rendered callback
Template.Exemple.onCreated(function () {
    // Usualy perform sub and initialize template reactive variable
	this.subscribe('Publication');
	this.exempleVar = new ReactiveVar(false);
});

Template.Exemple.onRendered(function () {
    // Autorun function are reactive function listening on reactiveVar (eg: ReactiveVar or Session variable)
	this.autorun(function () {
	  // SubscriptionsReady is a reactive function notifying us when all subscriptions performed are ended
	  if (this.subscriptionsReady()) {
	    // usualy set template variable here when data are loaded on Minimongo
	    const record = Collection.findOne(this.data._id);
	    this.exempleVar.set(record.name);
	  }
	}.bind(this))
});

// Helper function are reactive function scoped to this template only
Template.Exemple.helpers({
    // access this in the dom by calling {{helperName}}
	helperName() {
    	return Template.instance().exempleVar.get();
	},
	helperEachName() {
	  return [{
	    foo: 'bar'
	  }, {
	    bar: 'foo'
	  }];
	}
});

// Event binding on the template
Template.Exemple.events({
    // By convention event are binded on class and prefixed by js-event-name
	'click .js-class-name'(event, instance) {
    	// Meteor.call allow us to communicate with the server from the client
        Meteor.call('server.call', this, (error, result) => {
      	  if (error) {
      	    // handle error
      	    console.error(error);
      	  } else {
      	    // handle result
      	    instance.exempleVar.set(result);
      	  }
    	})
	}
});

Template.Exemple.onDestroyed(function () {
	// perform task before template is delete from DOM
});

```
