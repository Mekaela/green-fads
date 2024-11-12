# exercise 8

|Platform| URL| Path to API information| Documentation URL| API URL| Data Format|
|--------|----|------------------------|------------------|--------|------------|
|GBIF | [GBIF](https://www.gbif.org/)  | [info](https://techdocs.gbif.org/en/) | [docs](https://techdocs.gbif.org/en/openapi/) | [url](https://api.gbif.org/v1) | JSON |
|Eurostat | [Eurostat](https://ec.europa.eu/eurostat/)  | [info](https://ec.europa.eu/eurostat/web/user-guides/data-browser/api-data-access)  | [docs](https://ec.europa.eu/eurostat/web/user-guides/data-browser/api-data-access/api-getting-started#Catalogue)  | [url](https://ec.europa.eu/eurostat/api/dissemination/files) | XML | 
|INE | [INE](https://www.ine.pt/) | [info](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ics_feeds&ine_smenu.boui=357197120&ine_smenu.selected=357197349&ine_smenu.boui=357197120&ine_smenu.selected=357197349)  | [docs](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_api&INST=322751522&ine_smenu.boui=357197120&ine_smenu.selected=357197822&ine_smenu.boui=357197120&ine_smenu.selected=357197822)  | [url](https://www.ine.pt/ine) | JSON |
|Climate Data Store | [CDS](https://cds.climate.copernicus.eu/cdsapp#!/home) | [info](https://cds.climate.copernicus.eu/how-to-api)  | [docs](https://cds.climate.copernicus.eu/how-to-api)  | [url](https://cds.climate.copernicus.eu/api) | JSON? |
|Copernicus Open Access Hub | [COAH](https://scihub.copernicus.eu/)  | [info](https://documentation.dataspace.copernicus.eu/APIs.html)  | [docs](https://documentation.dataspace.copernicus.eu/APIs/SentinelHub/ApiReference.html) | [url](http://www.opengis.net/def/crs/) | XML |
|WMO | [WMO](https://worldweather.wmo.int/en/home.html)  | [info](https://space.oscar.wmo.int/apidoc/)  | [docs](https://space.oscar.wmo.int/apidoc/)  | [url](https://space.oscar.wmo.int//api/v1/) | JSON | 
|Agri4Cast | [Agri4Cast](https://agri4cast.jrc.ec.europa.eu/DataPortal/)  | [info](https://agri4cast.jrc.ec.europa.eu/DataPortal/) | N/A  | N/A - download from website, not API | XLSX/PDF |
|European Environment Agency | [EEA](https://www.eea.europa.eu/)  | [info](https://www.eea.europa.eu/code)  | [docs](https://www.eea.europa.eu/code/api/)  | [various - e.g.](https://www.eea.europa.eu/code/api/indicators/daviz.json) | Various |



### How can I detect that a web site has hidden data?
Use inspect in Developer tools to see any links not visible on the page. 

### When should I decide to do steps in web scraping manually versus doing everything automatically?
Web scraping manually takes a lot of time, so should only be used for small projects. It can be useful when websites are changing often, and so the parameters are constantly changing, or when a site only needs to be scraped once. It also helps while learning to understand the techniques while only having to look at one page. Automated is good for large projects, and where the scraping has to be performed often. Often they will both be used - manual when setting up scraping to get a sense of pages, and then automated once the formatting and available data is known. 

### What advantages and problems do I have doing web scraping?
Some websites don't allow it. It is useful where an API isn't available, or where it is important to know which data is on a specific website page. It can also be useful if the API is not open, though such websites likely try to prevent scraping as well. 

### What are the differences in getting data by between web scraping compared to an API? Which approach do I prefer and why?
APIs are more reliable, as content on a site can change, and APIs are only related to the data, and not what is happening on the website (i.e. data, backend and frontend). I prefer API's, for the reason above, and because they are generally simpler to work with once the structure of the data is known. 


## Visit SASSCAL WeatherNET. Explore the details in data for one particular station of your choice.

### Make a plan to scrap the information from this site:
1. Decide which parameters to use
2. Inspect the HTML: identify the HTML elements containing the parameters desired
3. Determine the scraping method: Beautiful Soup, as I have used that in the tutorial. It doesn't appear there is dynamic Javascript on these pages, so Beautiful Soup should be sufficient.
4. Examine the URL parameters. This can be used to scrape other pages of this site without having to navigate to each one. For example 'weatherstat_daily_we.', can be changed to 'weatherstat_hourly_we' to find hourly pages instead of daily pages. 
5. Plan how to extract each desired data point from its corresponding HTML element.
7. Choose a storage method and save to the chosen format. 
8. Design a script based off of the above, including mplementing error handling: in case something goes wrong, so it's easier to either retry, and/or see what went wrong.Run the script. 
9. Verify the returned data is the same as what is seen on sasscalweathernet.org

### Can I do it (legally)? Why?
Adding /robots.txt to the url does not cause any errors. However in the Declaration on the use of data, it says 'Free use of the data is granted for non-commercial and educational purposes. Commercial use can be granted based on request to SASSCAL'. My assumption from that, is that scraping is legal as long as it is for non-commercial or educational purposes. 

### Which items of information (IDs, parameters, etc) are available to use in web scraping?
For Chadiza weather station, there is Hourly, Daily and Monthly weather data. Each record contains: Date, Hour, Air Temp., Soil Temp., Rain, Wind Speed, Wind Direct., Wind Speed (max), Humidity, Barom. Press., Solar Radiation, Solar Radiation Energy, and Battery Voltage. There is also an information sheet with Station Information, and information on the sensors used for the different parameters, as well as a photo of the weather station. 