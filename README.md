## Locating KBAs: An automated workflow for identifying potential Key Biodiversity Areas
##### Daniela Linero - [National Audubon Society](https://www.audubon.org/)  
 \
This GitHub repository is associated with the following website: [https://dlinero-kbas.github.io/](https://dlinero-kbas.github.io/)

### Introduction 
***
In the face of an alarming and accelerating loss of biodiversity, it is essential to safeguard the places that contribute significantly to the persistence of species around the world. The IUCN Species Survival and World Protected Areas Commissions recently led an effort to develop a [standard](https://portals.iucn.org/library/sites/library/files/documents/2016-048.pdf) for identifying the places with the highest conservation value, the Key Biodiversity Areas (KBAs; IUCN, 2016). In the process of identifying KBAs, it is recommended to first conduct a comprehensive scoping analysis (KBA Standards and Appeals Committee, 2020). However, this analysis requires a great effort to obtain, compile and analyze spatial data for as many taxonomic groups as possible. The *Locating KBAs workflow* helps to streamline the scoping analysis by using the R programming language and leveraging GBIF data. The workflow code accesses the occurrence data of species present in a user-defined area and determines all those that could trigger the criteria of the KBA standard. Subsequently, it helps users identifying the places where the potential trigger species occur in significant numbers. In this way, the workflow enables users to efficiently and transparently identify the sites where it is most appropriate to focus efforts on gathering information on mature individuals, engaging stakeholders, and applying the standard’s criteria. 


### Methodology 
***

#### 1. Installation and initial requirements

To get started, you need to confirm that you have the following requirements:

* Have R and RStudio installed on your computer. If you do not have them, please download and install [R](https://cran.r-project.org/) first and continue downloading and installing [RStudio](https://www.rstudio.com/products/rstudio/).

* Have a GitHub account and GitHub Desktop installed on your computer. You can create a free GitHub account [here](https://github.com/) and download GitHub Desktop [here](https://desktop.github.com/). 

* Have a GBIF account. If you do not have one yet, create it using this [link](https://www.gbif.org/user/profile).

* Request an API Key [here](https://apiv3.iucnredlist.org/) to access the IUCN Red List information. 


Once you have met all the above requirements, open RStudio and make sure you have the following packages installed; otherwise use the following code to install them:


```{r, eval=FALSE}

install.packages(c("tidyverse", "Hmisc", "rgbif", "wellknown", "rredlist", "ggplot2", "ggspatial", "RCurl", “xml2”, “rvest”, “sf”, “DT”, “leaflet”, “knitr”))
```


#### 2. Workflow 

The workflow code  is designed to facilitate and streamline the scoping analysis for KBAs identification by leveraging the free and open access data of GBIF. Before exploring and running the workflow code, I encourage users to familiarize themselves with the [Global Standard for the Identification of Key Biodiversity Areas](https://portals.iucn.org/library/sites/library/files/documents/2016-048.pdf) (IUCN, 2016) and the [Guidelines for using this standard](https://portals.iucn.org/library/sites/library/files/documents/2020-033-En.pdf) (KBA Standards and Appeals Committee, 2020).

In this workflow we will focus solely on the following species-based criteria:

* A1 for globally threatened species
* B for restricted-range species
* D1 for congregations of species during a particular stage of their life cycle


The workflow is divided into **three main steps**. First, the user downloads and cleans GBIF occurrence data. The code then retrieves information for each species present in the dataset, accessing the IUCN Red List and Bird Data Zone portals and the tools provided in the following KBA [webpage](http://www.keybiodiversityareas.org/working-with-kbas/proposing-updating/criteria-tools). With this information, the code **selects the species present in the study area that have the potential to trigger the aforementioned KBA criteria.** The second step is to apply two functions that allow the user to map the location of the potential trigger species and **identify the sites where they occur in significant numbers.** In the case of bird species, it is also possible to locate the places where they meet the thresholds of the KBA criteria considered. The last step of the workflow is to **obtain the citations** of the different sources of information consulted in the previous steps. 

The scheme below represents the overall workflow 

![](methods/Workflow.jpeg)

#### 3. Detailed step-by-step instructions 

Please visit this [website](https://dlinero-kbas.github.io/) and select the Notebook tab. There you will find the explanation of all the steps to complete the workflow and their associated code.  Additionally, you will be able to interact with the most important results of the workflow, such as the table of potential trigger species and the maps of the sites where they occur in significant numbers. 


### Example outputs
***

The following is a preview of the table to identify potential trigger species for the above criteria (globally threatened species, restricted range species, species that form seasonal congregations). For bird species, it is also possible to obtain the global number of mature individuals and calculate the criteria thresholds.

![](https://media.giphy.com/media/DWLQNMalkuxhvMXRbG/giphy.gif)

The code also contains a function that will help the user identifying the sites where potential trigger species have large counts or where there are multiple records of potential trigger species.

![](https://media.giphy.com/media/oWrsaglCvK79HCkV82/giphy.gif)

A second function, available only for bird species, creates an interactive map showing the location of records that meet the threshold of individuals for each criterion evaluated.

![](https://media.giphy.com/media/n7im3EPT7aMvoEBgr7/giphy.gif)


### GitHub repository structure
***


```
│   Notebook_files/figure-html            : Figures shown in the notebook(R Markdown)
│
└───data
│   └───   Quindio.shp                    : Shapefile of the study area
│
└───methods
│   └───   Workflow.jpeg                  : Workflow schema
│   └───   howto_.jpg                     : Screenshots on how to clone the repository 
│   
└───outputs
│    └───   Map_1.png                     : Example of the output of map function 1
│    └───   Map_2.png                     : Example of the output of map function 2
│
└───site_libs                             : Website rendering files
│   
│   .gitignore                            : Files to be ingored by github
│   .nojekyll                             : Establish website themes
│   GitHub_repository.Rmd                 : Markdown file with the repository link
│   GitHub_repository.html                : html file derived from markdown
│   LICENSE                               : Repository license  
│   Notebook.Rmd                          : Markdown file with workflow code
│   Notebook.html                         : html file derived from markdown
│   README.md                             : Description of the repository
│   _site.yml                             : Website configuration file
│   dlinero-KBAs.github.io.Rproj          : RStudio project file 
│   index.Rmd                             : Markdown file with workflow overview
│   index.html                            : html file derived from markdown
│

```

### How to run the workflow code in your local computer
***


1. Sign in into your GitHub account [here](https://github.com/). 

2. To copy the repository to your profile, go to the search tab at the top of the screen and type dLinero-KBAs/dlinero-KBAs.github.io

![](methods/howto_step1.jpg)

4. Click on the repository

5. Click the fork button in the right corner.

![](methods/howto_step5.jpg)

6. If you want to open or modify the files and run the code in your local computer, open the GitHub Desktop software. 

7. If this is your first time opening the software, it will ask you to sign into your GitHub account. Once done, select the Locating KBAs repository and click the clone button at the bottom.

![](methods/howto_step7.jpg)

8.  In the pop-up window, select GitHub.com and set the folder where you want to save all the files that are in the repository.

![](methods/howto_step8.jpg)

9. Select clone

10. After the GitHub desktop finishes cloning the files to your local computer, select show in explorer to open the folder where the files were saved.

![](methods/howto_step10.jpg)

11. Open the dlinero-KBAs.github.io RStudio project. In the lower right corner,  select Notebook.Rmd to open the Rmarkdown file.

![](methods/howto_step11.jpg)

12. Now you are ready to modify the script and run it!


### Additional resources
***

Introductory video: [https://youtu.be/oesnhDeYpHQ](https://youtu.be/oesnhDeYpHQ)

### Citation
***

Linero D (2021) Locating KBAs: An automated workflow for identifying potential Key Biodiversity Areas. [https://github.com/dLinero-KBAs/dlinero-KBAs.github.io](https://github.com/dLinero-KBAs/dlinero-KBAs.github.io)

### Contact
***

Feel free to email me at daniela.linero@audubon.org

[ResearchGate profile](https://www.researchgate.net/profile/Daniela-Linero)

[LinkedIn profile](https://www.linkedin.com/in/daniela-linero/)

### References
***

* Gueta, T., Carmel, Y (2016). Quantifying the value of user-level data cleaning for big data: A case study using mammal distribution models. Ecological Informatics, 34, 139-145. https://doi.org/10.1016/j.ecoinf.2016.06.001

* IUCN (2016). A Global Standard for the Identification of Key Biodiversity Areas, Version 1.0. First edition. Gland, Switzerland: IUCN.

* KBA Standards and Appeals Committee (2020). Guidelines for using A Global Standard for the Identification of Key Biodiversity Areas. Version 1.1. Prepared by the KBA Standards and Appeals Committee of the IUCN Species Survival Commission and IUCN World Commission on Protected Areas. Gland, Switzerland: IUCN. viii + 206 pp.