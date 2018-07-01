> Feeling impatient? Dive into some calculations we already prepared: [analysis.pdf](analysis.pdf)

# Maternity clinic distances

This repository contains the data used for researching distances to the nearest maternity clinic for [Ottar](https://www.ottar.se/). For the published outcome, see:

 - http://bb-resan.ottar.se/ (Interactive. Select your municipality, and make the journey to your nearest maternity ward)
 - https://www.ottar.se/artiklar/krystv-rkar-p-d-dens-v-g
 - https://www.ottar.se/artiklar/bb-avst-nden-kar-s-l-ngt-r-det-i-din-kommun
 - Further texts available in print: https://www.ottar.se/tidskriften/vischan)

We created a database of maternity clinics in since 2000, and then we used 1x1 km populations grids of Sweden (113,000 squares) to calculate distances. That way we could calculate the average distance for inhabitants in each municipality and how it changed over the years, find the approximate number of people who had more than a certain distance to the nearest maternity clinic at a given time, etc.

A summary of the analysis is provided in the PDF file [analysis.pdf](analysis.pdf).

Weaknesses and potential pitfalls of the data include, but are not limited to:

 - We have used population grids from two points in time only. Having one grid for each year in the analysis would obviously be better. That data is available, but has to be paid for, from SCB.
 - Distances given are beeline (great-circle) distances, and do not reflect traveling times, or even real life traveling distances. While routing ([GraphHopper](https://www.graphhopper.com/) is a great tool for that) each point/clinic pair would more or less be possible, that comes with its own difficulties, as historical road data is not easily available, some points, e.g. isolated islands, will be hard or impossible to route, and the point-by-point alignment that needs to be done to put points close enough to a road is not as straightforward as it might seem.
 - The population grid contains the whole population, not just those in fertile age. This may or may not be the desired data, depending on what kind of conclusions you are after.

We believe that the conclusions in the published articles stand despite these issues, but some numbers included in the analyses in this repository might not. You will obviously have to use any numbers drawn from this data with care.

Did we overlook something? Please let us know! (stockholm@jplusplus.org)[mailto:stockholm@jplusplus.org]


## Running the analysis

The data is in CSV files: Two 1x1 km population grids (one earlies and one later), with centroid coordinates and municipality, and one list of maternity wards with start and end dates for each.

We have prepared a number of calculations to get you started in a Python 3 notebook:

```shell
jupyter-notebook ./bb.ipynb
```


## Installing

This code is written for Python 3. Depending on your environment, you will use either `pip` or `pip3` to install required modules.

```shell
git clone https://github.com/jplusplus/bb
pip3 install -r requirements.txt
```

We strongly suggest you use [virtual environments](https://docs.python.org/3/library/venv.html) for your Python installations.


## Developing

To update the submodule [datatypes](https://github.com/jplusplus/statscraper-datatypes):

```shell
git subtree pull -P datatypes --squash https://github.com/jplusplus/statscraper-datatypes.git master
```
