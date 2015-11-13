# Fingal Garda Stations API


##Data-Representation and Querying Project


**Jason Thorne**
**G00317349**


##Overview##

This project outlines the design and documentation for the use of datasets regarding Garda Stations in Fingal.
These datasets are found at data.gov.ie, at the following [link] (https://data.gov.ie/dataset/garda-stations).
This API is designed to help app developers provide Fingal residents with information on where and how to contact their local garda Station in the event of an emergency. This data can be also be useful in other cases however. Such as by touring event organisers, wishing to contact stations local to their destinations.


##Dataset Description##

The data is recieved inComma Separated Values (CSV) format, from the following [link] (https://data.gov.ie/dataset/garda-stations).
The CSV file contains 19 rows. The first being the header row with the names of each field.
There are 15 columns of fields. These are as follows: 


Field Name | Description 
-----------|------------
Name|The name of the Station
Address1|First address field for the Station
Address2|Second address field for the Station
Address3|Third address field for the Station
Phone|The Station's Phone Number
Website|The Station's Website
Division|Station's Division
Divisional_HQ|The Division's HQ
Divisional_HQ_Phone|Division HQ's Phone Number
District|The District te Station is under
District_HQ|Location of the Dictrct HQ
District_HQ_Phone|The Dictrct HQ's Phone Number
Opening_Hours|The Station opening hours
LAT|Station Latitude co-ordinates
LONG|Station Longitude co-ordinates


**Example of Data in CSV format:**


Name|Address1|Address2|Address3|Phone|Website|Division|Divisional_HQ|Divisional_HQ_Phone|District|District_HQ|District_HQ_Phone|Opening_Hours|LAT|LONG
-----------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------
Balbriggan Garda Station|Drogheda Road|Balbriggan|Co. Dublin|+353 1 8020510|http://www.garda.ie/Stations/Default.aspx|Dublin Metropolitan Region Northern Division|Ballymun|+353 1 6664493|Balbriggan|Balbriggan|+353 1 8020510|Open 24hrs |53.61437815|-6.191052919



##Using the Dataset##


This API will return information in JSON format. This is done through using HTTP Request methods, and the required URL, as outlined in the examples below. 


###Querying by Name###


To retrieve information on a station by it's name, use the GET method at the following URL:

```
http://www.fingalgarda.ie/stations/name/[name]
```

Where '[name]' is replaced by the name you wish to search. For example, if you wanted to find Swords Garda station, you would type the following: 

```
http://www.fingalgarda.ie/stations/name/[Swords Garda Station]
```

This would return the following information in JSON format:

```
 {
    "Name":"Swords Garda Station",
    "Address1":"Main Street",
    "Address2":"Swords",
    "Address3":"Co. Dublin",
    "Phone":"+353 1 6664700",
    "Website":"http://www.garda.ie/Stations/Default.aspx",
    "Division":"Dublin Metropolitan Region Northern Division",
    "Divisional_HQ":"Ballymun",
    "Divisional_HQ_Phone":"+353 1 6664493",
    "District":"Coolock",
    "District_HQ":"Coolock",
    "District_HQ_Phone":"+353 1 6664282",
    "Opening_Hours":"Open 24hrs ",
    "LAT":53.4560671353432,
    "LONG":-6.22116473435358
  },
  
```


###Querying by County###

To search for all Stations within a particular County, use the following URL, where '[name]' is replaced by the name of the county:

```
http://www.fingalgarda.ie/stations/county/[name]
```

To find Stations within Co. Dublin for example, type the following: 

```
http://www.fingalgarda.ie/stations/county/[Co. Dublin]
```

A list of all Stations within this County will be returned. An example from this is as follows:

```
[
  {
    "Name":"Balbriggan Garda Station",
    "Address1":"Drogheda Road",
    "Address2":"Balbriggan",
    "Address3":"Co. Dublin",
    "Phone":"+353 1 8020510",
    "Website":"http://www.garda.ie/Stations/Default.aspx",
    "Division":"Dublin Metropolitan Region Northern Division",
    "Divisional_HQ":"Ballymun",
    "Divisional_HQ_Phone":"+353 1 6664493",
    "District":"Balbriggan",
    "District_HQ":"Balbriggan",
    "District_HQ_Phone":"+353 1 8020510",
    "Opening_Hours":"Open 24hrs ",
    "LAT":53.6143781459678,
    "LONG":-6.19105291877873
  },
]
```

###Querying by Division###

Stations may also be searched for through their Division. Replacing '[name]' with the name of the Division.

```
http://www.fingalgarda.ie/stations/division/[name]
```

An example of this URL:

```
http://www.fingalgarda.ie/stations/division/[Kildare Division]
```
 
The results of this query:

```
 {
    "Name":"Leixlip Garda Station",
    "Address1":"Leixlip",
    "Address2":"Co. Kildare",
    "Address3":"",
    "Phone":"+353 1 6667800",
    "Website":"http://www.garda.ie/Stations/Default.aspx",
    "Division":"Kildare Division",
    "Divisional_HQ":"Naas",
    "Divisional_HQ_Phone":"+353 45 884311",
    "District":"Leixlip",
    "District_HQ":"Leixlip",
    "District_HQ_Phone":"+353 1 6667800",
    "Opening_Hours":"Open 24hrs",
    "LAT":53.3674665276442,
    "LONG":-6.49833624071316
  },
  
```




###Posting a new record###

To post a record of a new Station, use the following URL, replacing '[name]' with the name of the station:

```
http://fingalgarda.ie/stations/new/[name]
```

The post request should look like as below, replacing '[value]' with the required data for that field, and '[name]' with name of station.

```
POST /stations/new/[name].html HTTP/1.1
Host: www.fingalgarda.ie
Name=[value]&Address1[value]&Address2=[value]&Address3=[value]&Phone=[value]&Website=[value]&Division=[value]&Divisional_HQ=[value]&Divisional_HQ_Phone=[value]&District=[value]&District_HQ=[value]&District_HQ_Phone=[value]&Opening_Hours=[value]&LAT=[value]&LONG=[value]
```
