---
layout: posts
author: kyla
---

# How variability can masquerade as uncertainty: representation errors in satellite salinity measurements

The launch of the [SMOS](http://www.esa.int/Applications/Observing_the_Earth/SMOS) (2009), [Aquarius](https://aquarius.nasa.gov/) (2011) and [SMAP](https://www.nasa.gov/smap) (2015) satellites heralded a new era of oceanographic observation: salinity measurements from space. Previously, salinity was only measured in situ, most broadly through the global network of [Argo floats](http://www.argo.ucsd.edu/) that began sampling in the early 2000s. Although the Argo program radically increased the observation of ocean salinity, Argo floats nominally make one measurement per 3 degrees longitude x 3 degrees latitude every 10 days, with few Argo floats in polar and coastal oceans and in marginal seas. Salinity satellites are thus a valuable complement to the Argo network, providing weekly global maps with ~1 degree horizontal resolution, and have provided unprecedented measurements of global surface salinity variability, enabling a better understanding of [ocean variability and climate phenomena](https://www.frontiersin.org/articles/10.3389/fmars.2019.00243). The satellite salinity community has undertaken a significant effort to validate measurements from these new sensors, and continues to do so in order to refine algorithms and improve the accuracy and resolution of salinity products. Much of the validation is done by comparing salinity measurements from satellites and those from Argo floats. While this approach seems fairly straightforward, two major factors complicate the satellite-in situ comparisons: vertical and horizontal gradients in salinity. These both lead to representation errors, which are differences in what satellite and in situ measurements represent rather than errors in what the sensors measure. Representation errors are important to distinguish from measurement errors when assessing the uncertainty of the satellite measurements. In this post, I want to introduce the concept of representation errors, describe how they are distinct from other types of errors, and suggest some strategies for handling them.

L-band (~1.4 GHz frequency) radiometers measure salinity by exploiting the fact that the emissivity of seawater at that frequency is related to its salinity (as well as its temperature). The L-band passive radiometers used to measure salinity from space sample the ocean at around 1 cm depth, whereas the shallowest Argo measurements are typically at 1 to 5 m depth. In a well-mixed ocean, it&#39;s safe to assume that the salinity at these two depths is the same so the measurements can be compared directly. However, rain falling on the ocean can produce near-surface fresh layers (also called puddles or lenses) that can have substantially lower salinity than the water just beneath\*:

![vertical salinity profile under rain](/blog/images/salinity-profile-under-rain.png)

*Vertical profile of salinity within a rain-formed fresh layer: the satellite salinity measurement, made at ~1 cm depth, is fresher than an Argo measurement made at ~1-5 m depth. (Adapted from Boutin et al., 2015.)*

This means that satellite salinity measurements in rainy regions can be systematically fresher than the 5-m salinity measured by Argo floats. This is particularly the case in regions with low wind speeds (e.g., the intertropical convergence zone), where upper ocean mixing is low and rain-formed fresh layers can persist for tens of hours. This makes the satellite salinity measurements appear to have a fresh bias, when in fact they just represent a different depth. In other words, these apparent errors in the satellite data are not actually errors at all. Understanding where and when surface fresh layers are present has thus become an important part of understanding how much of the satellite-in situ salinity differences are due to measurement errors versus sampling differences.

The horizontal variability of salinity adds another complication. The signal measured by a satellite radiometer is effectively a weighted spatial average over a footprint that is ~40 to 100 km across (depending on the satellite), and is compared to a point measurement from an Argo float that has popped up at random somewhere within that footprint. In regions with a lot of horizontal salinity variability, it is probable that an Argo float will sample at a location that does not represent the average salinity over the footprint. This is demonstrated by the following image, which shows a map of surface salinity in the California Current taken from a high-resolution model, with an example satellite footprint and two example Argo floats superimposed:

![sub-footprint-scale salinity variability](/blog/images/SSS_footprint_small.png)

*Sea surface salinity from the MITgcm llc4320 model simulation (courtesy of Dimitris Menemenlis) with an example satellite footprint shown as a black ellipse. Argo floats sampling at the location of the white or red dots would have very different salinities, neither of which would represent the salinity measured by the satellite.*

In this case, there is a strong mesoscale front through the middle of the satellite footprint, so an Argo float sampling at a random location within the footprint would appear to be measuring a different value than the satellite. River plumes, melting ice, ocean currents and instabilities, and rainfall can all generate surface salinity variability on horizontal scales smaller than one satellite radiometer footprint. As in the case of vertical salinity gradients, this can lead to differences between the satellite and in situ salinities that might be interpreted as uncertainty – but is in fact a mismatch in the scales of the two measurements being compared.  While here we have focused on the case of salinity, these types of representation errors are an issue for comparing any remotely sensed and in situ measurements, for instance [sea surface temperature](https://www.ghrsst.org/wp-content/uploads/2016/10/SSTDefinitionsDiscussion.pdf), winds over the ocean, surface currents, [wave heights](https://journals.ametsoc.org/jtech/article/24/9/1665/2940/Error-Estimation-of-Buoy-Satellite-and-Model-Wave), etc.

So, what are some strategies for handling representation errors in satellite validation efforts?

1. Use models or observations to estimate the contribution of sampling differences to satellite/in-situ comparisons. For instance, d&#39;Addezzio et al. (2019) used high-resolution model output to estimate the surface salinity variability on scales smaller than the satellite footprint; Drushka et al. (2019) used in situ salinity observations from ships to assess how much this sub-footprint-scale variability contributes to uncertainties in satellite measurements. Santos-Garcia et al. (2014) developed a &quot;rain impact model&quot; to predict the vertical salinity gradients due to rain; these estimates are now provided as part of the [Aquarius satellite salinity product](https://podaac.jpl.nasa.gov/dataset/AQUARIUS_L2_SSS_CAL_V5).

2. Develop protocols for matching up satellite &amp; in situ measurements, so that the match-up statistics can be done consistently across datasets and platforms. The [Salinity PiMEP](https://www.salinity-pimep.org/) effort aims to do this for salinity by compiling data from numerous in situ and satellite salinity products and allowing users to compute statistics through an interactive website.

3. Provide uncertainty estimates on satellites products (e.g., due to uncertainties in corrections for sea surface temperature and roughness; atmospheric, ionospheric, and galactic signals; and satellite navigation, among others). Meissner et al., (2018) separate these into systematic (fluctuate on time scales \&gt;1 month and spatial scales \&gt;100 km) and random (shorter time and length scales) components. Such uncertainty estimates are independent of Argo or other in situ data, and thus enable users to quantify how much of satellite-in situ differences are expected from instrument noise and measurement errors. The [Aquarius salinity product](https://podaac.jpl.nasa.gov/dataset/AQUARIUS_L2_SSS_CAL_V5) comes with separated estimates of random and systematic uncertainty; [SMOS](https://sextant.ifremer.fr/record/12dba510-cd71-4d4f-9fc1-9cc027d128b0/) and [SMAP](https://www.sciencedirect.com/science/article/abs/pii/S0034425718302517) come with total uncertainty estimates.

4. When presenting data from the upper few meters of the ocean, explicitly state the measurement (or model) depth rather than simply labeling them as surface data, which can be misleading when near-surface vertical gradients are present.

\*In typical fresh lenses, salinity at 1 cm depth is on order 0.1 to 1 psu fresher than at 5 m depth… but during the [SPURS-2 experiment](https://ourocean3.jpl.nasa.gov/spurs2/index.php), we observed a surface freshening of 10 psu during very heavy rain, low wind conditions!



**References:**

Boutin J, Chao Y, Asher WE, Delcroix T, Drucker R, Drushka K, et al. Satellite and In Situ Salinity: Understanding Near-Surface Stratification and Subfootprint Variability. Bull Amer Meteor Soc. 2015 Dec 16;97(8):1391–407.

D&#39;Addezio JM, Bingham FM, Jacobs GA. Sea surface salinity subfootprint variability estimates from regional high-resolution model simulations. Remote Sensing of Environment. 2019 Nov 1;233:111365.

Drushka K, Asher WE, Sprintall J, Gille ST, Hoang C. Global Patterns of Submesoscale Surface Salinity Variability. J Phys Oceanogr. 2019 Apr 25;49(7):1669–85.

Meissner T, Wentz FJ, Le Vine DM. The Salinity Retrieval Algorithms for the NASA Aquarius Version 5 and SMAP Version 3 Releases. Remote Sensing. 2018 Jul;10(7):1121.

Santos-Garcia A, Jacob MM, Linwood Jones W. Near-surface salinity stratification observed by SMOS under rainy conditions. In: Geoscience and Remote Sensing Symposium (IGARSS), 2015 IEEE International. 2015. p. 117–20.
