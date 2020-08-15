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

These visualizations give us a very good idea about how LBMP data behaves. Thus, we can now establish the parameters that will form the basis of our analysis.


# Quantitative Analysis

## Parameters

Our model parameters are as follows:

* $p$ : price per unit of carbon offsets (\$ / ton $CO_2$), constant 
* $c_t$ : cost of electric power in hour $t$ (\$ / MWh): changes each hour (LBMP)
* $\lambda$ : power consumed per carbon offset produced (MWh / ton $CO_2$), constant
- Hence $1/\lambda$ measures plant efficiency
* $N$ : plant maximum capture rate (ton $CO_2$/h), constant
* $t = 1, \ldots, T$ : index of hours in the calendar year ($T \approx 8260$ )

> Since our LBMP data is in 5 minute intervals, we apply our hourly calculation to each 5 minute LBMP and convert that into 5 minute revenue by multiplying by a factor of 5/60.

## Derived Quantities

  * $C_t = c_t \lambda N$ : total costs of power, if plant is operating at maximum capacity
  * $R_t = \max\{p-c_t \lambda, 0\}N$ : operating revenue in hour $t$, assuming optimal operations 

## Definitions:

  * *Operating net income*: Total revenues from carbon offsets less cost of power


# Assumptions

In our analysis, we assume stakeholders are compensated per ton of CO2 removed from the atmosphere. This may be a result of a policy set by state and local governments. We also assume that the plant is smart enough to cease operation when the LBMP of electricity would cause the plant to run at a loss and would run at maximum capacity otherwise. Additionally, we are assuming it is technically feasible to turn a DAC off and on, cheaply and easily.

# Methodology

This analysis was performed in a jupyter notebook and written in the python programming language. In order to perform our analysis we first had to calculate the revenur of a DAC facility for every 5 minutes of operation given LBMP. We define our parameters as follows. The parameter 'co_offset' is the price of carbon offsets per ton of CO2 captured and removed from the atmosphere. The parameter 'lmbda' is our lambda that corresponds to the power consumed per carbon offset produced (MWh/ton CO2). The parameter 'capacity' is the capacity of a plant in tons of CO2/hr. Finally, 'yr_op_expenses' represents the yearly operating expenses of a plant including the cost of employees, debts, and other fixed costs. We then define our revenue function that calculates the revenue of the facility for a given 5 minute LBMP. It does this by simply using the equation for revenue per hour and converts it into revenue per 5 minutes. Next, we calculated the revenues for the three locations for every LBMP of the year. 

```
co_offset = 100   # price in $ of carbon offsets per ton ($/Ton CO2)

lmbda = 2.5        # power consumed per carbon offset produced, MWh/ton CO2

capacity = 1       # plant capacity, tons CO2/hr

yr_op_expenses = 250000    # Yearly operating expenses

def RevenuePer5Mins(lbmp):
    rev_hr = (co_offset - (lbmp*lmbda))*capacity
    return (rev_hr/60.0) *5


genese_revs, dunwood_revs, central_revs = [], [], []

# calculate and collect revenues for the three locations.
for lbmp in genese["LBMP ($/MWHr)"]:
    genese_revs.append(RevenuePer5Mins(lbmp))
    
for lbmp in dunwood["LBMP ($/MWHr)"]:
    dunwood_revs.append(RevenuePer5Mins(lbmp))
    
for lbmp in central["LBMP ($/MWHr)"]:
    central_revs.append(RevenuePer5Mins(lbmp))
    
# Make dataframes of revenues for different locations with time stamps. 
genese_revs_df = pd.DataFrame(genese_revs, 
    index=genese.index, columns =['Revenue ($)'])
dunwood_revs_df = pd.DataFrame(dunwood_revs, 
    index=dunwood.index, columns =['Revenue ($)'])
central_revs_df = pd.DataFrame(central_revs, 
    index=central.index, columns =['Revenue ($)'])

```

Given this, we are now able to create dataframes from our revenue calculations and sum up our revenues for the three locations to get the Annual Operating Revenue factoring in the cost of power. In order to simulate an optimized DAC plant we removed all of the negative revenues from the dataframes. This falls in line with our assumption that the plant can shut off when the cost of power is too high to make a profit. For comparison the original unoptimized revenues are also saved so we can also asses the difference in revenues between an optimized and unoptimized plant.

```
# Make dataframes of revenues for different locations with time stamps. 
genese_revs_df = pd.DataFrame(genese_revs, 
    index=genese.index, columns =['Revenue ($)'])
dunwood_revs_df = pd.DataFrame(dunwood_revs, 
    index=dunwood.index, columns =['Revenue ($)'])
central_revs_df = pd.DataFrame(central_revs, 
    index=central.index, columns =['Revenue ($)'])

# Save original dataframes before removing negatives
genese_revs_og = genese_revs_df
dunwood_revs_og = dunwood_revs_df
central_revs_og = central_revs_df


print("Genese Revenues Preview:\n", genese_revs_df.head())
print("\n")

# Assuming we only run the DAC when the LBMP will create a 
# break even or profit we will remove all negative values
genese_revs_df = genese_revs_df[genese_revs_df['Revenue ($)'] > 0]
dunwood_revs_df = dunwood_revs_df[dunwood_revs_df['Revenue ($)'] > 0]
central_revs_df = central_revs_df[central_revs_df['Revenue ($)'] > 0]
```

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure7.png} \caption{Optimized Operating Revenues of Genese 2019 given LBMP} \end{figure}
\begin{figure}[H] \centering \includegraphics[scale=.6]{figure7u.png} \caption{Unoptimized Operating Revenues of Genese 2019 given LBMP} \end{figure}

# Results

# Value

# Conclusions

# Future Work

# Acknowledgements

I would like to acknowledge Dr. Small for a great summer course experience learning Time Series Analysis. I truly enjoyed the research and learned a lot from this class that will help me in my career. 

# References

[1] https://www.researchgate.net/profile/Mark_Workman2/publication/271581596_High-level_techno-economic_assessment_of_negative_emissions_technologies/links/59ed956daca272cddde06ee2/High-level-techno-economic-assessment-of-negative-emissions-technologies.pdf

[2] https://web.stanford.edu/group/efmh/jacobson/Articles/Others/19-CCS-DAC.pdf 

[3] https://www.sciencedirect.com/science/article/pii/S0959652619307772

[4] Adoption of the Paris Agreement—Proposal by the President United Nations Framework Convention on Climate Change Paris, France (2015)

[5] Chemical and Petrochemical Sector - Potential of Best Practice Technology and Other Measures for Improving Energy Efficiency
IEA information paper. OECD/IEA, Paris, September (2009)
Available at: [LINK](https://www.iea.org/publications/freepublications/publication/chemical_petrochemical_sector.pdf), Accessed 25th May 2018