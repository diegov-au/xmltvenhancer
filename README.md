# xmltvenhancer
xmltvenhancer is an application used to enhance your XMLTV based EPG by adding artwork and other metadata.

The application is available as both a linux and windows package. It is designed to run as a scheduled task via task scheduler or cron.

As of version 1, XMLTV enhancer will only add artwork, however over time will introduce additional metadata to enhance your EPG viewing experience.

# How it works
XMLTV Enhancer requires a local xmltv file or a xmltv url link to process. It will process the xmltv file and add a directory for each distinct programme under the directory <b>artwork</b>. It will then add an additional <b>icon src</b> element for each programme and then creating a link to a jpg stub file which can be replaced manually by you or via the TVDB service.

Once xmltvenhancer processes the (yourepgfile).xml file it will create a file named (yourepgfile)-enhanced.xml which you then use as your xmltv.xml source within emby.

If you are using your own xmltv.xml file as the input you must place it in the <b>xmltv</b> directory. The application automatically looks in this directory for your xmltv file.

# Installation

Create an xmltvenhancer directory and unzip to contents of the package into this directory.

# Notes

1. If you are using your own xml file place it in the <b>xmltv</b> directory. The application will automatically assume your xmltv file sits in this directory. It will not look in the root directory of the application. There is no need to specify this directory on the command line.

2. If you are using a URL, you must specify a local file name which the application will later append the -enhanced suffix to. Also not .gz files are not supported, only urls which server a raw xml feed.

3. To use the TVDB service you must register for a tvdb api key. You must place this api key in the xmltvenhanced.ini file. Once you have met these prerequisites, you enable tvdb poster lookup by adding the -enabletvdb switch

4. It is recommended you run -enabletvdb once as it will take time to scrape for the tvdb website, and then generally run xmltvenhancer without the -enabletvdb switch, to simply update the xmltv.xml file for emby consumption

5. In the event that artwork cannot be found or is incorrect, you can manually add your own artwork. Artwork that is added by either tvdb or you will not be replaced by the application

6. Currently the tvdb algorithm will only match currently running series, this is to reduce false positives.

# Usage Examples

xmlenhancer xmltv.xml (processes a local xmltv.xml file located in the xmltv directory)

xmlenhancer http://url/file.xml au-epg.xml (download the xmltv data from a url and saves it to au-epg.xml)

xmlenhancer http://url/file.xml au-epg.xml -enabletvdb (as above with the addition of enabling artwork processing via TVDB)

![xml](https://github.com/user-attachments/assets/3ea28196-0eef-4a67-a5c2-030d27568b66)


