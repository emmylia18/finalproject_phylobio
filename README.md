
# Transitions in Plethodontidae Scapula Morphology

## Introduction and Goals

For my project, I plan to focus on salamanders in the family Plethodontidae. This family exhibits two feeding types, both of which involve tongue projection: muscle-powered feeding and spring-powered feeding (Lombard & Wake, 1976). Spring-powered or ballistic tongue projection, which relies on stored elastic energy, is comparatively more forceful than muscle-powered feeding (Scales 2020). In addition to these two feeding classes, some salamanders perform a forward lunge in tandem with tongue projection (Wake & Deban 2000). It is hypothesized that this forward lunge may provide additional power or accuracy to tongue projection. Some studies have explored the morphology involved in salamander jumping, but the adaptive benefit of the feeding lunge has not yet been confirmed (Ryerson, 2013; Hessel & Nishikawa, 2017).

I spent the summer of 2022 working in the Peabody Collections studying preserved salamander specimens. My research was focused on salamander forelimb architecture. I predicted that muscle-powered feeders may have forelimb structure that is better-optimized for forward lunges. In this sense, the forward lunge may be a compensatory mechanism for less powerful feeders.

To visualize differences in forelimb skeletal structure, I segmented ~20 different taxa within the family. Specifically, I focused on the scapula, humerus, radius, and ulna. To quantify differences in trait values, I plan to eventually use a geometric morphometrics program developed by Dr. Zachary Morris. For this investigation, I will be using linear measurements of different features along the scapulae.

The goal of my project is to determine how forelimb morphology has evolved in Plethodontidae salamanders. I will use PGLS analysis to assess the correlation of feeding mode with scapula shape in lungless salamanders. Specifically, I will be considering the acromion and coracoid processes, two features that vary between scapulae (McGonnell, 2001).

Ultimately, I would like to compare the evolutionary transition of forelimb morphology to the appearance of ballistic or muscle-powered feeding. With this comparison, it may become evident if natural selection is acting on optimized forelimb morphology for muscle-powered feeders, making the weakest feeders the best lungers.

This is part of a larger project that I presented at SICB 2023.

## Methods

*Data Collection*

My scapula data was obtained from Morphosource. I requested approximately 20 CT scans of different *Plethodontidae* species from museum collections across the country. After obtaining the .tiff files from collections managers, I refined the scans and isolated the species’ right pectoral girdles. Using Volume Graphics Studio (VG Studio), I spent the summer of 2022 segmenting the scapulae, humeri, radii, and ulnarae of the 20 specimens. I extracted the meshes of the scapulae as 3D objects. These extractions are digital replicas of the scapulae, which can then be compared across species.


![Untitled](https://user-images.githubusercontent.com/90157894/207922956-ee0e650c-7643-4889-b0b3-f9d6f7240cca.png)

**Figure 1:** The 3D mesh of the scapula of *Aneides lugubris*, a muscular feeder.


![image](https://user-images.githubusercontent.com/90157894/207924377-5780050b-0b6e-45d0-ae05-dfbeac0f26f3.png)

**Figure 2:** The 3D mesh of the scapula of *Ensatina eschscholtzii*, a ballistic feeder.


After extracting the meshes, I used the program Blender to measure linear features along the surface of the scapula. In particular, I focused on the acromion process and the coracoid process, which are both major sites of muscle attachment in amphibians (Howell, 1935; McGonnell, 2001; Keeffe et al., 2022). Because skeletal attachment sites can reflect the size of the muscle(s) to which they’re attached, these varying surfaces provide an excellent proxy for assessing lunging capacity. All scapulae were introduced to VG Studio and Blender with size information, such that their relative sizes have not changed. Therefore, the scalar measurements retrieved from Blender are unitless.


![Untitled-labeled features](https://user-images.githubusercontent.com/90157894/207926424-5ea666fe-bbc9-4a3e-90b3-501e8265817e.png)

**Figure 3:** The scapula of *Aneides lugubris* in the Blender interface. The acromion process and coracoid process are labeled. 


I used three variables to summarize the shape of the acromion-coracoid projection: “length”, “angle”, and “distance”. “Length” refers to the length of the acromion process, measured from origin to tip. “Angle” refers to the approximate angle formed by the acromion process and coracoid process. This angle does not include any flaring or tapering that appears at the end of the processes. Lastly, “distance” describes the length of the space between the tip of the acromion process and the tip of the coracoid process. Therefore, it includes information about flaring that is not described by the “angle” variable. I measured the SVL of each specimen in Blender to account for body size, then divided each linear variable by the specimen's SVL.

The variable of feeding mode was included binarily, such that a value of "0" indicates ballistic feeding and "1" indicates muscular feeding.


![Untitled-labeled variables](https://user-images.githubusercontent.com/90157894/208000172-a1a4b654-6eda-428f-86de-d97ad10d0269.png)

**Figure 4:** The scapula of *Aneides lugubris* in the Blender interface. The “length”, “angle”, and “distance” variables are labeled.


Though some amphibian research has described the role of the pectoral girdle in skeletal or muscular function, few studies have focused on *Caudata* specifically. The variables selected to describe scapula variation in this study were chosen based on observation of shape variation in *Plethodontidae*. Additionally, the acromion and coracoid have been linked to trapezium and deltoid muscular function in *Rana*, hinting at a similar function for lungless salamanders (Howell, 1935; McGonnell, 2001).


*Tree Mapping*

In order to trace evolution within the *Plethodontidae* family, I decided to select an amphibian phylogeny from the scientific literature and prune it for my species of interest. To this end, I used an amphibian tree of life created by Jetz & Pyron (2018) (**Figure 5**). I limited my total number of segmented specimens to the species that were included in the tree, which left me with 18 tips (**Figure 6**).


![image](https://user-images.githubusercontent.com/90157894/207920620-490ec27b-0478-46ca-9b21-517092195cfe.png)

**Figure 5**: The complete amphibian tree of life (Jetz & Pyron, 2018)


![image](https://user-images.githubusercontent.com/90157894/207946802-90770cb2-6f22-44df-bea6-61eb3ec93df3.png)

**Figure 6**: Pruned, unrooted amphibian tree of life, showing only the 18 species of interest (Jetz & Pyron, 2018)


*Phylogenetic Methods*

By combining the pruned *Plethodontidae* phylogeny with continuous trait data, I hope to:

1. *Plot variation in scapula scalar data on the tips of a phylogeny*: I will use the package "ggplot2" to plot continuous scapula traits onto a known phylogeny to visually assess patterns between feeding mode and scapula shape.

2. *Use phylogenetic generalized least-squares analysis to determine the correlation between feeding mode and various scapula features*: I will use the packages "nlme" and "geiger" to perform PGLS analyses on feeding mode as it correlates to scapula shape and size. I will use a maximum likelihood model for the PGLS, and assume Brownian motion for evolution.


## Results

*Aim One*

In order to plot scapula variation along a phylogeny, I began with a vector establishing my species of interest (**Figure 7**). I sampled 9 muscular feeders and 9 ballistic feeders. I mapped this variation in feeding mode onto the pruned tree; blue dots indicate muscle-powered feeders, while orange dots indicate ballistic feeders (**Figure 8**).


![image](https://user-images.githubusercontent.com/90157894/207950193-dece324f-993a-4dbc-bc89-2192602a3e55.png)

**Figure 7**: The vector *Plethodontidae*, which includes 18 species of interest (all of which belong to the lungless salamanders).


![image](https://user-images.githubusercontent.com/90157894/207950744-c2a69795-9df6-4d7c-8587-17cfa512f4ad.png)

**Figure 8**: Feeding mode plotted onto the pruned amphibian tree (Jetz & Pyron, 2018). Blue dots indicate muscular feeders and orange dots indicate ballistic feeders.


Next, I plotted the variables that describe scapula shape onto the tree. This includes "length" (**Figure 9**), "angle" (**Figure 10**), and "distance" (**Figure 11**). The "length" variable does not vary much along the phylogeny, though slightly larger length values seem characteristic of muscle-powered feeders. The "angle" variable does not change in a discernable way with feeding mode. *Bolitoglossa mexicana* has an exceptionally large angle, with a value over 100, compared to the other taxa. The "distance" variable also seems to skew slightly larger for the muscle-powered feeders.

![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/e36a41c0-f523-4a0d-9d98-51a6967a23aa)

**Figure 9**: The length of the acromion process ("length") versus feeding mode.


![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/1f0ed478-d790-456c-a1a8-21f86d44aa91)

**Figure 10**: The angle between the acromion process and the coracoid process ("angle") versus feeding mode.


![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/0c14f1d5-a63d-49b1-bab7-d777976ef7c9)

**Figure 11**: The distance between the tips of the acromion process and the coracoid process ("distance") versus feeding mode.


*Aim Two*

None of the three variables are significantly different across species when performing a PGLS analysis.


![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/53698292-5332-46fa-8349-d56fc69eaaf4)

**Figure 12**: The PGLS analysis of "length" and "feedingtype"


![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/acbf8c78-1cf7-47ee-9b77-4cbd938dc647)

**Figure 13**: The PGLS analysis of "distance" and "feedingtype"


![image](https://github.com/emmylia18/finalproject_phylobio/assets/90157894/a7604748-622c-4f3c-a733-48d2ceb83b46)

**Figure 14**: The PGLS analysis of "angle" and "feedingtype"



## Discussion

These results indicate a strong relationship between feeding mode and the scapula shape across length, distance, and angle. Based on the pruned tree with these variables plotted onto it, muscle-powered feeders tend to have narrower values of all three variables - they have more consistent acromion processes and distances between the tips of the acromion and coracoid proceses. These findings seem to support the hypothesis that muscle-powered feeders are better-adapted for lunging; some selective pressure may be acting on the shape of the scapula to lead to higher consistency between species.

None of the PGLS analysis yielded statistically significant results. However, after viewing the violin plots developed through Aim 1, this begins to make more sense. Rather than establishing a difference in the mean of these values according to feeding mode, the main difference appears to be through variation - ballistic feeders exhibit far more variation in scapula shape than muscle powered feeders (Fig. 

The biggest difficulty in implementing these analyses was, by far, formatting my data to work with the chosen packages. Throughout this project, I oscillated between using 3D landmark coordinates and scalar measurements of shape. I chose to use the scalar measurements for practicality - the methodology was more established and straight-forward, and more resources were available for guidance. Once I formatted the data correctly, the project was (mostly) smooth sailing.

This project is, ultimately, still a work in progress. I presented these findings at SICB in January 2023, and I hope to eventually use Dr. Morrison's landmarking package, "alignR". Going forward, I want to focus on getting usable data that describes the overall shape of the scapula, and isn't limited to the acromion and coracoid processes. 

If I did these analyses again, I would incorporate more variables. I would love to have more information about other aspects of the pectoral girdle, for example, such as length or width of the long bones. I would also like to add more information about feeding itself - for example, does the type or mobility of prey impact lunging ability for lungless salamanders? Does scapula architecture correlate to the speed of prey? Ultimately, I would love to include more information that recenters the role of ecology. This is a very morphology-heavy investigation, and I want to emphasize that these aspects of physiology are not happening in a vacuum - that they occur in tandem with information about the environment, prey, predators, conspecifics, and other physiological features of the organism itself. If I could redo my investigation, I would emphasize the wide variety of constrains that could be influencing lunging capacity - beyond simply feeding mode.

## References

Hessel AL, Nishikawa KC (2017). The Hip-twist Jump: A Unique Mechanism for Jumping in Lungless Salamanders. J Herpetol 51(4): 461-467.

Howell AB (1935). Morphogenesis of the Shoulder Architecture: Part III: Amphibia. Q Rev Biol 10(4):397-431.

Jetz W, Pyron RA (2018). The interplay of past diversification and evolutionary isolation with present imperilment across the amphibian tree of life. Nat. Ecol. Evol 2:850-858.

Keeffe RM, Blob RW, Blackburn DC, Mayer CJ (2022). XROMM Analysis of Feeding Mechanics in Toads: Interactions of the Tongue, Hyoid, and Pectoral Girdle. Integ Org Biol 4(1).

Lombard RE, Wake DB (1976). Tongue Evolution in the Lungless Salamanders, Family Plethodontidae. J Morphol 148(3):265-286.

McGonnell IM (2001). The evolution of the pectoral girdle. J Anat 199:189-194. 

Paradis E, Schliep K (2019). “ape 5.0: an environment for modern phylogenetics and evolutionary analyses in R.” Bioinformatics 35:526-528.

Pennell M, Eastman J, Slater G, Brown J, Uyeda J, Fitzjohn R, Alfaro M, Harmon L (2014). “geiger v2.0: an expanded suite of methods for fitting macroevolutionary models to phylogenetic trees.” Bioinformatics 30:2216-2218.

Pinheiro J, Bates D, R Core Team (2022). nlme: Linear and Nonlinear Mixed Effects Models. R package version 3.1-161.

Ryerson WG (2013). Jumping in the Salamander Desmognathus ocoee. Copeia 3:512-516.

Scales J, Bloom SV, Deban SM (2020). Convergently evolved muscle architecture enables high-performance ballistic movement in salamanders. J Morphol 281:196-212. 

Wake D, Deban SM (2000). Terrestrial Feeding in Salamanders. FEEDING: 95-116.

Wickham H (2016). ggplot2: Elegant Graphics for Data Analysis. Springer-Verlag New York. ISBN 978-3-319-24277-4.

Xie Y (2022). knitr: A General-Purpose Package for Dynamic Report Generation in R. R package version 1.41.
