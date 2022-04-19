# Advanced_analytics_on_Youtube_videos
This project provides notebooks to scrape videos from a Youtube channel, model Topics  and predict video likes

## Youtube_scraper.ipynb

This notebook shows how to 

*  Scrape youtube videos from a Youtube channel

*  Get likes related to each video

*  Download each video

We simply use `selenium` to drive actions on Youtube pages.
One can simply provide to selenium the xml path (`Xpath`) to the desired element (ex: number of video likes).

The xml path of a given element can be copy-pasted from "inspect" mode on browser (`Copy > Copy full XPath`):

![IMG_20220420_002627](https://user-images.githubusercontent.com/16710784/164112363-3c881076-13a4-4e1e-8532-6c9c62c34605.jpg)

Difficulties appear when interactions through selenium driver are needed like:

*  Scrolling the channel videos page to get all videos or the video comments section to get all comments

*  Clicking on comments icon to make short video comments displayed

Videos downloadiing is simply performed thanks to [youtube-dl](https://github.com/ytdl-org/youtube-dl). The video downloading being IO-bound, we implement a multithreaded videos loop.


NB: Possible improvments can be made by reaching also comments replies, which are much more numerous than comments themselves.

