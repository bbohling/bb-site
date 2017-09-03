---
categories:
    - technology
tags:
    - coding
    - javascript
date: 2013-04-29T00:00:00Z
published: true
title: Underscore Your JavaScript This Moment
aliases: /technology/Underscore-Your-JavaScript-This-Moment/
---

Up until last year it had been many years since I had been a full-time developer. After a year back in the code, I still do not feel as competent as I felt in my prime. So maybe what I am about to share is common knowledge among the developer community, but just in case...

 If you are developing solutions using JavaScript I highly recommend you check out two helpful libraries: [Underscore][underscore] and [Moment][moment]. 

Shamelessly copied from the underscore website:

> Underscore provides 80-odd functions that support both the usual functional suspects: map, select, invoke — as well as more specialized helpers: function binding, javascript templating, deep equality testing, and so on. It delegates to built-in functions, if present, so modern browsers will use the native implementations of forEach, map, reduce, filter, every, some and indexOf.

and moment:

> A 5.5kb javascript date library for parsing, validating, manipulating, and formatting dates.

So two libraries to make a developer's life easier...perfect. Let's look at a few examples to show off their awesomeness. Keep in mind, I purposely selected more basic features just to introduce the libraries. If there is enough interest I can cover more advanced usage scenarios in the future.

## Moment

For the example we will use the following sample JSON response:

	var jsonSample = {
	  "Vacation": {
	    "StartDate": "/Date(1366182000000)/",
	        "EndDate": "/Date(1368169200000)/",
	        "Trips": [{
	        "Name": "Fun in the Sun",
	            "Origin": {
	            "Location": "Iowa City, IA",
	                "Date": "/Date(1367046000000)/",
	                "DateFormatted": "Saturday, April 27th 2013"
	        },
	            "Destination": {
	            "Location": "Phoenix, AZ",
	                "Date": "/Date(1367218800000)/",
	                "DateFormatted": "Monday, April 29th 2013"
	        }
	    }, {
	        "Name": "Family Time",
	            "Origin": {
	            "Location": "Portland, OR",
	                "Date": "/Date(1366182000000/",
	                "DateFormatted": "Wednesday, April 17th 2013"
	        },
	            "Destination": {
	            "Location": "Iowa City, IA",
	                "Date": "/Date(1366527600000)/",
	                "DateFormatted": "Sunday, April 21st 2013"
	        }
	    }, {
	        "Name": "Return Home",
	            "Origin": {
	            "Location": "Phoenix, AZ",
	                "Date": "/Date(1367910000000)/",
	                "DateFormatted": "Tuesday, May 7th 2013"
	        },
	            "Destination": {
	            "Location": "Portland, OR",
	                "Date": "/Date(1368169200000)/",
	                "DateFormatted": "Friday, May 10th 2013"
	        }
	    }]
	  }
	};

Nothing too elaborate, but hopefully should be familiar if you have worked with JSON before. If you are new to JSON, check out [this video][4]. 

First, let's address the unfriendly dates that we are sometimes served. Moment makes it a snap:

	var dt = moment('/Date(1366182000000)/');
	var humanReadableDate dt.format('dddd, MMMM Do YYYY, h:mm:ss a');

Creating a moment object is simple as the first line shows. A moment can be created from any string that can be parsed by `Date.parse`. Then, like many modern languages, formatting is as straightforward as following a certain syntax. 

If you are comfortable with how this works, then you can actually perform this as a 1-liner:

	var humanReadableDate = moment('/Date(1366182000000)/').format('dddd, MMMM Do YYYY, h:mm:ss a');

To some I am sure this simple example does not impress, but [look at the docs][5] for yourself. I doubt you will come across a scenario where Moment will not make your life easier when dealing with date and time.

To see this in action yourself: [http://jsfiddle.net/bbohling/8vDQS/][jsFiddle].

## Underscore

Underscore is not always necessary to complete a task, but it has almost always reduced my code by at least 30%. In addition, it makes the code much more maintainable in my opinion. Let's take a look at a few examples of what we can do with underscore.

### Sort: Organize Your Lists

In our `jsonSample` above the data is not sorted by date which could be an issue. With underscore, this is easily addressed:

	var sortedTrips = _.sortBy(jsonSample().Vacation.Trips, function (trip) {
	   return moment(trip.Origin.Date);
	});

First we pass in our list `jsonSample().Vacation.Trips` and then  our iterator. In this case, it means that our trips will be sorted in ascending order by each trip's origin date (we use moment to ensure a standard date is used).

Note: `jsonSample` has parenetheses because in the [jsFiddle][jsFiddle] I created for this tutorial I am using [Knockout][8], which is another fantastic JavaScript library I highly recommend.

### Some: Is there any truth in your list?

Let's say we want to know if a user is going somewhere specific. We can create a function that takes a destination and will return true/false based on if the trip is located in the `jsonSample`. This can be implemented using underscore's `some` function which again takes a list and iterator.

	tripTo = function (destination) {
	   return _.some(jsonSample().Vacation.Trips, function (trip) {
	      return trip.Destination.Location == destination;
	   });
	};  

Here we have a function called `tripTo` that has a destination parameter, which will be used in the `some` function. Similar to `sortedTrips` above we will pass our Trip list and our iterator that checks to see if the trip (destination) location is the same as the destination that was provided. As soon as one of the destination locations equals the destination argument, the function will stop traversing the trip list and `tripTo` will return true. Of course, if the destination argument does not match any of the trip locations `tripTo` will return false.

See the [example in action][jsFiddle].

### Each: Traversing Your Lists

In this final example, let's add a property to `jsonSample`. Instead of always converting the date whenever a view needs to display it, let's convert it up front. Underscore makes this a snap with the `each` function.

	newJson = function (json) {
	   _.each(jsonSample().Vacation.Trips, function (trip) {
	      trip.Origin.DateFormatted = standardDate(trip.Origin.Date);
	      trip.Destination.DateFormatted = standardDate(trip.Destination.Date);
	   });
	   return json;
	};

I'm guessing those comfortable in JavaScript can easily guess what's going on here. Thanks to the flexibility of JavaScript in our iterator we are simply adding a `DateFormatted` property to `trip.Origin` and `trip.Destination`. You can see what the updated `jsonSample` looks like when it has been sent through our `newJson` function by checking out the [jsFiddle][jsFiddle].

## Wrap-up

Again, these examples are basic, but hopefully intriguing enough to check out [underscore][underscore] and [moment][moment]. It shouldn't take you long before these two libraries are making your life as a developer much easier. 







[underscore]:	http://underscorejs.org/
[moment]:	http://momentjs.com/
[4]:	http://www.youtube.com/watch?v=9xXr2EZfDPQ
[5]:	http://momentjs.com/docs/
[jsFiddle]:	http://jsfiddle.net/bbohling/8vDQS/
[8]:	http://knockoutjs.com/
