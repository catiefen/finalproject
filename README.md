[covariates.csv](https://github.com/user-attachments/files/18117878/covariates.csv)# Phylogenetic Biology - Final Project

## Guidelines - you can delete this section before submission

This is a stub for your final project. Edit/ delete the text in this readme as needed.

There are two ways you can use this document:  
- You can download this file to a folder on your computer, edit this document and add other files (data, code, etc), and then zip up and submit the folder on canvas.
- You can for the [repository](finalproject) containing this document on gitub. Then commit and push your canges to the repository, and submit a link to the repository on canvas.

Github is a great way to work on projects, but also has a steep initial learning curve.


Some guidelines and tips:

- Use the stubs below to write up your final project. Alternatively, if you would like the writeup to be an executable document (with [knitr](http://yihui.name/knitr/), [jupytr](http://jupyter.org/), or other tools), you can create it as a separate file and put a link to it here in the readme.

- For information on formatting text files with markdown, see https://guides.github.com/features/mastering-markdown/ . You can use markdown to include images in this document by linking to files in the repository, eg `![GitHub Logo](/images/logo.png)`.

- The project must be entirely reproducible. In addition to the results, the repository must include all the data (or links to data) and code needed to reproduce the results.

- If you are working with unpublished data that you would prefer not to publicly share at this time, please contact me to discuss options. In most cases, the data can be anonymized in a way that putting them in a public repo does not compromise your other goals.

- Paste references (including urls) into the reference section, and cite them with the general format (Smith at al. 2003).

OK, here we go.

# Evolutionary Alterations to the Eurypterid Metastoma

## Introduction and Goals

Eurypterids, commonly known as sea scorpions, are a diverse and cosmopolitan group of extinct subphylum Chelicerata (phylum Arthropoda). They lived from the mid-Ordovician to the late Permian and inhabited a wide array of marine and freshwater environments. Ranging in length from a few centimeters to 2.5 meters, eurypterids are studied for a range of paleoecological and preservational purposes (Bicknell et al 2020). The Peabody Museum, due to a long-term collaboration with Sam Ciurca, has the world’s largest collection of eurypterids—larger than all other museums combined. 

Last summer (2024), with support from the Von Damm Fellowship and YPM’s Invertebrate Paleontology division, I began digitizing and categorizing the Ciurca collection, cataloging every specimens’ preserved anatomical elements. Due to Ciurca’s detailed and extensive field notes, most specimens have robust locality, age, and species data, enabling me to use these data in a phylogenetically meaningful way.

The metastoma is a ventrally located anatomical element of eurypterids’ chitin exoskeleton. It connects laterally with segments of the swimming appendages; its anterior edge forms one border of the mouth, and its posterior edge connects to the body segments (tergites) containing the genital appendage. Metastoma have a wide variety of morphologies, including heart-shaped, elliptical, elongate, and pinched at either end. Additionally, metastoma have incredible representation in the fossil record of sites Ciurca sampled, as they seem to disarticulate easily. 

I am interested in mapping morphological change in eurypterid metastomas across the established phylogeny (Tetlie 2007). I want to determine how metastoma shape has evolved across the clade, how it associates with other changes such as the elongation of chelicerae, alteration of paddle appendages into claws, and alteration of the telson from a pointed to paddle shape. I am also interested in hypothesizing how these changes correlate with environmental or niche changes, if those changes can be grouped by clade, and how morphological variation could have been ecologically favored. 

From the established dataset, I will select several representative metastomas for each eurypterid species that the Peabody has data for. Once several metastoma samples have been selected, I will select and mark homologous points in the metastoma using a method developed by a previous postdoctoral mentor, Dr. Zachary Morris. I will select homologous points using the R package Stereomorph, and will map this data to the existing eurypterid phylogeny. I will also use this data to create an original phylogeny to determine how closely associated metastoma morphology is with speciation events (and just to see what it outputs!). 

## Methods

See my R script at: ([Uploading Metastoma_analysis.R…]).


To generate shape data, I used the stereomorph package in R to upload images, digitize landmarks, and read this data. See input files at: ([Curves.txt](https://github.com/user-attachments/files/18117796/Curves.txt), [Landmarks.txt](https://github.com/user-attachments/files/18117799/Landmarks.txt), [Shapes.zip](https://github.com/user-attachments/files/18117837/Shapes.zip), [Pictures.zip](https://github.com/user-attachments/files/18117841/Pictures.zip)). I used the geomorph package to run a GPA and PCA on the shape data, and I plotted the results with respect to Species and Genus. See covariate input file at: ([covariates.csv](https://github.com/user-attachments/files/18117881/covariates.csv)).

To construct a phylogeny from metastoma shape data, I created a distance matrix from the scaled & aligned GPA coordinate outputs. 

## Results

The tree in Figure 1...

## Discussion

These results indicate...

The biggest difficulty in implementing these analyses was...

If I did these analyses again, I would...

## References

Bicknell, R. D. C., Smith, P. M., & Poschmann, M. (2020). Re-evaluating evidence of Australian eurypterids. Gondwana Research, 86, 164–181. https://doi.org/10.1016/j.gr.2020.06.002

Tetlie, O. E. (2007). Distribution and dispersal history of Eurypterida (Chelicerata). Palaeogeography, Palaeoclimatology, Palaeoecology, 252(3), 557–574. https://doi.org/10.1016/j.palaeo.2007.05.011
