# t-hotel-search Specification

### Component Use

``` html

<t-search 
		options={{searchOption}} 
		resources={{resources}} 
		init-model={{searchModel}} 
		on-do-search="{{doSearch}}"
		lang="en">
</t-search>

```


### Search Option to Component

```javascript

	var searchOption ={
		traveller:{
			minAdultCount : 1,
			maxAdultCount : 6,
			minChildCount : 0,
			maxChildCount : 6,
			totalRoomPaxCount : 9,
			minChildAge : 0,
			maxChildAge : 12,
			defaultAdultCount : 2,
			defaultChildCount :0,

			defaultSelectOption : [
				{ 
					room : 1,
					adult : 1
				},
				{ 
					room : 1,
					adult : 2
				},
				{ 
					room : 1,
					adult : 3
				}
			]
		},
		// If maxRoomCount is greater than 1, this will be treated as MultiRoom booking scenario
		maxRoomCount : 4,
		date : {

			// check-in allowed from current date. Value 0 means same day seach allowed.
			checkInAllowFromNow : 0,

			// Duration between check-in and check-out date
			maxStayDuration : 30,

			//default checkout date if check-in date is selected
			defaultStayDuration : 1,

			format : "mm/dd/yyyy"
		}

	}
```

### Globalization Resource Input

```javascript
	var resources = {
		labels : {
			adult : 'Adult',
			children : 'Children',
			child : 'Child',
			age : 'Age',
			room : "Room"
		},
		watermark : {
			checkIn : "MM/DD/YYYY",
			checkOut : "MM/DD/YYYY",
			hotelLocation : "City, Airport, Address or Point of Interest"
		}
	}
```

### Search Model 

```javascript
	var searchModel = {
		"destination": {
			"id": 1235,
			"name": "Las Vegas, NV, US",
			"geoCode": "36.23305,-115.2423",
			"type": "City",
			"code": "LAS",
			"formattedAddress": "Las Vegas, NV, US"
		},
		"checkInDate": {
			"date": "01/10/2017",
		},
		"checkOutDate": {
			"date": "01/15/2017",
		},
		"rooms": [
			{
				"adults": {
					"quantity": 1,
					"type": "Adult",
					"ages": [
						25
					]
				},
				"children": {
					"quantity": 1,
					"ages": [
						2
					],
					"type": "Child"
				}
			}
		],
				
		"type": "Hotel"
	}
```

## Important Information

- Auto-suggest - When user start typing auto-suggest should suggest results only after entering minimum 3 char.
- Auto-suggest - Once user stop entering the data, auto-suggest should fire after a gap of 50 ms (Milli seconds).
- Auto-suggest - Text box (Destination) will show loader while processing and after selection of item, it shoul started showing cross icon to clear the data.
- Auto-suggest - Should allow user to select an items says "Las Vegas, NV, United States - McCarran International Airport (LAS)" but after selection in text box it will appear as "LAS - Las Vegas" (Short version)
- Auto-suggest - Spec should categorised with CITY / AIRPORT and POINTS OF INTEREST. 
- Auto-suggest - On selection of search button pass on the location object of user selection.
- Component Events - doSearch (Triggers	event with search data) and initializeSearch (Listens to this event to set defautl state as per data passed)
- Misc items to be handled from CSS like:
1. Background color of outer container.
2. Mixin (to control outer width)
3. Button color etc.


## Test Cases

- Basic validation - Don't enter or select anything and click Search
- Validations - If Pax count is having child than age selection should be mandatory
- Date - Checkin/Checkout - Calender should be available
- Date - User should allow to type in Checkin/checkout dates
- Destination - If user don't select from autosuggest and click search with proper dates
- Auto-suggest - When user starts typing auto-suggest should start giving results after min. 3 char
- Auto-suggest - Should fire when user stop typing - Gap should be min 50ms
- Auto-suggest - Destination text box to show loader while processing and cross icon after selection to clear
- Button name should change on click of Search to "Searching" or whatever the name set in property

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calender element and textboxes etc.)
- You can use some Tavisca's elements like auto-suggest if required from https://github.com/atomelements/t-autosuggest but all the features and properties mentioned in scope should be added. (Fork the existing element and create V2)
- APIs Integration - Use Tavisca's APIs for integration purpose.

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for search components - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/212067485
- API access : Url - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
