---
title: Optimizing the Profitability of DAC Facilities
subtitle: Project for University of Virginia SYS 5581 Summer 2020
author: David Hill, Jr., Dr. Arthur A. Small 
date: August 7, 2020
papersize:
- a4
fontsize:
- 12pt
geometry:
- margin=1in
fontfamily:
- charter
header-includes:
- \setlength\parindent{24pt}
- \usepackage{float}
- \usepackage{placeins}
- \usepackage{graphicx}
- \graphicspath{ {./figures/} }
---

\maketitle
\pagenumbering{arabic}
\setcounter{page}{1}

# Abstract


# Introduction

As our environment increasingly feels the negative effects of of climate change, there is a critical need for innovative and profitable solutions that will help to reduce the effects of climate change. Carbon dioxide (CO2) is a persistent atmospheric gas, and it seems increasingly likely that concentrations of CO2 and other greenhouse gases in the atmosphere will over shoot targets of“safe” levels (e.g. the 450 ppm target set as the tolerable level of atmospheric concentration)[1].CO2 concentration in the atmosphere has rapidly increased from 280 ppm in the pre-industrial era to 403 ppm in 2016, with an annual growth rate of 2 ppm [5]. The Paris Agreement aims to mitigate climate change and keep temperature rise well below 2 °C and preferably 1.5 °C in comparison to the pre-industrial age by united efforts of all countries [4]. This has spurred many developed countries and organizations around the world to invest and research ways to generate energy without creating pollution using methods such as solar capture and off-shore eind turbines. Additionally, this initiative to reducing environmental CO2 pollution has led to the development of technologies with the goal of removing pollution from the atmosphere and safely and permanently disposing of it. These technologies are often are called Negative CO2 Emissions Technologies (NETs). A range of options are available for CO2 emissions removal [3]. CO2 emissions can be captured at point sources such as flue gases from conventional power plants or non-energetic sectors such as cement plants [3]. However, some plants are too old and cannot be retrofitted [3]. Moreover, even in plants with CO2 removal systems, not all emissions are captured as the average capture rates are in the range of 50–94% [3]. On the other hand, it is not possible to directly capture CO2 emissions produced by long-distance aviation and marine transport [3]. This highlights the need for sustainable solutions that can capture CO2 from the atmosphere without dependency on location or source of pollution. Trees and plants have accomplished the task of removing CO2 from the air since the beginning of life on the planet. However, with increasing deforestation and increasing CO2 pollution, natural plants and forestation cannot keep up with the increase in pollution. 

There are a few technologies that are used to accomplish the goal of CO2 removal. Aforestation, bioenergy with carbon capture and storage (BECCS) and enhanced weathering is one such technology. However, it lacks real commercial feasability and poses huge risks. Large-scale BECCS and afforestation threat biodiversity, water and food security, as both are characterised by huge land requirements [3]. Enhanced weathering provokes rising pH values in rivers and changing the chemistry in oceans [3]. Besides afforestation/reforestation, BECCS and enhanced weathering, the full portfolio of NETs also includes biochar, ocean fertilisation and soil carbon sequestration, which may have to be applied in a portfolio of NETs for effective climate change mitigation [3]. CO2 Direct Air Capture (DAC) is an alternative technology to BECCS. This technology removes CO2 from the atmosphere.  DAC is a relatively new and innovative technology in early commercial stages, which in a long term perspective, along with conventional technologies, can help humankind to control and mitigate climate change [3]. In this paper, we will mainly look at DAC facilities as the basis of an economic sustainability analysis. 

# Problem

For DAC to be a sustainable solution, it must be technically and economically sound. While, there is a lot of research studying the environmental effects and ways to improve CO2 DAC, there has been little analysis around the economic sustainability for the stakeholders of DAC facilities in the future. A lot of this will be driven by legislative policies and regulations that have yet to be defined. As this technology matures, state and local governments will greatly benefit from supporting the construction of DAC facilities. Thus, in our analysis we seek to determine the economic sustainability of DAC facilities given the costs associated with running such facilities. Moreover, we seek to define the basis of a framework that will allow stakeholders to identify the most profitable regions to build DAC facilities.

# Data

The data that we will use in our analysis comes from the New York Independent System Operator (NYISO) database that tracks real time locational based marginal price (LBMP) information about energy generation regions in New York. This data is an aggregate of the LBMP at every region in New York every five minute increment of the day for every day of 2019. The structure of our dataset is depicted in figure 1. Our data is time series, as the timestamps for each five minute increment of the year is taken into account.

\begin{figure}[h!] \centering \includegraphics[scale=.6]{figure0.png} \caption{NYISO LBMP Data Structure} \end{figure}

Since our analysis requires us to understand the characteristics of LBMP data, we plotted the LBMP for every day of the year for the locations, Genese, Central, and Dunwood. This is depicted in figures 3, 4 and 5.

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure1.png} \caption{LBMP of Genese for 2019} \end{figure}
 

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure2.png} \caption{LBMP of Dunwood for 2019} \end{figure}
 

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure3.png} \caption{LBMP of Central for 2019} \end{figure}

LBMP is extremely volatile and fluctuates between negative and extremely high values in an unpredictable fashion. The unpredictable and volatile nature of LBMP of electricity means that it is imperative that we optimize profitability by only running the DAC facility when profitable. It is also important to note that the LBMP of the three locations were all very similar throughout the year. This suggests that there may be a correlation between LBMP for different locations. When one location experiences a spike in LBMP so do the others. This may be a basis for further investigation and analysis.

To understand the distribution of the data we also plotted histograms of LBMP frequency for the locations Genese, Dunwood, and Central.

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure4.png} \caption{LBMP Frequency for Genese 2019} \end{figure}
 

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure5.png} \caption{LBMP Frequency for Dunwood 2019} \end{figure}
 

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure6.png} \caption{LBMP Frequency for Central 2019} \end{figure}



# Parameters

Here we define the parameters that form the basis of our analysis:

* $p$ : price per unit of carbon offsets (\$ / ton $CO_2$), constant 
* $c_t$ : cost of electric power in hour $t$ (\$ / MWh): changes each hour (LBMP)
* $\lambda$ : power consumed per carbon offset produced (MWh / ton $CO_2$), constant
- Hence $1/\lambda$ measures plant efficiency
* $N$ : plant maximum capture rate (ton $CO_2$/h), constant
* $t = 1, \ldots, T$ : index of hours in the calendar year ($T \approx 8260$ )


# Assumptions

In our analysis, we assume stakeholders are compensated per ton of CO2 removed from the atmosphere. This may be a result of a policy set by state and local governments. We also assume that the plant is smart enough to cease operation when the LBMP of electricity would cause the plant to run at a loss and would run at maximum capacity otherwise. 



# Methodology

# Results

# Value

# Conclusions

# Future Work

# Acknowledgements

# References

[1] https://www.researchgate.net/profile/Mark_Workman2/publication/271581596_High-level_techno-economic_assessment_of_negative_emissions_technologies/links/59ed956daca272cddde06ee2/High-level-techno-economic-assessment-of-negative-emissions-technologies.pdf

[2] https://web.stanford.edu/group/efmh/jacobson/Articles/Others/19-CCS-DAC.pdf 

[3] https://www.sciencedirect.com/science/article/pii/S0959652619307772

[4] Adoption of the Paris Agreement—Proposal by the President United Nations Framework Convention on Climate Change Paris, France (2015)

[5] Chemical and Petrochemical Sector - Potential of Best Practice Technology and Other Measures for Improving Energy Efficiency
IEA information paper. OECD/IEA, Paris, September (2009)
Available at: [LINK](https://www.iea.org/publications/freepublications/publication/chemical_petrochemical_sector.pdf), Accessed 25th May 2018