---
title       : Interactive Data Visualization - An Example
subtitle    : Life Expectancy across Globe
author      : Perumal Kumar     
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---    

## Challenge     



The biggest chalenge a person creating a report faces is to make it fit the end user requirements. Often the end user gives unclear requirements and ends up giving more requirements when a report is created, sometimes requiring a minor modification to the parameters or requiring more from the data.     
                


Would it not be wonderful to have a solution that is interactive and looks appealing!  


          
"Life Expectancy Across the Globe" app is a great example of a way to do this.             
                   
                 
Let us look at how it was done! 

--- .class #id 

## Solution

R along with googleVis helps in creating interactive document. Shiny allows you to publish this to server that can be served to anybody on the net.

googleVis package has several cool features that helps to create different kind of charts. The "Life Expectancy across Globe" application uses the following charts to make analysis of the WHO data interactive:-      
- gvisTable - to create an interactive table to display    
- gvisGeoChart - to Data on Map helping visualization     
- gvisMotionChart - an interactive plot to look at trends
- gvisMerge - to Merge the multiple plots to a page   

Let us look at how easy is to produce interactive graph. We will do how the "Life Expectancy across Globe" app does.

--- .class #id 

## Interactive Chart - Code

The code is below to create interactive chart 


```r
suppressPackageStartupMessages(library(googleVis))
# Read Data
a1<-"http://apps.who.int/gho/athena/data/data-verbose.csv?target=GHO/WHOSIS_000002,WHOSIS_000001,WHOSIS_000015&profile=verbose&filter=COUNTRY:*;REGION:AFR;REGION:AMR;REGION:SEAR;REGION:EUR;REGION:EMR;REGION:WPR;SEX:*"
d1<-read.csv(a1)
#filter to have a better set
d11<-d1[d1$YEAR..CODE=="2012" & d1$"GHO..CODE." =="WHOSIS_000001" & d1$SEX..CODE. =="BTSX",
        c("COUNTRY..DISPLAY.","Numeric")]
#Modify column names
names(d11) <- c("Country","Year")
# Geo chart
m<-gvisGeoChart(d11,locationvar="Country",colorvar="Year",                                               options=list( height=350,displayMode='auto',colorAxis="{values:[40,60,75,80],colors:[\'red', \'pink\', \'orange',\'green']}"))
# Table
q<-gvisTable(d11,options=list(page="enable",pageSize=5,sort="enable"))
# Merge
gt<-gvisMerge(m,q,horizontal=TRUE,
                              tableOptions="cellspacing=\"20\" bgcolor=\"#AABBCC\"")
```

--- .class #id 

## Interactive Chart - Chart


```r
print(gt,'chart')
```

<!-- GeoChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Sat Sep 20 22:18:05 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartID16b42f5d50ad () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Andorra",
83 
],
[
 "Antigua and Barbuda",
75 
],
[
 "Cyprus",
82 
],
[
 "Czech Republic",
78 
],
[
 "Ireland",
81 
],
[
 "Republic of Korea",
81 
],
[
 "Kuwait",
78 
],
[
 "Netherlands",
81 
],
[
 "New Zealand",
82 
],
[
 "Portugal",
81 
],
[
 "Singapore",
83 
],
[
 "Trinidad and Tobago",
70 
],
[
 "Ethiopia",
64 
],
[
 "Haiti",
62 
],
[
 "Myanmar",
66 
],
[
 "Niue",
74 
],
[
 "Sierra Leone",
46 
],
[
 "Togo",
58 
],
[
 "Azerbaijan",
72 
],
[
 "China",
75 
],
[
 "Georgia",
74 
],
[
 "Jordan",
74 
],
[
 "Kiribati",
66 
],
[
 "Papua New Guinea",
62 
],
[
 "Paraguay",
75 
],
[
 "Bahamas",
75 
],
[
 "Barbados",
78 
],
[
 "France",
82 
],
[
 "Hungary",
75 
],
[
 "Italy",
83 
],
[
 "Monaco",
82 
],
[
 "Norway",
82 
],
[
 "Saudi Arabia",
76 
],
[
 "Slovenia",
80 
],
[
 "Comoros",
62 
],
[
 "Eritrea",
63 
],
[
 "Guinea",
58 
],
[
 "Kyrgyzstan",
69 
],
[
 "Mali",
57 
],
[
 "Mauritania",
63 
],
[
 "South Sudan",
55 
],
[
 "Angola",
51 
],
[
 "Côte d'Ivoire",
53 
],
[
 "Guatemala",
72 
],
[
 "Iran (Islamic Republic of)",
74 
],
[
 "Lesotho",
50 
],
[
 "Maldives",
77 
],
[
 "Nicaragua",
73 
],
[
 "Philippines",
69 
],
[
 "United Arab Emirates",
76 
],
[
 "Belgium",
80 
],
[
 "Bahrain",
77 
],
[
 "Canada",
82 
],
[
 "Estonia",
77 
],
[
 "Finland",
81 
],
[
 "Equatorial Guinea",
55 
],
[
 "Malta",
81 
],
[
 "Sweden",
82 
],
[
 "Central African Republic",
51 
],
[
 "Ghana",
62 
],
[
 "Guinea-Bissau",
54 
],
[
 "Lao People's Democratic Republic",
66 
],
[
 "Mozambique",
53 
],
[
 "Uganda",
57 
],
[
 "Bhutan",
68 
],
[
 "Micronesia (Federated States of)",
69 
],
[
 "Indonesia",
71 
],
[
 "Morocco",
71 
],
[
 "Mongolia",
67 
],
[
 "Nigeria",
54 
],
[
 "El Salvador",
72 
],
[
 "Sao Tome and Principe",
67 
],
[
 "Brunei Darussalam",
77 
],
[
 "Germany",
81 
],
[
 "Greece",
81 
],
[
 "Iceland",
82 
],
[
 "Israel",
82 
],
[
 "Oman",
76 
],
[
 "San Marino",
83 
],
[
 "Afghanistan",
60 
],
[
 "Burundi",
56 
],
[
 "Democratic Republic of the Congo",
52 
],
[
 "Liberia",
62 
],
[
 "Niger",
59 
],
[
 "Senegal",
64 
],
[
 "Chad",
51 
],
[
 "Uzbekistan",
69 
],
[
 "Zimbabwe",
58 
],
[
 "Armenia",
71 
],
[
 "Cabo Verde",
74 
],
[
 "Djibouti",
61 
],
[
 "Honduras",
74 
],
[
 "Republic of Moldova",
71 
],
[
 "Austria",
81 
],
[
 "Japan",
84 
],
[
 "Nauru",
79 
],
[
 "Qatar",
79 
],
[
 "United States of America",
79 
],
[
 "Benin",
59 
],
[
 "Madagascar",
64 
],
[
 "Nepal",
68 
],
[
 "Democratic People's Republic of Korea",
70 
],
[
 "Somalia",
53 
],
[
 "Viet Nam",
76 
],
[
 "Cameroon",
56 
],
[
 "Guyana",
63 
],
[
 "Iraq",
70 
],
[
 "Sri Lanka",
75 
],
[
 "Marshall Islands",
70 
],
[
 "Australia",
83 
],
[
 "Switzerland",
83 
],
[
 "Cook Islands",
76 
],
[
 "Denmark",
80 
],
[
 "Spain",
82 
],
[
 "United Kingdom of Great Britain and Northern Ireland",
81 
],
[
 "Croatia",
78 
],
[
 "Luxembourg",
82 
],
[
 "Slovakia",
76 
],
[
 "Burkina Faso",
58 
],
[
 "Bangladesh",
70 
],
[
 "Gambia",
61 
],
[
 "Kenya",
61 
],
[
 "Cambodia",
72 
],
[
 "Malawi",
59 
],
[
 "Rwanda",
65 
],
[
 "Tajikistan",
68 
],
[
 "United Republic of Tanzania",
61 
],
[
 "Yemen",
64 
],
[
 "Zambia",
57 
],
[
 "Albania",
74 
],
[
 "Belize",
75 
],
[
 "Bolivia (Plurinational State of)",
68 
],
[
 "Congo",
59 
],
[
 "Ecuador",
75 
],
[
 "Egypt",
71 
],
[
 "India",
66 
],
[
 "Pakistan",
65 
],
[
 "Thailand",
75 
],
[
 "Ukraine",
71 
],
[
 "Cuba",
79 
],
[
 "Gabon",
63 
],
[
 "Saint Kitts and Nevis",
74 
],
[
 "South Africa",
59 
],
[
 "Turkmenistan",
63 
],
[
 "Botswana",
62 
],
[
 "Latvia",
74 
],
[
 "Montenegro",
76 
],
[
 "Mauritius",
74 
],
[
 "Peru",
77 
],
[
 "Serbia",
75 
],
[
 "Venezuela (Bolivarian Republic of)",
76 
],
[
 "Chile",
80 
],
[
 "Colombia",
79 
],
[
 "Dominican Republic",
77 
],
[
 "Palau",
73 
],
[
 "Uruguay",
77 
],
[
 "Tonga",
71 
],
[
 "Bosnia and Herzegovina",
77 
],
[
 "Belarus",
72 
],
[
 "Algeria",
72 
],
[
 "Grenada",
73 
],
[
 "Mexico",
76 
],
[
 "Namibia",
67 
],
[
 "Poland",
77 
],
[
 "Sudan",
63 
],
[
 "Solomon Islands",
69 
],
[
 "Swaziland",
54 
],
[
 "Syrian Arab Republic",
68 
],
[
 "Timor-Leste",
66 
],
[
 "Tunisia",
76 
],
[
 "Samoa",
73 
],
[
 "Costa Rica",
79 
],
[
 "Jamaica",
74 
],
[
 "Lebanon",
80 
],
[
 "Libya",
75 
],
[
 "The former Yugoslav republic of Macedonia",
76 
],
[
 "Malaysia",
74 
],
[
 "Suriname",
77 
],
[
 "Seychelles",
74 
],
[
 "Saint Vincent and the Grenadines",
74 
],
[
 "Vanuatu",
72 
],
[
 "Argentina",
76 
],
[
 "Bulgaria",
74 
],
[
 "Brazil",
74 
],
[
 "Dominica",
75 
],
[
 "Fiji",
69 
],
[
 "Kazakhstan",
68 
],
[
 "Saint Lucia",
75 
],
[
 "Lithuania",
74 
],
[
 "Panama",
77 
],
[
 "Romania",
74 
],
[
 "Russian Federation",
69 
],
[
 "Turkey",
75 
],
[
 "Tuvalu",
68 
] 
];
data.addColumn('string','Country');
data.addColumn('number','Year');
data.addRows(datajson);
return(data);
}


// jsData 
function gvisDataTableID16b42e193f05 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Andorra",
83 
],
[
 "Antigua and Barbuda",
75 
],
[
 "Cyprus",
82 
],
[
 "Czech Republic",
78 
],
[
 "Ireland",
81 
],
[
 "Republic of Korea",
81 
],
[
 "Kuwait",
78 
],
[
 "Netherlands",
81 
],
[
 "New Zealand",
82 
],
[
 "Portugal",
81 
],
[
 "Singapore",
83 
],
[
 "Trinidad and Tobago",
70 
],
[
 "Ethiopia",
64 
],
[
 "Haiti",
62 
],
[
 "Myanmar",
66 
],
[
 "Niue",
74 
],
[
 "Sierra Leone",
46 
],
[
 "Togo",
58 
],
[
 "Azerbaijan",
72 
],
[
 "China",
75 
],
[
 "Georgia",
74 
],
[
 "Jordan",
74 
],
[
 "Kiribati",
66 
],
[
 "Papua New Guinea",
62 
],
[
 "Paraguay",
75 
],
[
 "Bahamas",
75 
],
[
 "Barbados",
78 
],
[
 "France",
82 
],
[
 "Hungary",
75 
],
[
 "Italy",
83 
],
[
 "Monaco",
82 
],
[
 "Norway",
82 
],
[
 "Saudi Arabia",
76 
],
[
 "Slovenia",
80 
],
[
 "Comoros",
62 
],
[
 "Eritrea",
63 
],
[
 "Guinea",
58 
],
[
 "Kyrgyzstan",
69 
],
[
 "Mali",
57 
],
[
 "Mauritania",
63 
],
[
 "South Sudan",
55 
],
[
 "Angola",
51 
],
[
 "Côte d'Ivoire",
53 
],
[
 "Guatemala",
72 
],
[
 "Iran (Islamic Republic of)",
74 
],
[
 "Lesotho",
50 
],
[
 "Maldives",
77 
],
[
 "Nicaragua",
73 
],
[
 "Philippines",
69 
],
[
 "United Arab Emirates",
76 
],
[
 "Belgium",
80 
],
[
 "Bahrain",
77 
],
[
 "Canada",
82 
],
[
 "Estonia",
77 
],
[
 "Finland",
81 
],
[
 "Equatorial Guinea",
55 
],
[
 "Malta",
81 
],
[
 "Sweden",
82 
],
[
 "Central African Republic",
51 
],
[
 "Ghana",
62 
],
[
 "Guinea-Bissau",
54 
],
[
 "Lao People's Democratic Republic",
66 
],
[
 "Mozambique",
53 
],
[
 "Uganda",
57 
],
[
 "Bhutan",
68 
],
[
 "Micronesia (Federated States of)",
69 
],
[
 "Indonesia",
71 
],
[
 "Morocco",
71 
],
[
 "Mongolia",
67 
],
[
 "Nigeria",
54 
],
[
 "El Salvador",
72 
],
[
 "Sao Tome and Principe",
67 
],
[
 "Brunei Darussalam",
77 
],
[
 "Germany",
81 
],
[
 "Greece",
81 
],
[
 "Iceland",
82 
],
[
 "Israel",
82 
],
[
 "Oman",
76 
],
[
 "San Marino",
83 
],
[
 "Afghanistan",
60 
],
[
 "Burundi",
56 
],
[
 "Democratic Republic of the Congo",
52 
],
[
 "Liberia",
62 
],
[
 "Niger",
59 
],
[
 "Senegal",
64 
],
[
 "Chad",
51 
],
[
 "Uzbekistan",
69 
],
[
 "Zimbabwe",
58 
],
[
 "Armenia",
71 
],
[
 "Cabo Verde",
74 
],
[
 "Djibouti",
61 
],
[
 "Honduras",
74 
],
[
 "Republic of Moldova",
71 
],
[
 "Austria",
81 
],
[
 "Japan",
84 
],
[
 "Nauru",
79 
],
[
 "Qatar",
79 
],
[
 "United States of America",
79 
],
[
 "Benin",
59 
],
[
 "Madagascar",
64 
],
[
 "Nepal",
68 
],
[
 "Democratic People's Republic of Korea",
70 
],
[
 "Somalia",
53 
],
[
 "Viet Nam",
76 
],
[
 "Cameroon",
56 
],
[
 "Guyana",
63 
],
[
 "Iraq",
70 
],
[
 "Sri Lanka",
75 
],
[
 "Marshall Islands",
70 
],
[
 "Australia",
83 
],
[
 "Switzerland",
83 
],
[
 "Cook Islands",
76 
],
[
 "Denmark",
80 
],
[
 "Spain",
82 
],
[
 "United Kingdom of Great Britain and Northern Ireland",
81 
],
[
 "Croatia",
78 
],
[
 "Luxembourg",
82 
],
[
 "Slovakia",
76 
],
[
 "Burkina Faso",
58 
],
[
 "Bangladesh",
70 
],
[
 "Gambia",
61 
],
[
 "Kenya",
61 
],
[
 "Cambodia",
72 
],
[
 "Malawi",
59 
],
[
 "Rwanda",
65 
],
[
 "Tajikistan",
68 
],
[
 "United Republic of Tanzania",
61 
],
[
 "Yemen",
64 
],
[
 "Zambia",
57 
],
[
 "Albania",
74 
],
[
 "Belize",
75 
],
[
 "Bolivia (Plurinational State of)",
68 
],
[
 "Congo",
59 
],
[
 "Ecuador",
75 
],
[
 "Egypt",
71 
],
[
 "India",
66 
],
[
 "Pakistan",
65 
],
[
 "Thailand",
75 
],
[
 "Ukraine",
71 
],
[
 "Cuba",
79 
],
[
 "Gabon",
63 
],
[
 "Saint Kitts and Nevis",
74 
],
[
 "South Africa",
59 
],
[
 "Turkmenistan",
63 
],
[
 "Botswana",
62 
],
[
 "Latvia",
74 
],
[
 "Montenegro",
76 
],
[
 "Mauritius",
74 
],
[
 "Peru",
77 
],
[
 "Serbia",
75 
],
[
 "Venezuela (Bolivarian Republic of)",
76 
],
[
 "Chile",
80 
],
[
 "Colombia",
79 
],
[
 "Dominican Republic",
77 
],
[
 "Palau",
73 
],
[
 "Uruguay",
77 
],
[
 "Tonga",
71 
],
[
 "Bosnia and Herzegovina",
77 
],
[
 "Belarus",
72 
],
[
 "Algeria",
72 
],
[
 "Grenada",
73 
],
[
 "Mexico",
76 
],
[
 "Namibia",
67 
],
[
 "Poland",
77 
],
[
 "Sudan",
63 
],
[
 "Solomon Islands",
69 
],
[
 "Swaziland",
54 
],
[
 "Syrian Arab Republic",
68 
],
[
 "Timor-Leste",
66 
],
[
 "Tunisia",
76 
],
[
 "Samoa",
73 
],
[
 "Costa Rica",
79 
],
[
 "Jamaica",
74 
],
[
 "Lebanon",
80 
],
[
 "Libya",
75 
],
[
 "The former Yugoslav republic of Macedonia",
76 
],
[
 "Malaysia",
74 
],
[
 "Suriname",
77 
],
[
 "Seychelles",
74 
],
[
 "Saint Vincent and the Grenadines",
74 
],
[
 "Vanuatu",
72 
],
[
 "Argentina",
76 
],
[
 "Bulgaria",
74 
],
[
 "Brazil",
74 
],
[
 "Dominica",
75 
],
[
 "Fiji",
69 
],
[
 "Kazakhstan",
68 
],
[
 "Saint Lucia",
75 
],
[
 "Lithuania",
74 
],
[
 "Panama",
77 
],
[
 "Romania",
74 
],
[
 "Russian Federation",
69 
],
[
 "Turkey",
75 
],
[
 "Tuvalu",
68 
] 
];
data.addColumn('string','Country');
data.addColumn('number','Year');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartGeoChartID16b42f5d50ad() {
var data = gvisDataGeoChartID16b42f5d50ad();
var options = {};
options["width"] =    556;
options["height"] =    200;
options["displayMode"] = "auto";
options["colorAxis"] = {values:[40,60,75,80],colors:['red', 'pink', 'orange','green']};

    var chart = new google.visualization.GeoChart(
    document.getElementById('GeoChartID16b42f5d50ad')
    );
    chart.draw(data,options);
    

}
  


// jsDrawChart
function drawChartTableID16b42e193f05() {
var data = gvisDataTableID16b42e193f05();
var options = {};
options["allowHtml"] = true;
options["page"] = "enable";
options["pageSize"] =      5;
options["sort"] = "enable";

    var chart = new google.visualization.Table(
    document.getElementById('TableID16b42e193f05')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "geochart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartGeoChartID16b42f5d50ad);
})();
function displayChartGeoChartID16b42f5d50ad() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}


// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "table";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTableID16b42e193f05);
})();
function displayChartTableID16b42e193f05() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartID16b42f5d50ad"></script>


<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableID16b42e193f05"></script>
 
<table cellspacing="20" bgcolor="#AABBCC">
<tr>
<td>

<!-- divChart -->
  
<div id="GeoChartID16b42f5d50ad" 
  style="width: 556; height: 200;">
</div>

</td>
<td>

<!-- divChart -->
  
<div id="TableID16b42e193f05" 
  style="width: 500; height: automatic;">
</div>

</td>
</tr>
</table>

Use the mouse on the above plots to see the interactive plot. You can change the table sort order as well

If you liked it, visit http://perumalkumar.shinyapps.io/ShinyPrj1/   to see the code in action. You can also see the R code.

