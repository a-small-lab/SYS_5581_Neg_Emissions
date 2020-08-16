---
title: Optimizing the Profitability of DAC Facilities
subtitle: Project for University of Virginia SYS 5581 Summer 2020
author:  Dr. Arthur A. Small, David Hill, Jr. 
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

The goal of this paper is to introduce a data driven profitability analysis that will be the basis of a framework for establishing the economic viability of direct air capture facilities for major stakeholders. Direct air capture technology is a novel solution to remove harmful CO2 concentrations from the air. As it develops and matures it is likely that direct air capture (DAC) facilities will become more prevalent and thus it is necessary for them to be profitable for investors. One of the main costs of operation for such facilities is electricity which varies drastically and sporadically throughout the year. For an investor to make a profit with a DAC facility, the profits they make per unit of CO2 removed from the atmosphere must be greater than the electricity cost to capture that unit of CO2. Thus, our analysis will assess three energy generating regions and New York State and use the cost of electricity from those regions to derive the annual gross and net revenue for a DAC facility given parameters associated with profit per unit of CO2, cost of electricity, and amount of energy needed to capture a unit of CO2.

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

Figures 8 and 9 show the revenues of genese when optimized and unoptimized. We can see that the unoptimized version has spikes of negative revenue that will affect the annual operating revenues.

# Results
In this section we will discuss the results of our analysis. To obtain our results we took the sum of the revenues for each location for both the optimized and unoptimized dataframes. We calculated optimized and unoptimized net revenues by subtracting the expected annual expenses of the plant. As a result we were able to get a summary of potiential annual gross and net revenues of DAC facilities in three different regions of New York. The summary result is depicted in figures 10 and 11.

```
# Yearly Net Operating Revenue
genese_op_rev = genese_revs_df.sum()
dunwood_op_rev = dunwood_revs_df.sum()
central_op_rev = central_revs_df.sum()

#Yearly Net Operating revenue unoptimized
og_genese_rev = genese_revs_og.sum()
og_dunwood_rev = dunwood_revs_og.sum()
og_central_rev = central_revs_og.sum()

print("Genese Yearly Operating", genese_op_rev)
print("Genese Unoptimized Yearly Operating", og_genese_rev)
print("\n")

print("Dunwood Yearly Operating", dunwood_op_rev)
print("Dunwood Unoptimized Yearly Operating", og_dunwood_rev)
print("\n")

print("Central Yearly Operating", central_op_rev)
print("Central Unoptimized Yearly Operating", og_central_rev)
print("\n")

genese_net_rev = genese_op_rev - yr_op_expenses
dunwood_net_rev = dunwood_op_rev - yr_op_expenses
central_net_rev = central_op_rev - yr_op_expenses

# Unoptimized net revs
u_genese_net_rev = og_genese_rev - yr_op_expenses
u_dunwood_net_rev = og_dunwood_rev - yr_op_expenses
u_central_net_rev = og_central_rev - yr_op_expenses

print("Genese Net ", genese_net_rev)
print("Unoptimized Genese Net ", u_genese_net_rev)
print("\n")

print("Dunwood Net", dunwood_net_rev)
print("Unoptimized Dunwood Net", u_dunwood_net_rev)
print("\n")

print("Central Net", central_net_rev)
print("Unoptimized Central Net", u_central_net_rev)
```

\begin{figure}[H] \centering \includegraphics[scale=.6]{figure10.png} \caption{Summary of Annual Gross Operating Revenues 2019} \end{figure}
\begin{figure}[H] \centering \includegraphics[scale=.6]{figure11.png} \caption{Summary of Annual Net Revenues 2019} \end{figure}

Given the gross and net revenues for DAC's in different locations we can now make decisions based on this data. We observed that out of the three locations analyzed and the parameters given, the most profitable DAC location was Genese. This is whether an optimized DAC or unoptimized one is built. We also observed that despite optimization, a DAC facility can be profitable either way. We know this because when we compare our net and gross revenues for an optimized and unoptimized plant, there is not a large gap in revenues. Looking at optimized and unoptimized revenues is also beneficial because it provides stakeholders with a potiential maximum and minimum annual revenue for a given scenario.

# Value
This analysis is valuable as it provides the basis for further analysis of DAC profit potiential. It also serves as the basis for a framework to evaluate power generating regions for the development of DAC facilities. Investors in clean energy and emissions reduction would benefit from this analysis as it provides them a new potiential investment opportunity. This analysis is also beneficial for policy makers as it provides them a way of determinining how to incentivise the construction of DAC facilities for investors. 

# Conclusion
In summary, we have successfully derived the potiential annual gross and net revenues of DAC facilities in three different regions of New York. We found that given the locational marginal based price of electricity, we can determine the revenue per hour of a DAC facility based on its capacity and amount of power it consumes per unit of carbon offsets captured. We also discovered that a DAC facility can be profitable whether or not it is run optimally in the sense that the plant stops operating when it would operate at a loss. This analysis framework could be used to study other regions where electricity is generated to study the profit potiential of DAC facilities. The profitability of a DAC facility will largely be dependent on the parameters passed in. These parameters are based on technical capabilities of DAC technology and legislative policies that would make DAC facilities profitable. It is our hope that this research will lead to policy decisions that will support the implementation of DAC facilities and that investors will consider investing in negative emissions facilities.

# Future Work
This analysis could be expanded into a decision analysis tool in which stakeholders could run scenarios given their specific parameters to identify the most profitable locations to build DAC facilities. Investigation into further costs for running DAC facilities is also necessary to improve our net revenue calculations. A replication of this analysis with a dataset spanning several years could also prove beneficial to provide an outlook of DAC profitability over several years. This will enable stakeholders to determine the long term investment potiential of DAC facilities. Policy research should also be conducted to find out what price per ton of carbon captured is feasible. Regulations, construction, and financing costs should be further studied as well to provide a better idea of initial and annual costs. This would improve the model presented in this paper as well.

# Acknowledgements

I would like to acknowledge Dr. Small for a great summer course experience learning Time Series Analysis. I truly enjoyed the research and learned a lot from this class that will help me in my career. 

# References

[1] McGlashan, N., Shah, N., Caldecott, B., &amp; Workman, M. (2012, October 3). High-level Techno-economic Assessment of Negative Emissions Technologies. Retrieved August 7, 2020, from [LINK](https://www.researchgate.net/profile/Mark_Workman2/publication/271581596_High-level_techno-economic_assessment_of_negative_emissions_technologies/links/59ed956daca272cddde06ee2/High-level-techno-economic-assessment-of-negative-emissions-technologies.pdf)

[2] Jacobson, M. Z. (2019). The health and climate impacts of carbon captureand direct air capture. Energy &amp;EnvironmentalScience. Retrieved August 8, 2020, from https://web.stanford.edu/group/efmh/jacobson/Articles/Others/19-CCS-DAC.pdf

[3] Fasihi, M., Efimova, O., &amp; Breyer, C. (2019, March 14). Techno-economic assessment of CO2 direct air capture plants. Retrieved August 16, 2020, from https://www.sciencedirect.com/science/article/pii/S0959652619307772

[4] Adoption of the Paris Agreement—Proposal by the President United Nations Framework Convention on Climate Change Paris, France (2015)

[5] Chemical and Petrochemical Sector - Potential of Best Practice Technology and Other Measures for Improving Energy Efficiency
IEA information paper. OECD/IEA, Paris, September (2009)
Available at: [LINK](https://www.iea.org/publications/freepublications/publication/chemical_petrochemical_sector.pdf), Accessed 25th May 2018