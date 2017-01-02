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
					adult : 2,
					child : 1
				}
			]
		},
		multiRoomEnable : true,
		maxRoomCount : 4,
		date : {

			// check-in allowed from current date. Value 0 means same day seach allowed.
			checkInAllowFromNow : 0,

			// Duration between check-in and check-out date
			maxDuration : 30,

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

## Information

- Auto-suggest - When user starts typing auto-suggest should start giving results after min. 3 char
- Auto-suggest - Should fire when user stop typing - Gap should be min 50ms
- Auto-suggest - Destination text box to show loader while processing and cross icon after selection to clear


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

## Other Information
- Set Hithub repository at your end for this project, we will merge them later
- For development use Google or Vaadin's elements/components while development.
- Some elements like auto-suggest can be used of Tavisca's but all the features and properties mentioned above in scope should be added by Waain
-Performance test standard  - If you open the component in web page tester, it should load under 500ms.
