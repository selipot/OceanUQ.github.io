---
layout: posts
author: Kyla
title: How variability can masquerade as uncertainty: representation errors in satellite salinity 
---

The launch of the SMOS (2009), Aquarius (2011) and SMAP (2015) satellites heralded a new era of oceanographic observation: salinity measurements from space. These satellites have provided an unprecedented view of surface salinity variability, enabling a better understanding of the climate phenomena including the global water cycle, river outflow, large-scale coupled air-sea phenomena such as El Nino and the Madden-Julian Oscillation, and more.

The satellite salinity community has undertaken a significant effort to validate measurements from these new sensors, and continues to do so in order to refine algorithms and improve the accuracy and resolution of salinity products. The majority of satellite salinity validation is done by making statistical comparisons between salinity measurements from satellites and those from Argo floats. While this approach seems fairly straightforward, two major factors complicate the satellite-in situ comparisons: vertical and horizontal gradients. These both lead to representation errors, which are important to distinguish from measurement errors. 

First, the L-band (~1.413 GHz frequency) radiometers used to measure salinity from space sample the ocean at around 1 cm depth, whereas the shallowest Argo measurements are typically at made 1 to 5 m depth. In a well-mixed ocean, it’s safe to assume that the salinity at these two depths is the same so the measurements can be compared directly. However, rain falling on the ocean can produce near-surface fresh layers (also called puddles or lenses) that can have substantially lower salinity than the water just beneath*:

[]
(Adapted from Boutin et al., 2015.)


This means that a satellite salinity measurements in rainy regions, particularly those with low winds (e.g., the intertropical convergence zone), can be systematically fresher than the 5-m salinity measured by Argo floats. This makes the satellite salinity measurements appear to have a fresh bias, when really the relatively fresh satellite values are a result of how the signals being compared are measured. 


A second complication in comparing satellite and in situ measurements arises from the horizontal variability of salinity. The signal measured by a satellite radiometer is effectively a weighted spatial average over a footprint that is ~40 to 100 km across, and is compared to a point measurement from an Argo float that has popped up somewhere within that footprint.  As illustrated by the schematic below (adapted from Bingham, 2019), in regions with a lot of horizontal salinity variability it is probable that the Argo float will sample at a location that does not represent the mean salinity within the footprint. For instance, river plumes, melting ice, ocean currents and instabilities, and rainfall can generate surface salinity variability on horizontal scales smaller than one satellite radiometer footprint. This can lead to differences between the satellite and in situ salinities that might be interpreted as uncertainty –  but is in fact a mismatch in the scales of the two measurements being compared. 

So, what are some strategies for handling repreentation errors in satellite validation efforts?

1. use models or observations to estimate the contribution of sampling differences to satellite/in-situ comparisons. For the case of salinity, this has been done by several authors to estimate sub-footprint-variability (e.g., d’Addezzio  et al., 2019; Drushka et al., 2019) and vertical salinity gradients due to rain (e.g., Santos-Garcia et al., 2014).

2. Develop protocols for matching up satellite & in situ measurements, so that the match-ups statistics are done consistently across datasets and platforms. The “Salinity PiMEP” effort aims to do this for salinity. 

3. Provide uncertainty estimates on satellites products based on uncorrectable instrument noise and other known errors. The Aquarius salinity product comes with separated estimates of random and  systematic uncertainty; SMOS and SMAP come with total uncertainty estimates.  

4. When presenting data from the upper few meters of the ocean, explicitly state the measurement (or model) depth rather than simply labeling them as surface data, which can be misleading when near-surface vertical gradients are present.
