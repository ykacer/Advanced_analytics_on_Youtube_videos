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

![IMG_20220420_003849](https://user-images.githubusercontent.com/16710784/164119959-4b74667c-0530-42b7-910a-a6ca41f5f955.jpg)

Difficulties appear when interactions through selenium driver are needed like:

*  Scrolling the channel videos page to get all videos or the video comments section to get all comments

*  Clicking on comments icon to make short video comments displayed

*  The video comments scraping being IO-bound, we implement a multithreaded videos loop.


Videos downloading is simply performed thanks to [youtube-dl](https://github.com/ytdl-org/youtube-dl).


NB: Possible improvments can be made by reaching also comments replies, which are much more numerous than comments themselves.

References:

* https://python.plainenglish.io/scraping-joe-rogans-youtube-profile-and-ranking-his-videos-by-popularity-with-python-pandas-and-a684fff4472e

* https://towardsdatascience.com/how-to-scrape-youtube-comments-with-python-61ff197115d4


## Youtube_topics_modeling.ipynb

This notebook aims at finding Youtube videos topics through theirs comments.

*Non-Negative matrix factorization* and *Latent Discrimination Analysis* are the dedicated algorithm when it comes to cluster texts.
Such algorithms takes as input observations (document/word matrix like *Term-Frequency* or *Term-Frequency Inversed-Document-Frequency*) and tries to reach the same objective : providing words weights for each *K* topic (*K* being a user parameter). One can then directly interpret each topic by reviewing its top weighted words (see figure below).

The only difference is that *LDA* solves the problem in a probalistic way (the weights are seen as a Dirichlet distribution parameters) while *NMF* uses a pure matrix factorization with positivity constraints.

In the notebook, we define a Youtube videos text as the concatenation of all its comments.

We apply such topic modeling on 61 Youtube videos (published one month ago) from [Brut.](https://www.youtube.com/channel/UCSKdvgqdnj72_SLggp7BDTg)  Youtube channel. *Brut.* being a media, we expect to find topics related to recents news or society trends.

We finally found that *NMF* is better at providing coherent *K* word distributions `P(word/topic_{k})` (*K*=5):

![image](https://user-images.githubusercontent.com/16710784/164117632-289d087a-cfa1-4819-9927-261419f1580e.png)

*  topic 1 related to War in Ukrania

*  topic 3 related to men/women equality

*  topic 4 related to 2022 French elections

*  topic 5 related to Covid pandemia

Topic 2 seems to be a mix of various topics, but increasing *K* has no positive effects. A solution could be to use replies comments to enrich each Youtube video text.

References:

* https://scikit-learn.org/stable/auto_examples/applications/plot_topics_extraction_with_nmf_lda.html

## Youtube_video_likes_prediction.ipynb
