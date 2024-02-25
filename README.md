# Project-4-DMCAs
 
This repository contains the notebooks used while working to the forth project of the LEDE Program. You can read the final story at the following link: [Google is still falling for an old trick](https://marcodallastella.github.io/articles/dmca.html)

## Notebook 1 : Google DMCA data
I used this notebook to clean and extract relevant information from a large dataset of takedown requests received by Google and available at the [Google Transparency Report](https://transparencyreport.google.com/copyright/overview?hl=en&copyright_result_owner=&copyright_result_org=&copyright_result_domain=&search_copyright=q:https&lu=search_copyright).

Because of the size of the dataset (various millions of rows) I had to decide a criteria to reduce its size and focus my work. I opted for only keeping successful requests (meaning that resulted in at least one link removed from Google search results) from 2023. I then filtered out submissions coming from an organization or entity with more than one-houndred submissions - that's because fraudulent DMCAs are usually made with fictitious names, while legit complaints usually come from legit organizations that always identify themselves.

## Notebook 2 : Lumen Data
I used this notebook to download details about the notices from the [Lumen Database](https://lumendatabase.org/). That's because Google Transparency Report data does not include details about the takedown request, but it does include the Lumen ID number. I used that number to interact with the Lumen API and store all relevant data as a json file.

## Notebook 3 : Final cleaning and analysis
I used this notebook to clean and analyse the json data previously downloaded. My goal was to find a way to efficiently identify fraudulent-looking takedown requests. For this reason I operated according the following criteria:

* Keeping only notices that originated from blogs. I identified blogging platofrms using the words `blogspot`, `tumblr`, `livejournal`, `issuu`, `wix`, `over-blog`.
* Flattening the json, melting together various `infringing_urls` and `copyrighted_urls`.
* Removing all requests that targeted a blogging platoform (likely not actual journalism).
* Removed most common `infringing_source`. This step was made to keep the dataset as small as possible. I did this to eliminate common sites being targeted which are usually forums or sketchy websites of pirate contents. However, if a website of a newspaper has been targeted more than ten times, it won't be in the final data being analyzed. This is something that might be changed in the future to keep a higher barrier.
* To identify most relevant examples, I ended my analyisis on [Google Sheets](https://docs.google.com/spreadsheets/d/1PkJy7dFvoSeltSoXpe2EcXKVoScQheMzlwKtXImdDU0/edit?usp=sharing)

## Things to improve
My initial idea was to use machine learning and NLP to cluster articles together and identify groups of articles that are of interest. I had to abandon this initial idea for time constraints but hopefully will come back to it later.

## Contact information
Marco Dalla Stella
md3934@columbia.edu
