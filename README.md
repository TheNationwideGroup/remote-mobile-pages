# remote-mobile-pages
This public repository is created to host static remote sources that can be requested by Hybrid Mobile apps.
index.json file inside each of the application folders specifies the rules for injecting and displaying elements.
 App index.json Config Example
```JSON
{
	"guid": 2,
	"pages":{
		"MenuPage":[
			{ "action":"insertAfter", "selector": ".menu-body>.menu-tree", "sourceFile": "ads/menu/index.html","displayToUserTypes":[1,2], "displayToRegions":["ca"],"displayToLanguages":["en"] , "displayFrequency":3 } 
		],
		"Dashboard":[
			{ "action":"insertAfter", "selector": ".content", "sourceFile": "ads/dashboard/index.html","displayToUserTypes":[1,2], "displayToRegions":["ca"],"displayToLanguages":["en"], "displayInterval": "2 weeks" } 
		],
		"DetailsTab":[
			{ "action":"insertBefore", "selector": "#infos", "sourceFile": "ads/orderdetails/index.html","displayToUserTypes":[1,2], "displayToRegions":["ca"],"displayToLanguages":["en"], "displayFrequency": 2 } 
		]
	}
}
```
index.json Structure
 - guid - config ID unique value. Resets all local RemoteConfig settings (like displayInterval, displayFrequency )
 - pages - **{}** -  key-value pair of PageName - Config array values
	 - PageClassName
		 - action - **string**, insertAfter | insertBefore
		 - selector - **string**, query to select the item on the page
		 - sourceFile - **string**, relative path to html snippet/template file
		 - displayToUserTypes - **number[]** - user type_ids to display the element to
		 - displayToRegions - **string[]** - region names to display the element to 
		 - displayToLanguages - **string[]** - languages to display the element to 
		 - displayInterval - **string** - "number period" string specifying how often to show the element ex "2 weeks"
		 - displayFrequency - **number** - how often should the element be displayed ex: 5 - element displayed every fifth time

File structure

 - root
   - AppFolder
	   - index.json - json file containing rules and paths to element sources
	   -  element1 - element folder contains all assets of the element
		   - index.html - element html snippet/template
		   - logo.png 
		   - otherassets.png 
	   -  element2 
	   -  element3
