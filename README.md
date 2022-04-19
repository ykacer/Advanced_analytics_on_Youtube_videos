# Advanced_analytics_on_Youtube_videos
This project provides notebooks to scrape videos from a Youtube channel, model Topics  and predict video likes

## Youtube_scraper.ipynb

This notebook shows how to 

*  scrape youtube videos from a Youtube channel

*  Get likes related to each video

*  Download each video

We simply use `selenium` to drive actions on Youtube pages. 
One can simply provide to selenium the xml path (`Xpath`) to the desired element (ex: number of video likes).
The xml path can be copy-paste from "inspect" mode on browser (`Copy > Copy full XPath`):
Difficulties appears when interaction through driver are needed like:

*  Scrolling the channel videos page to get all videos

*  Click on comments icon to make short video comments displayed

Videos download is simply performed thanks to [youtube-dl](https://github.com/ytdl-org/youtube-dl)

