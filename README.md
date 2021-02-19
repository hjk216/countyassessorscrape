{\rtf1\ansi\ansicpg1252\cocoartf2576
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica-Bold;\f1\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\margl1440\margr1440\vieww10820\viewh9200\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\b\fs24 \cf0 County Assessor Real Property Information\
\
Summary / Project Structure
\f1\b0 \
\
I set out to create a simple Cuyahoga County Assessor property web scraper.  In my scripts I scraped the information of real property in Orange, Ohio.  I retrieved information on parcels, addresses, property class, transfers, values, and permits.  I then wrote few scripts analyzing the data, including calculating the annual appreciation rate for each property and the suburb as a whole.  \
\
\
\

\f0\b Get_Parcel_Numbers.py\

\f1\b0 There was no easy way to retrieve all the valid properties in Orange, Ohio.  The only data I could get from the county assessor was a list of addresses, and when typed into the Cuyahoga property search would not yield any results.  Therefore, the only way was to collect all the valid parcel numbers and search that way.  I noticed, from clicking around on the map, that parcel numbers in Orange started with 901, and are eight digits long.  Cuyahoga County has a parcel search that retrieves all relevant documents on the given parcel.  I made the assumption that if a parcel number was valid, then it would have at least one document of some kind.  The following web scraper typed in all numbers from 90100000 to 90199999, and if there was a document, it was labeled VALID, and if there was no document, INVALID.  All number and label data was then saved into a text file.\
\
\
\

\f0\b Get_Valid_Parcel_Numbers.py
\f1\b0 \
Reads parcel numbers from possible parcel number list.  Line by line, if the parcel is valid, then it is put into a new file.\
\
\
\

\f0\b County_Assessor_Web_Scraper.py\

\f1\b0 Web scraper searches each parcel number in the Cuyahoga County property search, and saves information to a file.  I chose to scrape and save, the parcel number, address, property class, transfer information (date and sales amount), values (date and value amount), and construction permits (date and added tax value).  The data was saved in arrays, each array representing a parcel, and printing into a text file.\
\
\
\

\f0\b Clean_Data.py\

\f1\b0 The web scrape was not perfect, and looking through the data file, I noticed some things needed to be removed or cleaned up.  This script cleans that data and pastes the cleaned data to a new file.\
\
After collecting all the data, I found that there were properties with the property class of \'93LW,\'94 or \'93listed with.\'94  The properties appeared to be city property or special properties in that the county does not assess them.  Therefore, I decided to remove these from the final property list.  There were also parcels with property class, \'93H,\'94 for highway, which was also not included.  Properties with property classes of \'93A,\'94 for agriculture, \'93E,\'94 for exempt, \'93RE,\'94 for residential-exempt, and \'93CE,\'94 for commercial-exempt, were included.\
\
\
\

\f0\b Analysis.py\

\f1\b0 In this script I wrote a few functions as examples of what we can use the data to discover.  I included functions for calculating the average assessed market residential value, how many homes were sold in 2020, and the average annual appreciation rate for all property in Orange over the last six years.  At the end of the file I also included a function to print, for each property, the parcel number, address, property class, and appreciation rate.  To calculate the annual appreciation rate I used the following formula: Appreciation = ((endvalue/startvalue)**(1.0/period))  - 1.\
\
\
\

\f0\b \
}