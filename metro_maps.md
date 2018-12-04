Metropolitan Area Maps
================
Charlotte Mack
November 27, 2018

A few maps of U.S. Census Bureau core-based statistical areas (CBSAs), based partly on a protocol by Kyle E. Walker, ["Generating metropolitan subsets of Census data with R and tigris."](http://walkerke.github.io/2017/05/tigris-metros/) These maps show the counties that comprise the CBSAs. Census determines CBSAs on a county basis, with counties being included entirely or not at all. In the present delineation, dated 2015, there are 389 Metropolitan CBSAs centered on the larger cities in the country, and 945 including the smaller Micropolitan areas ([U.S. Census Bureau, "Metropolitan and Micropolitan"](https://www.census.gov/programs-surveys/metro-micro/about.html)). Delineations of CBSAs are changed periodically with counties sometimes added or removed, so care should be taken of the components of CBSAs or metropolitan (and micropolitan) areas when doing studies over time. As one might want to generate sets of CBSA maps for multicity projects, automation of the project is desirable. The maps here illustrate some of the issues to be handled.

Each map has three layers, the CBSA as a whole, the set of counties, and the states; where the CBSA is contained in only one State this last layer can be omitted. The full name of the CBSA, which includes the State or States of its domicile, is extracted from the roster given by tigris::core\_based\_statistical\_areas(). State names are stripped from this into a vector, which is then used to filter the output of the tigris::counties() command by States, to get the counties of the States in question. The subset of counties needed for the CBSA are extracted using an indexing procedure from Kyle Walker. Finally, for the cases where the CBSA extends to more than one State, a layer of the constituent States is clipped to the outline of the CBSA and, using a ggplot() aesthetic designation, colored for identification.

Metropolitan Chicago map
========================

![](metro_maps_files/figure-markdown_github/Chicago%20CBSA%20map-1.png)

Do It Again: Metropolitan Philadelphia map
==========================================

![](metro_maps_files/figure-markdown_github/Philadelphia%20CBSA%20map-1.png)

A One-State Case: Los Angeles
=============================

![](metro_maps_files/figure-markdown_github/Los%20Angeles%20CBSA%20map-1.png)

New York City CBSA Through the Years
====================================

A moderate example of change in the delineation of a CBSA. The New York State counties of Dutchess and Orange were added to the CBSA around New York City between the delineations of 2011 and 2015. More dramatic examples of which I am aware occurred outside the time frame of the tigris package datasets, such as the five counties that were added to the Charlotte, NC CBSA between 2009 and 2013, doubling the number of counties in that area.

![](metro_maps_files/figure-markdown_github/New%20York%20City%20CBSA%20map%202011-1.png)

![](metro_maps_files/figure-markdown_github/New%20York%20CBSA%20map%202015-1.png)
