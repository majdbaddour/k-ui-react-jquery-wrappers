# kendo-ui-react-jquery-scheduler

The Kendo UI for jQuery Scheduler widget wrapped as a React component.

***WARNING:*** Must npm install professional version of Kendo UI using credentials.

You'll need to setup a `.netrc` file on your local system. This file contains the login (username & password) of the account on telerik.com in which you purchased [Kendo UI professional](http://www.telerik.com/kendo-ui) or [DevCraft](http://www.telerik.com/devcraft).

Below are the instructions for both Windows and Mac users.

***On Windows:***

Create a text file called `\_netrc` in your home directory (e.g. `c:\users\jane\_netrc`).

Next, Declare a HOME environment variable.

EXAMPLE

```
C:\> SETX HOME %USERPROFILE%
```

Add the credentials using the format in the example above.

Git might have problems resolving your home directory if it contains spaces in its path—for example, `c:\Documents and Settings\jane`). Therefore, update your %HOME% environment variable to point to a directory having no spaces in its name.

***On Mac:***

Create a file called `.netrc` in your home directory `~/.netrc` (i.e `/User/USERNAME/.netrc`). Make sure you modify the file permissions to make it readable only to you.

Add your credentials to the `~/.netrc` (i.e `/User/USERNAME/.netrc`) file using the format from the example below.

EXAMPLE:

```
machine bower.telerik.com
    login my-telerik.identity@example.com-here
    password my-password-here
```

## Install

```bash
npm i kendo-ui-react-jquery-fixed-events-scheduler
```

## Usage Example

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import KendoScheduler from 'kendo-ui-react-jquery-scheduler';

//Don't forget CSS, webpack used to include CSS
import 'kendo-ui-core/css/web/kendo.common.core.min.css';
import 'kendo-ui-core/css/web/kendo.default.min.css';

var App = React.createClass({
  render: function() {
	  return (<KendoScheduler options={{
						date: new Date("2013/6/6"), 
						dataSource: [ 
							{
							start: new Date("2013/6/6 08:00 AM"),
							end: new Date("2013/6/6 09:00 AM"),
							title: "Breakfast"
							},
							{
							id: 2,
							start: new Date("2013/6/6 10:15 AM"),
							end: new Date("2013/6/6 12:30 PM"),
							title: "Job Interview"
							}
						]
				}}></KendoScheduler>);
	}
});

ReactDOM.render(<App />, document.getElementById('app'));
```

## React Props

Every KUI React Wrapper can make use of the following React props:

* `options`
* `methods`
* `events`
* `unbindEvents`
* `triggerEvents`

Each is demonstrated below using a `<KendoDropDownList>` KUI React wrapper.

```javascript
<KendoDropDownList
	//only updates upon state change from above if widget supports setOptions()
	//don't define events here, do it in events prop
	options={{ //nothing new here, object of KUI configuration values
		dataSource:[{
			text: "Item1",
			value: "1"
		}, {
			text: "Item2",
			value: "2"
		}, {
			text: "Item3",
			value: "3"
		}],
		dataTextField: "text",
		dataValueField: "value"
	}}
	//updates if object is different from initial mount
	methods={{ //name of method and array of arguments to pass to method
		open:[], //send empty array if no arguments
		value:['2']
	}}
	//Right now, always updates
	events={{ //name of event, and callback
		close:function(){console.log('dropdown closed')},
		select:function(){console.log('item selected')},
		open:function(){console.log('dropdown opened')}
	}}
	//updates if array is different from initial mount
	unbindEvents={[ //name of event to unbind, string
		"select"
	]}
	//updates if array is different from initial mount
	triggerEvents={[ //name of event to trigger, string
		"open",
	]}>
		<input className="kendoDropDownList" />
</KendoDropDownList>
```

## KUI API

* Scheduler demos: [http://demos.telerik.com/kendo-ui/scheduler/index](http://demos.telerik.com/kendo-ui/scheduler/index)
* Scheduler docs: [http://docs.telerik.com/kendo-ui/controls/scheduling/scheduler/overview](http://docs.telerik.com/kendo-ui/controls/scheduling/scheduler/overview)
* Scheduler API: [http://docs.telerik.com/kendo-ui/api/javascript/ui/scheduler](http://docs.telerik.com/kendo-ui/api/javascript/ui/scheduler)

## License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
