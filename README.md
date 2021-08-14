# Martin's Oakland American Community Survey (ACS) Data Dive

## Introduction
***
The new numbers coming out of the 2020 U.S. Census have been receiving a lot of attention recently. What is less well-known is that the American Community Survey (ACS) is a Census Bureau-run program that surveys 3.5 million Americans each year as part of a larger data gathering effort. This data is available for free via BigQuery's public datasets program. While I am certainly skeptical of the quality of survey data in general, I was surprised This is a mandatory survey, with nonparticipation that could even result in a fine, and with the resources and backing of the U.S. government.

As a resident of Oakland, California for the past two years, I've been acutely aware of -- and curious about -- a variety of demographic, economic, and societal changes taking place in our city. I decided to explore the ACS data to see what I could find, and whether its findings matched my predictions.

In this project I access ACS data via BigQuery's API and perform some exploratory data analysis in Python and Pandas. There's so much to see and explore in this one dataset alone, and this notebook is just me scratching the surface.

## Prerequisites
***
To get started you'll need to install and import some libraries:
`from google.cloud import bigquery
import pandas as pd
import os
import numpy as np
import matplotlib.ticker as mtick
import matplotlib.pyplot as plt
from heatmap import heatmap, corrplot`

I use Google's own BigQuery Python Library to pull the data straight from the BigQuery API into a dataframe, numpy for plotting a few best fit lines, and a fantastic package called [`heatmapz`](https://pypi.org/project/heatmapz/) that makes really pretty, simple correlation heatmaps using Matplotlib and Seaborn.

In particular I had to install bigquery using

`pip install --upgrade google-cloud 

pip install --upgrade google-cloud-bigquery 

pip install --upgrade google-cloud-storage`

Let's just say it a couple tries and StackOverflows to get it right.

Also, I had to closely follow the [BigQuery getting started documentation](https://cloud.google.com/docs/authentication/getting-started) to get authenticated.