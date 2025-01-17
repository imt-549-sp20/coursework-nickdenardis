Now that you know how to fetch data from a web service, it's time to practice and demonstrate those skills on a real application. For this challenge you will fetch recent Fire 911 calls in Seattle, and plot them on an interactive map.

## Resources

The following resources will help you complete this challenge:

* [Querying Services Tutorial](https://imt-549-sp19.github.io/coursework/javascript-ajax.html)
* [Leaflet.js quick start guide](https://leafletjs.com/examples/quick-start/)
* [Fetch API overview](https://davidwalsh.name/fetch)
* [Seattle Real Time Fire 911 Calls API](https://dev.socrata.com/foundry/data.seattle.gov/grwu-wqtk)

## Where to Work

For this challenge, you will do you work in the `seattle911` directory. You will add code to the `js/app.js` file to enable the functionality described below.

## The Data

Before you start coding, open this link in a new browser tab to see what the data looks like:  
`[https://data.seattle.gov/resource/grwu-wqtk.json?$where=datetime is not null&$order=datetime desc&$limit=500]`

This URL returns the 500 most recent Seattle Fire 911 calls. The returned data is encoded as a JSON array of objects. As discussed in the tutorials, this format can be quickly parsed into JavaScript arrays and objects that you can then manipulate via your code.

Note that each array element is an object with the same set of properties. The ones we will need are:

* `latitude`: the latitude of the incident (may be missing)
* `longitude`: the longitude of the incident (may be missing)
* `type`: the type of incident (e.g., Aid Response, Fire Alarm, etc.)
* `address`: the address used to report the incident
* `datetime`: when the incident was reported

## Requirements

The code to create the interactive map is already provided for you, but you need to add code to the `js/app.js` file to accomplish the following:

1.  Fetch the URL stored in the `seattle911API` variable. Remember that this is done asynchronously, so it returns a Promise. You need to use the returned promise's `.then()` method to register a function you want called when the fetch is complete.
2.  When the fetch is complete, parse the response as `JSON`. Remember that this also happens asynchronously so you should return the promise that is returned from the `response.json()` method, and register another `.then()` function to receive the parsed data.
3.  When the parsing is complete, the data passed to your function will be the parsed array of objects. For each object in the array, create a [Leaflet marker](https://leafletjs.com/reference-1.3.0.html#marker) and add it to the map. If the object's `latitude` or `longitude` values are undefined, do not add a marker and just ignore that record.
4.  After creating the marker, use its `bindPopup()` method to bind some content that should be shown in a popup when the user clicks on the marker. Display at least the `type`, `datetime`, and `address` properties. To make the `datetime` property more human-friendly, use the [Moment.js library's `.fromNow()`](https://momentjs.com/docs/#/displaying/fromnow/) method.

## Commit, Sync, and Publish

When you've verified that your page is operating correctly, make sure you've committed all of your changes to your local repo and then synchronize with GitHub. You should then be able to see your published page at the following URL, replacing your-github-username with your GitHub user name:
https://imt-549-sp19.github.io/challenges-your-github-username/seattle911/

## Submit

After you've verified that your published page is working as expected, submit a link to your GitHub repo via this assignment.