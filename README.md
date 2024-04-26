# news-article-guideline

We are expecting to see a standard RSS 2.0 feed like this [example](https://www.rssboard.org/files/sample-rss-2.xml)

Each article should have an `<item>` entity

The following entities are _required_ for each article:

- `<title>`
  - Title of the article
- `<link>`
  - Unique link where the original article lives
  - Must be unique, or our feed processor will not accept the article as new
- `<content>`
  - Body content of the article
  - Should be encoded with a `CDATA` [section](https://www.w3.org/TR/REC-xml/#sec-cdata-sect)

We additionally parse following optional entities:

- `<image>`
  - A thumbnail image of the article
  - Contains 2 sub elements:
    - `<loc>` The URL of the image
    - `<title>` A description of the image, basically an `alt` attribute that will get added to the article markup 
- `<description>`
  - A summary of the article
- `<stock_tickers>`
  - Comma separated list of tickers associated with the article
- `<category>`
  - Comma separated list of categories

Here's a full example:

```
<?xml version="1.0"?>    
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom" xmlns:content="http://purl.org/rss/1.0/modules/content/" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">    
   <channel>    
      <title>NASA ISS Feed</title>    
      <link>http://www.nasa.gov/</link>    
      <description>A RSS news feed containing the latest NASA press releases on the International Space Station.</description>    
      <language>en-us</language>    
      <pubDate>Tue, 10 Jun 2023 04:00:00 GMT</pubDate>    
      <lastBuildDate>Fri, 21 Jul 2023 09:04 EDT</lastBuildDate>    
      <item>                                                       
         <title>This is a great article</title>    
         <link>https://www.nasa.gov/press-release/nasa-to-provide-briefing-coverage-of-spacewalks-for-station-upgrades</link>    
         <description>As part of the state's first Earth-to-space call, students from Louisiana will have an opportunity soon to hear from NASA astronauts aboard the International Space Station.</description>
         <content:encoded><![CDATA[<p>Two NASA astronauts aboard the International Space Station will conduct a pair of spacewalks Friday, June 9, and Thursday, June 15, to install two new solar arrays....</p>]]></content:encoded>
         <image:image>    
             <image:loc>https://www.nasa.gov/sites/default/files/styles/full_width/public/thumbnails/image/iss069e005732orig.jpeg</image:loc>    
             <image:title>NASA astronaut and Expedition 69 Flight Engineer Steve Bowen is pictured outside the International Space Station during his eighth career spacewalk, during which he routed cables and installed insulation to ready the orbital outpost for its next set of roll-out solar arrays.</image:title>
         </image:image>    
         <stock_tickers>IBM,AAPL,TSLA</stock_tickers>    
         <category>Science,Technology,Space</category>    
      </item>
      <item>
        ...  
      </item>
  </channel>    
</rss>
```
