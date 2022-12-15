# Phylogenetic Biology - Final Project

# Transitions in Plethodontidae Scapula Morphology

## Introduction and Goals

For my final project, I plan to focus on salamanders in the family Plethodontidae. This family exhibits two feeding types, both of which involve tongue projection: muscle-powered feeding and spring-powered feeding. Spring-powered or ballistic tongue projection, which relies on stored elastic energy, is comparatively more forceful than muscle-powered feeding (Scales 2020). In addition to these two feeding classes, some salamanders perform a forward lunge in tandem with tongue projection (Wake & Deban 2000). It is hypothesized that this forward lunge may provide additional power or accuracy to tongue projection, but this has not yet been confirmed.

I spent the summer working in the Peabody Collections studying preserved salamander specimens. My research was focused on salamander forelimb architecture. I predicted that muscle-powered feeders may have forelimb structure that is better-optimized for forward lunges. In this sense, the forward lunge may be a compensatory mechanism for less powerful feeders.

To visualize differences in forelimb skeletal structure, I segmented ~20 different taxa within the family. Specifically, I focused on the scapula, humerus, radius, and ulna. To quantify differences in trait values, I plan to eventually use a geometric morphometrics program developed by Dr. Zachary Morris. For this investigation, I will be using linear measurements of different features along the scapulae. Therefore, I will be using my own data.

The goal of my project is to determine how forelimb morphology has evolved in Plethodontidae salamanders. I will use PGLS analysis to assess the correlation of feeding mode with scapula shape in lungless salamanders. Specifically, I will be considering the acromion and coracoid processes, two features that vary between scapulae.

Ultimately, I would like to compare the evolutionary transition of forelimb morphology to the appearance of ballistic or muscle-powered feeding. With this comparison, it may become evident if natural selection is acting on optimized forelimb morphology for muscle-powered feeders, making the weakest feeders the best lungers.

This is part of a larger project that I will present at SICB 2023.

## Methods

*Data Collection*

My scapula data was obtained from Morphosource. I requested approximately 20 CT scans of different *Plethodontidae* species from museum collections across the country. After obtaining the .tiff files from collections managers, I refined the scans and isolated the species’ right pectoral girdles. Using Volume Graphics Studio (VG Studio), I spent the summer of 2022 segmenting the scapulae, humeri, radii, and ulnarae of the 20 specimens. I extracted the meshes of the scapulae as 3D objects. These extractions are digital replicas of the scapulae, which can then be compared across species.


![Untitled](https://user-images.githubusercontent.com/90157894/207922956-ee0e650c-7643-4889-b0b3-f9d6f7240cca.png)

**Figure 1:** The 3D mesh of the scapula of *Aneides lugubris*, a muscular feeder.


![image](https://user-images.githubusercontent.com/90157894/207924377-5780050b-0b6e-45d0-ae05-dfbeac0f26f3.png)

**Figure 2:** The 3D mesh of the scapula of *Ensatina eschscholtzii*, a ballistic feeder.


After extracting the meshes, I used the program Blender to measure linear features along the surface of the scapula. In particular, I focused on the acromion process and the coracoid process, which are both major sites of muscle attachment in amphibians (INSERT SOURCE HERE – GOOGLE IT, IT’S THE OLD ONE). Because skeletal attachment sites can reflect the size of the muscle(s) to which they’re attached, these varying surfaces provide an excellent proxy for assessing lunging capacity.


![Untitled-labeled features](https://user-images.githubusercontent.com/90157894/207926424-5ea666fe-bbc9-4a3e-90b3-501e8265817e.png)

**Figure 3:** The scapula of *Aneides lugubris* in the Blender interface. The acromion process and coracoid process are labeled. 


I used three variables to summarize the shape of the acromion-coracoid projection: “length”, “angle”, and “distance”. “Length” refers to the length of the acromion process, measured from origin to tip. “Angle” refers to the approximate angle formed by the acromion process and coracoid process. This angle does not include any flaring or tapering that appears at the end of the processes. Lastly, “distance” describes the length of the space between the tip of the acromion process and the tip of the coracoid process. Therefore, it includes information about flaring that is not described by the “angle” variable.

I also incorporated the variable “proportion”, which is the value of “distance” divided by “length”. It is designed to assess the width of the entire acromion-coracoid projection relative to the length of the acromion. 

The variable of feeding mode was included binarily, such that a value of "0" indicates ballistic feeding and "1" indicates muscular feeding.


[INSERT IMAGE HERE]

**Figure 4:** The scapula of *Aneides lugubris* in the Blender interface. The “length”, “angle”, and “distance” variables are labeled.


Though some amphibian research has described the role of the pectoral girdle in skeletal or muscular function, few studies have focused on *Caudata* specifically. The variables selected to describe scapula variation in this study were chosen based on observation of shape variation in *Plethodontidae*. Additionally, the acromion and coracoid have been linked to trapezium and XXXXX muscular function in *Rana*, hinting at a similar function for lungless salamanders.


*Tree Mapping*

In order to trace evolution within the *Plethodontidae* family, I decided to select an amphibian phylogeny from the scientific literature and prune it for my species of interest. To this end, I used an amphibian tree of life created by Pyron & Jetz (2018) (**Figure 5**). I limited my total number of segmented specimens to the species that were included in the tree, which left me with 18 tips (**Figure 6**).


![image](https://user-images.githubusercontent.com/90157894/207920620-490ec27b-0478-46ca-9b21-517092195cfe.png)

**Figure 5**: The complete amphibian tree of life (Pyron & Jetz, 2018)


![image](https://user-images.githubusercontent.com/90157894/207946802-90770cb2-6f22-44df-bea6-61eb3ec93df3.png)

**Figure 6**: Pruned, unrooted amphibian tree of life, showing only the 18 species of interest (Pyron & Jetz, 2018)


*Phylogenetic Methods*

By combining the pruned *Plethodontidae* phylogeny with continuous trait data, I hope to:

1. *Plot variation in scapula scalar data on the tips of a phylogeny*: I will use the package "ggplot2" to plot continuous scapula traits onto a known phylogeny to visually assess patterns between feeding mode and scapula shape.

2. *Use phylogenetic generalized least-squares analysis to determine the correlation between feeding mode and various scapula features*: I will use the packages "nlme" and "geiger" to perform PGLS analyses on feeding mode as it correlates to scapula shape and size.


## Results

*Aim One*

In order to plot scapula variation along a phylogeny, I began with a vector establishing my species of interest (**Figure 7**). I sampled 9 muscular feeders and 9 ballistic feeders. I mapped this variation in feeding mode onto the pruned tree; blue dots indicate muscle-powered feeders, while orange dots indicate ballistic feeders (**Figure 8**).


![image](https://user-images.githubusercontent.com/90157894/207950193-dece324f-993a-4dbc-bc89-2192602a3e55.png)

**Figure 7**: The vector *Plethodontidae*, which includes 18 species of interest (all of which belong to the lungless salamanders).


![image](https://user-images.githubusercontent.com/90157894/207950744-c2a69795-9df6-4d7c-8587-17cfa512f4ad.png)

**Figure 8**: Feeding mode plotted onto the pruned amphibian tree (Pyron & Jetz, 2018). Blue dots indicate muscular feeders and orange dots indicate ballistic feeders.







## Discussion

These results indicate...

The biggest difficulty in implementing these analyses was...

If I did these analyses again, I would...

## References

