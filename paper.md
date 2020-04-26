---
title: '*dms-view*: Interactive visualization tool for deep mutational scanning experiments'
tags:
  - Javascript
  - D3
  - molecular biology
  - protein evolution
  - data visualization
authors:
  - name: Sarah K. Hilton*
    affiliation: "1, 2"
  - name: John Huddleston*
    affiliation: "3, 4"
  - name: Allison Black
    affiliation: "3, 5"
  - name: Khrystyna North
    affiliation: "1, 2"
  - name: Adam Dingens
    affiliation: 1
  - name: Trevor Bedford
    affiliation: 3
  - name: Jesse D. Bloom
    orcid: 0000-0003-1267-3408
    affiliation: "1, 2, 6"
affiliations:
  - name: Division of Basic Sciences and Computational Biology Program, Fred Hutchinson Cancer Research Center, Seattle, WA, USA
    index: 1
  - name: Department of Genome Sciences, University of Washington, Seattle, WA, United States of America
    index: 2
  - name: Vaccine and Infectious Disease Division, Fred Hutchinson Cancer Research Center, Seattle, WA, USA
    index: 3
  - name: Molecular and Cell Biology, University of Washington, Seattle, WA, USA
    index: 4
  - name: Department of Epidemiology, University of Washington, Seattle, Washington, United States
    index: 5
  - name: Howard Hughes Medical Institute, Seattle, Washington, USA
    index: 6
date: 22 April 2020
bibliography: paper.bib
---

# Summary and Purpose

One challenge when studying proteins is that the effect of amino-acid changes are idiosyncratic across the length of the gene [@echave2016causes].
However, recent technological developments in the form of a high-throughput functional assay called Deep Mutational Scanning (DMS) [@fowler2014deep], make it possible to experimentally measure the effect of all amino-acid mutations to a protein.
Over the past five years, this flexible assay has been used to study dozens of different proteins [@esposito2019mavedb] and answer a variety of research questions.
For example, DMS approaches have been used for protein engineering [@wrenbeck2017deep], understanding the human immune response to viruses [@lee2019mapping], and to potentially interpret human variation in a clinical setting [@starita2017variant; @gelman2019recommendations].
Accompanying this proliferation of DMS studies has been the development of software tools [@bloom2015software; @rubin2017statistical] and databases [@esposito2019mavedb] to standardize DMS analysis and facilitate data sharing.
However, the power of a DMS study is only fully leveraged when the experimental results are summarized, integrated, and visualized with other data, such the 3-D protein structure and natural sequence data.

Here we describe *dms-view* (https://dms-view.github.io/), a flexible, web-based, interactive visualization tool for deep mutational scanning experiments written in JavaScript and [D3](https://d3js.org).
*dms-view* links site-level and mutation-level results from a DMS to a 3-D protein structure.
The user can interactively select sites of interest to reveal the mutation-level details and view the sites on the protein structure.
*dms-view* tracks both the input data information and the user selections in the URL.
This allows the user to save their selections or send a specific view to collaborator.
Importantly, *dms-view* is designed with a flexible input data file so the user can display custom site- and mutation-level metrics and incorporate non-DMS data, such amino-acid frequencies in nature.

Users can access *dms-view* at https://dms-view.github.io.
The tool consists of a data section at the top and a description section at the bottom.
The data section displays the user specified data in three panels: the site plot panel, the mutation plot panel, and the protein structure panel (\autoref{fig:fig}A).
When sites are selected in the site plot panel, the individual mutation values are shown in the mutation plot panel below and highlighted on the protein structure to the right.
The description section is at the bottom of the page.
The user can use this section to explain the experimental setup, acknowledge data sources, hold notes about a particular analysis or another relevant information.

Please visit the documentation at https://dms-view.githubio/docs to learn more about how to use the tool, how to upload a new dataset, or view case studies.

# Example

## Mapping influenza A virus escape from human sera

Using a deep mutational scanning approach, @lee2019mapping measured the ability of every single amino-acid mutation in the Influenza Virus surface protein hemagglutinin to escape human sera.
For more information on the experimental setup, see the paper [@lee2019mapping] or the [GitHub repo](https://github.com/jbloomlab/map_flu_serum_Perth2009_H3_HA).

In this example, the conditions are the different human or ferret sera used for the selections.
The site- and mutation-level metrics are different summaries of [differential selection](https://jbloomlab.github.io/dms_tools2/diffsel.html), where higher values indicate more escape from the sera.

Lee and colleagues asked two questions in their paper which can be easily explored using *dms-view*.

  1. Are the same sites selected by sera from different people? (compare site-level and mutation-level metric values for specific sites between different conditions)
  1. Where on the protein structure are the highly selected sites located? (view sites on the protein structure)

### Comparing site-level and mutation-level metric values for specific sites between conditions

To address whether or not the same sites are selected by different human sera using *dms-view*, we selected the mostly highly targeted sites for the human sera condition "Age 21 2010" \autoref{fig:fig}A (144, 159, 193, and 222).
We then use the condition dropdown menu to toggle between the other sera.
The highlighted sites remain highlighted after the condition is changed so we can easily see if the same sites are targeted in other conditions.

In \autoref{fig:fig}B, we can see that three of the sites selected by the human sera "2010-age-21" are also targeted by the human sera "2009-age-53".
These data are the default data for *dms-view*, so to explore this question in more detail please see https://dms-view.github.io.

### View sites on the protein structure

To address where on the protein structure the targeted sites are located, we selected the most highly targeted sites (144, 159, 193, and 222) for the human sera condition "Age 21 2010" to highlight them on the protein structure.

In \autoref{fig:fig}A, we can see that these sites cluster on the "head" of the hemagglutinin, which is known to be a common target of the human immune system (cite).

# Code Availability

- dms-view is available at https://dms-view.github.io.
- Source code is available at https://github.com/dms-view/dms-view.github.io.
- Documentation (https://dms-view.github.io/docs) and case studies (https://dms-view.github.io/docs/casestudies/) are also available.

# Figures

![Using *dms-view* to analyze a real DMS. **(A)** The *dms-view* data section has three panels: the site plot, the mutation plot, and the protein structure plot. The interactive features for selecting sites and navigating are in the site plot panel. Here we show the five most highly targeted sites by the human sera "2010-Age-21" from the study by @lee2019mapping. All five sites fall on the ``head" influenza virus HA. **(B)** The same five sites targeted by the sera in panel **A** but now plotted with the data from a different human sera, "2009-age-53". Using *dms-view* to compare, we see that different sites on HA are targeted by the different sera. \label{fig:fig}](fig/fig.png)

# Acknowledgements

This work started as the final project for UW class CSE 512 Data Visualization as a part of the UW eScience Advanced Data Science Option curriculum and we would like to thank Dr. Jeffrey Heer, Halden Lin, and Jane Hoffswell for their input on the initial design.
Thank you to Bloom and Bedford lab members for their generosity providing feedback, data, and time for testing.
JDB is an Investigator of the Howard Hughes Medical Institute.

# References
