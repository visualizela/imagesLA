[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.2600530.svg)](https://doi.org/10.5281/zenodo.2600530)

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

	- [Flâneur](#flneur)
		- [Config file](#config-file)
		- [Posts](#posts)
		- [Pages](#pages)
		- [Index](#index)
		- [Leaflet](#leaflet)
			- [Map Markers](#map-markers)

<!-- /TOC -->


## Flâneur

Flâneur is a Jekyll theme for maps and texts using Leaflet, and based on the earlier [Boulevardier](https://github.com/kirschbombe/boulevardier) framework.

View the theme live [here](http://dawnchildress.com/flaneur).

To use this theme, fork this repo to your GitHub account and follow the setup instructions below.

**Update:** Flâneur will soon have **Leaflet-IIIF** functionality to allow the use of IIIF-hosted images in place of map tiles, using pixel corrdinates instead of lat,lng. Thanks to Jack Reed ([mejackreed](https://github.com/mejackreed)) for getting this started with his Leaflet-IIIF library. You can view the in-progress version in the "flaneur-iiif" branch.

### Config file

**Site settings:** You will want to replace the settings here with the info about your new site.

**Styles:** You can change the site accent color and font here without editing the CSS. You will still need to replace the Google Font import URL in `head.html`.

**Map settings:** Import a map tileset from MapBox, OpenStreetMap, etc. and set the max/min zoom and center point. You also have the option to choose clustered or single map points. Options are `grouped` or `single`. The `directionsapi` is an optional field that requires the URL for a direction API. This has been tested with router.project-osrm.org and MapBox. It will work with any direction API that follow the standards that these two APIs follow.

**Menu:** There are two menu display options, `dropdown` (default) and `circle`.

**headerimage:** By default there is a header title on each page which is the site title. This can be replaced by an image. Put the url for the image in the config file and it will display the image instead of text.

### Posts
Create posts in the standard `YYYY-MM-DD-title.md` format required for Jekyll. The front matter for posts has several important liquid markup points:
* `lat:` & `lng:` add latitude and longitude to pin a post to a point on the map
* `categories:` ["category1", "category2"] - these populate the map layers widget and article index pages. This is an optional field. If you don't want to use this field the layers will populate with one map marker.
* `headertitle:` the running title appears at the top of pages and posts. The default is to display the site title.
* `desc:` This is the text for the map marker popup
* `order:` This allows you to order the stops for things like a guided tour. It is optional. It will add a number to the map marker. It will also add a previous/next button to the top of the post page. It will also create routes if there is a `directionsapi.`
* `mapmarker:` Allows you to set a specific map marker for the post (this needs to be the full URL for the map marker). By default map markers are chosen based upon the order in the `assets/leaflet/img` folder.
* `timelinedate:` An optional field to populate the timeline page. Most date formats work except Month/Day/Year, you will need to do Year/Month/Day. If you do not want to use this feature delete the `timeline.md` file.

Images have special formatting using Liquid attributes. The Liquid tags are also needed for the Lightbox feature:
```md
![Image title](images/filename.jpg -or- imageurl)
   {:.image}
Image attribution / caption.
   {:.caption}
```

Bibliographies also have special formatting using Liquid attributes:
```md
{:.bibliography}
1. Entry 1
2. Entry 2
```

### Pages
Create pages that will show up in the sidebar.

* **Menu items:** In order to have them show up in the menu add the `order` to the front matter with the correct order for the menu. This `order` field determines the order in the menu.

* **Menu titles:** If you do not want the title of the page to be the title in the menu add the `menutitle` into the page with the appropriate title.

* **Homepage:** By default the homepage is the permalink /home. If you want to change that add `type: home` to the front matter of the page you want to be the homepage;

* **Search:** Add `type: search` to any page and that will make the page the search page. In this example it is the `search.html` file.

* **Article Index:** To add an item into the sort fields create a new file in the `_article_index` folder. Add the following fields to the front-matter: `layout: article-index` and `status: `. The status field should the be post field you want to sort by.

### Index
Documentation on the current indexing feature coming soon...

### Leaflet

#### Map Markers

By default map markers are stored in the `/assets/leaflet/img/` folder. To change map markers add images to that folder. The application will grab map markers in alphabetically order so you can number them if you have a specific order you want them to be used in.

If you want a specific map marker to be used for a specific category this is easily done. Simply rename the map marker to the category in lowercase with spaces replaced with underscores. For example, `Arts and Culture` would become `arts_and_culture.svg`.
