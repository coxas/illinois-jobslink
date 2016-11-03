
# Fusion Table Searchable Map Template
You want to put your data on a searchable, filterable map. This is a free, open source template to help you do it.

[![Searchable Map Template screenshot](https://raw.github.com/derekeder/FusionTable-Map-Template/master/images/searchable-map-template-v1.2.jpg)](http://derekeder.github.io/FusionTable-Map-Template/)

[See the working demo &raquo;](http://derekeder.github.io/FusionTable-Map-Template/)

## Features

* full screen, iframe and content templates
* display up to 100,000 map points
* address search (with variable radius and geocomplete)
* geolocation (find me!)
* results count
* RESTful URLs for sharing searches
* ability to easily add additional search filters (checkboxes, sliders, etc)
* mobile and tablet friendly using responsive design
* built with HTML, CSS and Javascript - no server side code required


## Releases

* [v 1.4](https://github.com/derekeder/FusionTable-Map-Template/releases/tag/v1.4) - iframe template, MapsLib class
* [v 1.3](https://github.com/derekeder/FusionTable-Map-Template/releases/tag/v1.3) - Bootstrap 3.2, more robust query function, dynamic zoom
* [v 1.2](https://github.com/derekeder/FusionTable-Map-Template/releases/tag/v1.2) - Bootstrap 3, jQuery 1.10.2, jQuery Address 1.6
* [v 1.1](https://github.com/derekeder/FusionTable-Map-Template/releases/tag/v1.1) - Bootstrap 2.0.3, jQuery 1.7.1, jQuery Address 1.4 
  
## Dependencies

* [Google Fusion Tables](http://www.google.com/fusiontables/Home)
* [Google Maps API V3](https://developers.google.com/maps/documentation/javascript)
* [jQuery](http://jquery.org)
* [jQuery Address](https://github.com/asual/jquery-address)
* [Bootstrap 3.2.0](http://getbootstrap.com/)

## Community
There's a [public Google Group](https://groups.google.com/forum/#!forum/fusion-table-map-template) for anyone who wants to or has used the Searchable Map Template. Join the growing community of map makers to learn, share and benefit from each other!

[Join the Fusion Table Map Template Google Group &raquo;](https://groups.google.com/forum/#!forum/fusion-table-map-template)

## Setup

Follow the steps below and you'll be in business with your own map.

1. Create a Fusion Table ([here's a great tutorial](https://support.google.com/fusiontables/answer/2527132?hl=en&topic=2573107&ctx=topic))
1. Make sure at least one column is set to a type of Location and that Fusion Tables has geocoded it
1. Set the Fusion Table to be publicly visible (via the Share button in the upper right) and make sure 'Allow Download' is enabled.
1. Create your own Google Maps JavaScript API key to replace the default in the Map Options section of the index.html file above. By inserting your own key, Google will allow 25,000 requests per day to your Searchable Map.
  1. Go to the [Google Developers Maps JavaScript API](https://console.developers.google.com/projectselector/apis/credentials) page and click the Get a Key button
  1. On the Google Developers Console page, select Create a New Project and press Continue
  1. On the Credentials page, create a key, which should look something like `AIzaSyBNVkiNzErPTEGpxWp0cvdqDMd2BxD-S50`.
  1. Copy and paste your key into the Map Options section of the index.html file as described above.
  1. To find or edit your key in the future, go back to the Google Developers Console page
1. Download or clone this project and fire up your text editor of choice. Open up `index.html` and set your map options at the bottom of the file ([see the full list of options](#mapslib-options))
   1. **fusionTableId** - the ID of your Fusion Table (found in Fusion Tables under File => About this table)
   1. **googleApiKey** - the API key from your [Google API Console](https://code.google.com/apis/console/)
   1. **locationColumn** - the name of your location column in your Fusion Table
   1. **map_center** - the lat/long you want your map to center on ([find yours here](http://www.itouchmap.com/latlong.html))
   1. **locationScope** - the area you want to limit searches to (set to 'chicago' by default)
1. **New** Get a Google Maps API key. [Follow these instructions](https://developers.google.com/maps/documentation/javascript/get-api-key) and replace the key on this line of `index.html`: `<script type="text/javascript" src="https://maps.google.com/maps/api/js?sensor=false&libraries=places&key=[YOUR KEY HERE]"></script>`
1. Add/modify additional filters to maps_lib.js. This will depend on the data you are trying to map. Take a look at the [wiki](https://github.com/derekeder/FusionTable-Map-Template/wiki) for [filter examples](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples) and [list views](https://github.com/derekeder/FusionTable-Map-Template/wiki/List-search-results) to get started.
1. Upload this map and all the supporting files (css, fonts, images and js folders) to your site 

## MapsLib options

You can configure your map by passing in a dictionary of options when you create a new `MapsLib` instance in `index.html` or `index_iframe.html`. Here's an example:

```javascript
var myMap = new MapsLib({
  fusionTableId:      "1m4Ez9xyTGfY2CU6O-UgEcPzlS0rnzLU93e4Faa0",
  googleApiKey:       "AIzaSyA3FQFrNr5W2OEVmuENqhb2MBB2JabdaOY",
  locationColumn:     "geometry",
  map_center:         [41.8781136, -87.66677856445312],
  locationScope:      "chicago"
});
```

| Option           | Default value           | Notes                                                                                                                                                         |
|------------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| fusionTableId    |                         | **Required**. Table ID of your Fusion Table (found under File => About).                                                                                      |
| googleApiKey     |                         | **Required**. Found at https://console.developers.google.com/ The key provided in this template is for demonstration purposes only. Please register your own. |
| map_centroid     |                         | **Required**. Center [latitude, longitude] that your map defaults to.                                                                                         |
| recordName       | record                  | Used for showing the count of results.                                                                                                                        |
| recordNamePlural | records                 |                                                                                                                                                               |
| searchRadius     | 805                     | Default search radius. Defined in meters. Default is 1/2 mile.                                                                                                |
| locationColumn   | geometry                | Name of the location column in your Fusion Table. If your location column name has spaces in it, surround it with single quotes like this "'my location'".    |
| locationScope    |                  | Appended to all address searches to keep results within a geographic area.                                                                                    |
| defaultZoom      | 11                      | Default zoom level when map is loaded (bigger is more zoomed in).                                                                                             |
| addrMarkerImage  | images/blue-pushpin.png | Image used to identify your address search on the map. Setting it to blank (`""`) will hide the marker.                                                              |


## Custom Filters and Views

Take a look at the [wiki](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples) to see how to add your own custom filters and views like:

* [Checkboxes](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-checkboxes)
* [Radio buttons](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-radiobuttons)
* [Drop down lists](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#drop-down-lists)
* [Text searches](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-textsearches)
* [Results lists](https://github.com/derekeder/FusionTable-Map-Template/wiki/List-search-results)
* [Text searches](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-textsearches)
* [Sliders](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-sliders)
* [Date sliders](https://github.com/derekeder/FusionTable-Map-Template/wiki/Filter-examples#wiki-date-sliders)

## iframe Template

If you want to embed the template in a page on your website, the easiest way to do it is with an iframe. We provide an iframe-optimized template for this purpose:

[![Searchable Map Template iframe screenshot](https://raw.github.com/derekeder/FusionTable-Map-Template/master/images/searchable-map-template-iframe.png)](http://derekeder.github.io/FusionTable-Map-Template/iframe_test.html)

[See the working demo &raquo;](http://derekeder.github.io/FusionTable-Map-Template/iframe_test.html)

This template works exactly the same way as the standard full screen template. All the javascript code is still contained in `js/maps_lib.js`.

To embed, you can use the following code on your page:

```html
<iframe 
  style="border-style: none;" 
  src="/path/to/map-template/index_iframe.html" 
  width="600" 
  height="950" >
</iframe>
```

You must explicitly set the size of the iframe, so midify the `height` and `width` attributes as necessary. You can also control the height of the map in `css/custom.css`:

```css
.iframe #map_canvas { height: 500px; }
```

## FusionTable-Map-2-layers

If you want to create a map with two layers - one with points and another with polygons, take a look at Jack Dougherty's [FusionTable-Map-2-layers](https://github.com/JackDougherty/FusionTable-Map-2-layers), based on this template. It's a great place to start.

## Resources

Fusion Tables 

* [Fusion Tables Home](http://www.google.com/fusiontables/Home)
* [v1 API Documentation](https://developers.google.com/fusiontables/docs/v1/using)
* [v1 API Migration Guide](https://developers.google.com/fusiontables/docs/v1/migration_guide)

Community

* [Fusion Table Map Template Google Group](https://groups.google.com/forum/#!forum/fusion-table-map-template)
* [Fusion Tables Issue Tracker](http://code.google.com/p/fusion-tables/issues/list)
* [Fusion Tables Google Group](http://groups.google.com/group/fusion-tables-users-group)

Reference Guides

* [Google Maps API](http://code.google.com/apis/maps/documentation/javascript/overlays.html#FusionTables)
* [Fusion Tables API Developer Guide](http://code.google.com/apis/fusiontables/docs/developers_guide.html)
* [Fusion Tables API Reference Guide](http://code.google.com/apis/fusiontables/docs/developers_reference.html)

## Common issues/troubleshooting

If your map isn't displaying any data, try the following:

1. Use the [Chrome developer console](https://developers.google.com/chrome-developer-tools/docs/console) or install [Firebug](http://getfirebug.com/) for FireFox. This will allow you to debug your javascript.
1. Load your map in the browser and open the javascript console 
   * Chrome developer console on a Mac: Option+Command+J
   * Chrome developer console on a PC: Control+Shift+J
   * Firebug in Firefox: Tools => Web Developer => Firebug => Open Firebug) 
1. If you aren't seeing any javascript errors:
   * Make sure that you have at least one column with address or lat/long points set to type 'Location'. You can check this in Fusion Tables under Edit => Modify Columns.
   * Make sure that Fusion Tables has geocoded your column. You check this by going to View => Map. If you see your points on the map, you're good!
   * Check that your Fusion Table is public (in Fusion Tables, upper right corner => Share button)
1. If you do see javascript errors:
   * The error will tell you what line it is failing on. Best to start by going there!
   * Columns in Fusion Tables are case sensitive, so make sure they are correct.
   * For columns that have multiple words in the title, make sure to surround the column name in your code with single quotes (example: "'first name'") 

#### My custom map styles won't display! 

This is due to a recent change to the FusionTablesLayer and only effects tables created after mid-November 2012. A __styleId__ and __templateId__ must be defined.

When you create custom styles for the first time, the styleId will be 2. For custom info window layouts, the first templateId will also be 2. The __latest version of this template has these defaults set__, but in case you want to add it to an existing project, use the following code:

```javascript
   MapsLib.searchrecords = new google.maps.FusionTablesLayer({
     query: {
       from:   MapsLib.fusionTableId,
       select: MapsLib.locationColumn,
       where:  whereClause
     },
     styleId: 2,
     templateId: 2
   });
```

For reference, styleId 1 is the default look - usually small red dots or red polygons. templateId 1 is the default info window that just shows the first few columns in your table.

For more information, see [Working with styles](https://developers.google.com/fusiontables/docs/v1/using#WorkingStyles) and [Working with templates](https://developers.google.com/fusiontables/docs/v1/using#WorkingInfoWindows) in the Fusion Tables documentation.

#### I want to display custom icons on my map

By default, Fusion Tables only provides 10 (5 large and 5 small) marker icons. 

<img src="http://storage.googleapis.com/support-kms-prod/SNP_2752125_en_v0" alt="small red map dot" title="small red map dot" width="9" height="9">&nbsp;<img src="http://storage.googleapis.com/support-kms-prod/SNP_2752063_en_v0" alt="small yellow map dot" title="small yellow map dot" width="9" height="9">&nbsp;<img src="http://storage.googleapis.com/support-kms-prod/SNP_2752129_en_v0" alt="small green map dot" title="small green map dot" width="9" height="9">&nbsp;<img src="http://storage.googleapis.com/support-kms-prod/SNP_2752068_en_v0" alt="small blue map dot" title="small blue map dot" width="9" height="9">&nbsp;<img src="http://storage.googleapis.com/support-kms-prod/SNP_2752264_en_v0" alt="small purple map dot" title="small purple map dot" width="9" height="9">&nbsp;<img alt="large_red" src="http://chart.googleapis.com/chart?chst=d_map_pin_letter&amp;chld=|FF0000">&nbsp;<img alt="large_yellow" src="http://chart.googleapis.com/chart?chst=d_map_pin_letter&amp;chld=|FFFF00">&nbsp;<img alt="large_green" src="http://chart.googleapis.com/chart?chst=d_map_pin_letter&amp;chld=|00FF00">&nbsp;<img alt="large_blue" src="http://chart.googleapis.com/chart?chst=d_map_pin_letter&amp;chld=|6699FF">&nbsp;<img alt="large_purple" src="http://chart.googleapis.com/chart?chst=d_map_pin_letter&amp;chld=|9933FF">

From my understanding, this is for performance reasons (the map and icon tiles are cached). However, there are two ways to work around it:

1. Use some of the 200 additional icons provided by Google. [This page](http://support.google.com/fusiontables/answer/2679986?hl=en) gives a good tutorial.
1. Use the Fusion Tables API to fetch your data and then draw your own markers using the Google Maps v3 API. Take a look at [this example](https://code.google.com/p/gmaps-samples/source/browse/trunk/fusiontables/custom_markers.html?spec=svn2515&r=2515) (warning: more advanced programming ahead!)

#### My map works, but the results count returns 0

The results counter uses the Fusion Tables API, which requires an API key and some specific sharing permissions. Try the following in this order:

1. Make sure you set fusionTableId to a valid API key. It should look something like `1m4Ez9xyTGfY2CU6O-UgEcPzlS0rnzLU93e4Faa0`. To get a new one, go to the [Google API Console](https://code.google.com/apis/console/)
1. Make sure that 'Allow Downloads' is checked for your Fusion Table (File => About this table => Edit table information)

#### Still can't figure it out or more detail needed?
Ask for help on our [Fusion Table Map Template Google Group](https://groups.google.com/forum/#!forum/fusion-table-map-template)!

## Bug fixes and pull requests

Notice a bug or want to add a feature? [Open an issue](https://github.com/derekeder/FusionTable-Map-Template/issues) or submit a pull request like so:
 
1. Fork the project.
1. Make your feature addition or bug fix.
1. Commit and send me a pull request.

## Contributors 

* [Derek Eder](http://derekeder.com) - primary contributor
* [Chris Keller](http://www.chrislkeller.com/) - [recenter map on resize](https://github.com/derekeder/FusionTable-Map-Template/pull/11)
* [nb-ofs](https://github.com/nb-ofs) - [Windows 8 touch screen ability](https://github.com/derekeder/FusionTable-Map-Template/pull/14), [Google Maps Visual Refresh](https://github.com/derekeder/FusionTable-Map-Template/pull/18), [Noscript message](https://github.com/derekeder/FusionTable-Map-Template/pull/19)
* [Felipe Figueroa](https://github.com/amenadiel) - [Geocomplete update](https://github.com/derekeder/FusionTable-Map-Template/pull/36), [Updates to query function](https://github.com/derekeder/FusionTable-Map-Template/pull/38), [maps_lib.js javascript class](https://github.com/derekeder/FusionTable-Map-Template/pull/45)

## Copyright and attribution

Copyright (c) 2015 Derek Eder. Released under the MIT License.

If you use this template, please provide the following attribution in the footer: 

```html
<a href='http://derekeder.com/searchable_map_template/'>Searchable Map Template</a> 
by <a href='http://derekeder.com'>Derek Eder</a>.
```

See [LICENSE](https://github.com/derekeder/FusionTable-Map-Template/blob/master/LICENSE) for more details.
=======
# Illinois JobsLink Project
Build Illinois Jobslink scraper, API, and front end. 


## Overview
+ Scrape the relevant information from [https://illinoisjoblink.illinois.gov/ada/r/search/jobs](https://illinoisjoblink.illinois.gov/ada/r/search/jobs). We will be using [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) and [Requests](http://docs.python-requests.org/en/master/).
  * Scrape `How To Apply`, `Education Level`, `Salary/Wages`, `Location`
  *  Python dictionaries, conditional and loop structures, HTTP methods, JSON.
  * Iron out authentication and login problems on Illinois Jobslink site.

+ Store in Google Fusion Tables and sqlite database
  * SQL queries helpful
  * Will need to solve OAuth2 troubles

+ [Derek Eder's Searcheable Map Template](http://derekeder.github.io/FusionTable-Map-Template/) will be used as the front end. 
  * Used before in Network9 Project for CPS
  * Bootstrap, JS stuff. 

+ Update Script that runs periodically (daily or weekly) and updates Google Fusion Tables and sqlite database. 
  * Will live on Heroku

## Teamwork

We will be using Git and GitHub for this project. To get started, fork the repository to your own account. Once forked, go to your repository and clone it to your local machine.
```
git clone /FORKED/REPO/URL
```

Make sure you make a new branch when you are implementing a new feature. Be sure to be working in the right branch when coding.

You will also need to make sure you set your upstream repository correctly. To do that do the following:

```
git remote add upstream https://github.com/uchicagotechteam/illinois-jobslink.git
```

Then you will need to create and pull the branches themselves, as follows:

```
git checkout -b init_scrape
git checkout init_scrape
git pull upstream init_scrape

git checkout -b api
git checkout api
git pull upstream api
```

You'll be ready to code now! Make sure you are in the right branch by using `git checkout <BRANCH_NAME>`. 

Once you code, make sure you add your files and commit them. Push them to your forked repository when ready.

```
git add FILENAMES (or use -a {be careful!})
git commit -m "Insert commit message."
git push origin <BRANCH_NAME>
```
Once you're done with your branch, be sure to send a pull request so I can merge your code with the existing project.

## Set Up
We will be using `pip` and `virtualenv` in this project. Make sure you have `pip` installed. If you downloaded Python via Anaconda, you are good to go. I'm not sure about other distributions.

To install `virtualenv`
```
pip install virtualenv
```

Once you've done this, `cd` into your project repo. Then run the following commands if you are on Windows.
```
virtualenv env
env/scripts/activate
pip install -r requirements.txt
```

If you're on MacOS, you'll run something like the following:
```
virtualenv env
env/bin/activate
pip install -r requirements.txt
```

This will create a virtual environment so that any development you do will not be affected by the global system variables. Also, you will download all of the packages from `requirements.txt`, so that the code will actually run. If you install any new packages for code you have written, make sure to put them into `requirements.txt`. 

## Team: `Srape`
The `init_scrape` branch is the branch dedicated for the initial scrape. Our objectives/tasks for this branch are:

+ Login to `https://illinoisjoblink.illinois.gov/ada/r/search/jobs`
  
  So I made an account for this website as you can only get all of the information for each job posting by making an account. However, I have NOT yet figured out how to actually login with Python. There are some workarounds that we can try. This is kind of an advanced feature, and if you have a lot of experience, I'll be in touch.
   
+ Request `https://illinoisjoblink.illinois.gov/ada/r/search/jobs` (This is the FIRST page) and scrape it. 

  Like we did on `12 OCT 2016`, we are going to have to scrape the list of job postings on this page. If you inspect the page source and scroll down a TON to the job postings, you'll see HTML that looks like the following for ONE job posting:

  ```
  <dt>
    <a href="/ada/r/jobs/4324478">Insurance Sales Agent (4324478)</a>
    <div class="updated right">Last Updated: 2016-10-12</div>
    <!-- search score: 1.0 -->
  </dt>
  <dd>
    <div class="row">
        <div class="col_1">
            <b>Employer: </b>
            Combined Insurance
        </div>
        <div class="col_2">
            <b>Location: </b>
            <i>Belleville , IL</i>
        </div>
    </div>
    <div class="description"><p>Management Trainees needed for the Metro East Area. For those competitive individuals with a desire to achieve, come join a winning team. Offering insurance products including Disability, Accident &amp; Sickness, Whole Life, &amp; Medicare Supplement, Combined Insurance, established in 1922, is expanding its Management Trainee program. Opportunities available in two…</p></div>
  </dd>
  ```

  Notice how for each job posting we have a `<dt>` and `<dd>` tag that is associated with the job. The `<dt>` tag points to the name of the job name as well as the url of the webpage of that job. The `<dd>` tag has descriptions and stuff.

+ Step through the url for each job posting and scrape the job page
  
  So we're going to have to get the urls, which are located in the `<a>` tag under the `<dt>` tag. If you look in `init_scrape.py` you'll see the following code (as of 12 OCT 2016, 8:30 PM):

  ```
  # Print the urls for each job listing.
    # Will need to implement stepping through these urls and scraping the
    # relevant data.
    listings = soup.find_all("dt")  # Finds all dt tags (elements in the list)
    for l in listings:
        # Finds the a tag, which will have the name and the url
        urls = l.find_all('a')
        for u in urls:
            job_url = u['href']  # The href part of the tag will have the url
            name = u.string  # The name will be in the string part of the a tag
            id_num = u.string[u.string.find('(') + 1:u.string.find(')')]
  ```

  So we've gotten the url for each job posting, and we need to step through the url and scrape that page. We can request the url as follows and set up a `BeautifulSoup` object for that page.

  ```
  r = requests.get("INSERT_JOB_URL_HERE")
  job_soup = BeautifulSoup(r.content, "html.parser")
  ```
  We're going to step through the url because that page has more information than just the homepage of the website. 

  We're going to scrape information like `description`, `location`, `wages`, etc.

+ Insert the scraped data into sqlite and Google Fusion Tables.

  I'll go over this in a session. We'll be going over SQL statements and sqlite. Don't worry about this right now. 

  Fusion Tables is going to be difficult, but we'll figure it out.


+ Step through the ALL the pages of the search results. 
  
  If you look at the bottom of `https://illinoisjoblink.illinois.gov/ada/r/search/jobs`, you'll see there are a LOT of result pages. We're going to have to step through each of these, scrape for all of the job urls, and THEN step through all of those job urls. 

  But, wait, how are we going to go to next page? Python doesn't have a mouse to click `Next Page`, so what are we to do??


  `https://illinoisjoblink.illinois.gov/ada/r/search/jobs?is_subsequent_search=false&page=2&refiners=%7B%7D&status=Active`

  This is the url for the second webpage. Notice the very subtle `page=2` in the url. So what we can do is iterate through by changing the number from `page=2` to `page=3` to get the third page. If we want the `ith` page, we would do `'page=' + str(i)`.

## Team: `Backend`

+ Write to Google Fusion Tables (OAuth)
  
  To use the searcheable map template developed by Derek Eder, we need to store all of our data on Google Fusion Tables. So we will need to write our data from our SQL database to a Google Fusion Table. We can do this through the Google API found: [https://developers.google.com/fusiontables/docs/v1/using](https://developers.google.com/fusiontables/docs/v1/using). 

  There are difficulties with OAuth which is a very confusing paradigm that Google uses for security. But once we have the data in the Google Fusion Table, mapping the data will be very easy. 

+ Endpoints
  
  Our data is stored in a `sqlite` database, which will be served via an API built on Flask. If we look in the `api` branch, there is `api.py` file that has all of the Flask code (well really basic stuff) in it. We can instantiate it as follows. (Make sure you have all of the correct packages installed i.e. `pip install requsts`, `pip install flask`, and other packages).
  ```
  (env) PS D:\Projects\TechTeam\illinois-jobslink> python api.py
 * Restarting with stat
 * Debugger is active!
 * Debugger pin code: 115-448-509
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
  ```

  This indicates that our server is running. We can then go to our favorite browser and type into the browser bar `http://127.0.0.1:5000/`. 

  You should get an error at this point, because in `api.py` we haven't written what should be done when the `/` endpoint is called. BUT we do have `/jobs` endpoint defined. So we can type in `http://127.0.0.1:5000/jobs` and we should see something pop up! It should look something like this 

  ```
  {
    "jobs": ""
  }
  ```

  So far this is empty since we haven't actually returned any of the job listings, but it should eventually come back with a list of all the jobs that fit our parameters.

  Jobs can be filtered via the url and a query string. If we type in 
  ```
  http://127.0.0.1:5000/jobs?name=ferret
  ```
  we can filter all of the jobs with the name `ferret`. This won't actually work since we haven't written the code to actually do it. We can chain together parameters with the `&` character as follows

  ```
  http://127.0.0.1:5000/jobs?name=ferret&id=007
  ```

  So we will be using this paradigm. A user can filter what jobs they want by using this query string, and its our job to only grab the jobs in the database that fit the parameters. Some more info about [query strings](https://en.wikipedia.org/wiki/Query_string).

  We will be servicing the requests through SQL statements, and you can find model code in `api.py` that does this. 

  Another thing to think about is whether we want to add more endpoints or functionality so that users can ask for data in different and more complex ways. 

+ Update
  
  We are going to have to solve how to update our database with new jobs and removing old jobs. We will be doing this with SQL statements again and probably periodically (daily or weekly?). [SQL](http://www.w3schools.com/sql/) commands and syntax.

## Team: Frontend

+ Searchable Map Template
  
  We will be using [Derek Eder's Searcheable Map Template](http://derekeder.github.io/FusionTable-Map-Template/) for our mapping purposes. He has GREAT documentation so check his page out. 

  We really have free range on how we want to design the map, so you guys have a lot of creative freedom.

+ Analytics
  
  I think it might be cool to do some of our own analytics on this data. We can use R as well as Python with `matplotlib` and `pandas`.

  You should start to think about what trends, relationships we want to look at and how we can describe these graphically.

+ D3

  [D3](https://d3js.org/) is a REALLY cool visualization library written in JavaScript. I don't have much experience at all but I think we can make some cool looking graphics. This team will work with the Analytics team closely.

