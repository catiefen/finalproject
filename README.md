# Evolutionary Alterations to the Eurypterid Metastoma

## Introduction and Goals

Eurypterids, commonly known as sea scorpions, are a diverse and cosmopolitan group of extinct subphylum Chelicerata (phylum Arthropoda). They lived from the mid-Ordovician to the late Permian and inhabited a wide array of marine and freshwater environments. Ranging in length from a few centimeters to 2.5 meters, eurypterids are studied for a range of paleoecological and preservational purposes (Bicknell et al 2020). The Peabody Museum, due to a long-term collaboration with Sam Ciurca, has the world’s largest collection of eurypterids—larger than all other museums combined. 

Last summer (2024), with support from the Von Damm Fellowship and YPM’s Invertebrate Paleontology division, I began digitizing and categorizing the Ciurca collection, cataloging every specimens’ preserved anatomical elements. Due to Ciurca’s detailed and extensive field notes, most specimens have robust locality, age, and genus data, enabling me to use these data in a phylogenetically meaningful way.

The metastoma is a ventrally located anatomical element of eurypterids’ chitin exoskeleton. It connects laterally with segments of the swimming appendages; its anterior edge forms one border of the mouth, and its posterior edge connects to the body segments (tergites) containing the genital appendage. Metastoma have a wide variety of morphologies, including heart-shaped, elliptical, elongate, and pinched at either end. Additionally, metastoma have incredible representation in the fossil record of sites Ciurca sampled, as they seem to disarticulate easily. 

From my established dataset, I will select several representative metastomas for each eurypterid species that the Peabody has data for. Once several metastoma samples have been selected, I will select and mark homologous points in the metastoma using a method developed by a previous postdoctoral mentor, Dr. Zachary Morris. I will select homologous points using the R package Stereomorph, and will map this data to the existing eurypterid phylogeny (Tetlie 2007). Additionally, I will use this morphological data to run a Generalized Procrustes Analyses and a Principal Components Analyses to evaluate metastoma shape variation among and within genuses. 

As eurypterid fossils are most often found incomplete and disarticulated, there is significant interest in genus-level identification from single anatomical elements. As the metastoma is frequently disarticulated from molts and/or carcasses, I will use metastoma shape data to generate a phylogeny to determine how closely associated metastoma morphology is with speciation events, as well as to assess the reliability of genus-level or even species-level identification from metastomas alone.


## Methods

See my R script, input files, and outputs here: Zip folder

To create shape data, I used the stereomorph package in R to upload images, digitize landmarks, and read data. This digitization process involves individual plotting of homologous points and curves (Landmarks.txt, Curves.txt) across all sample metastoma images ("Pictures" folder), as well as size scaling. The landmark data, saved as pixel coordinates (and contained in the folder "Shapes"), and was read by the stereomorph program for analysis via geomorph. 

I used the geomorph package to run a scaled GPA (Fig. 1) and PCA on the shape data, plotting the PCA results with respect to genus (Fig. 2). 

As integration of solely morphological data into a phylogenetic reconstruction proves challenging with currently available genonics-oriented softwares and technologies, and as metastoma shape is relatively simple and eaily qualitatively described, I captured metastoma shape through discrete, binary characters, as follows: 

Anterior lobes (1: one lobe, 2: two lobes)

Posterior lobes (0: flat, 1: one lobe, 2: two lobes)

Lateral concavity (0: convex, 1: concave)

Maximum width location (0: one maximum at midpoint, 1: two maximums near anterior and posterior ends, 2: one maximum between the anterior end and midpoint)

Posterior taper (0: present, 1: absent)


I manually structured four iterations of these data into four nexus file formats. With the iqtree software on Yale's McCleary computer cluster, I generated several phylogenies for my data: one using all coded samples, and three using different configurations of samples such that each genus is represented once (Figs. 4-7). 

Finally, I converted an established and well-supported eurypterid phylogeny (Tetlie 2007) to newick format for comparison with my phylogeny generated on metastoma data. I trimmed the Tetlie phylogeny to match the genuses of my input data for comparison (Fig. 3). 



## Results

![gpa_plot](https://github.com/user-attachments/assets/17b9751d-f2fe-41cd-9025-473c82190de8)

Figure 1: GPA plot with concensus and individuals. Scaled for size. Large black dots represent the consensus; small grey dots map each individual specimen's landmarks. Each pixel represents one landmark, as assigned with the stereomorph package. 




![pca_plot](https://github.com/user-attachments/assets/3bbc679b-8fb9-4fcb-8759-2c045fc8f093)
Figure 2: PCA results. Each dot represents one specimen's morphological shape data as recorded by landmarking in the stereomorph package. Color coded by family. 




My PCA (Fig. 2) indicates partial distinction between metastoma shapes (Fig. 1) between eurypterid families. (Note that for the families Carcinosomatidae and Mixopteridae, only one specimen each with a complete metastoma could be recovered. Their presence in this morphospace is for comparison with other families, not within-family comparison.) The Dolichopteridae samples group around (0.1, 0.04), and the Hughmilleriidae samples mostly group around (0.07, 0.06). The Eurypteridae samples, however, show a much greater variation. This could be due to the larger number of included species, but is likely due to the broader diversity of metastomas (and other anatomical elements) within Eurypteridae. It does not appear that metastomas alone can be used to confidently assign a eurypterid specimen to a family, though they would have use in combination with other diagnostic criteria. 




![trimmed_tetlie_phy](https://github.com/user-attachments/assets/10a87afa-fe6f-4c5c-9d70-71b8c4e6ae88)
Figure 3: Known eurypterid phylogeny, trimmed to match genuses in this study. Modified from Tetlie 2007.




When these data are converted to discrete characters and used to generate a phylogeny (Fig. 4), several families respond well: the Dolichopteridae all group together with 94% bootstrap support, and many of the Eurypterus species group together, though with slightly distinctive relationships and with varying levels of bootstrap support. Additionally, the families Carcinosomatidae, Mixopterus, and Hughmilleriidae cluster with a 90% bootstrap support, which is phylogenetically supported by the existing phylogeny. However, two other Hughmilleriidae samples are instead represented as sister to this group with very low bootstrap scores, and another Highmilleriidae sample groups within the Eurypteridae. This, in combination with the somewhat erratic grouping of the Eurypteridae species, makes this phylogeny immensely unreliable for discerning phylogenetic relationships without the employment of an established phylogeny (Fig. 3). 




![phy_all](https://github.com/user-attachments/assets/4851ab4a-e267-4972-9a3e-b7be8a957884)
Figure 4: Unrooted phylogeny from all 26 samples. With bootstraps. Generated using iqtree.




The first model of a phylogeny constructed with one specimen per available genus (Fig. 5) fares much better, though with very low bootstraps. It groups Carcinosomatidae and Mixopteridae as closely related, which is correct, and assigns Hughmilleriidae as the next closest related species--also correct. However, its grouping of Eurypteridae and Dolichopterus suggests a much closer phylogenetic relationship than recovered in the known phylogeny, with the clade containing Eurypteridae and Dolichopterus being sister to the clade containing other families in the trimmed Tetlie phylogeny (Fig. 3).




![phy1](https://github.com/user-attachments/assets/2879f6dc-4ed3-448e-9eb9-c2626f7d4fcf)
Figure 5: Unrooted phylogeny with only one specimen per genus. Includes YPM-256001, YPM-535959, YPM-251405, YPM-387989, YPM-207315, and YPM-237273. With bootstraps. Generated using iqtree.




The second model using this method (Fig. 6) is very similar, still with low bootstrap support. It incorrectly separates the two genuses within the Eurypteridae, though it does recover some of the relationship between Paracarcinosoma and Mixopterus. 




![phy2](https://github.com/user-attachments/assets/e441800b-e6c3-4ab1-bd2c-39d8faf141f8)
Figure 6: Unrooted phylogeny with only one specimen per genus. Includes YPM-256001, YPM-251416, YPM-256336, YPM-387990, YPM-209052, and YPM-207315. With bootstraps. Generated using iqtree.




The third model (Fig. 7) is most similar to the first (Fig. 4), with a closer grouping of the Eurypterida genuses and marginally higher bootstraps. (Note that in the known phylogeny, the genesus Eurypterus and Erieopterus are both paraphyletic. YPM fossils used in this study do not have identification to the species level, but for simplicity, we can expect the Eurypterus and Erieopterus species in the study to group with the majority of their genus in the consensus tree.)




![phy3](https://github.com/user-attachments/assets/3a328d04-cce4-4138-b8f2-3e773716c4ab)
Figure 7: Unrooted phylogeny with only one specimen per genus. Includes YPM-256001, YPM-255585, YPM-206827, YPM-388192, YPM-209060, and YPM-207315. With bootstraps. Generated using iqtree.




## Discussion

These results indicate that metastoma shape alone is not sufficient data to assign species to a genus or family level, nor should it be used as a sole factor to designate phylogenetic relationships. From the PCA, it does not appear that metastomas alone can be used to confidently assign a eurypterid specimen to a family, though they would have use in combination with other diagnostic criteria and do still hold value in distinguishing taxonomic assignments. Additionally, the phylogenies support that metastoma shape alone should not be used to distinguish phylogenetic relationships or establish new families, given that metastoma shape captured some, but not all, species variation necessary to correctly reconstruct accurate phylogenetic relationships. 

These data should advise caution when assigning taxonomic identities based on very limited anatomical data, and suggest a conservative approach to taxonomic designation in collections and in research. Additionally, these patterns can almost certainly be applied to other anatomical elements within eurypterids. For instance, telson and coxa shape are often used as a distinguishing criteria for taxonomic assignments. While these assignments based on limited recovered fossil material are risky, there is likely room for using the shape of multiple anatomical elements as a reliable taxonomic identifier, provided multiple anatomical elements are preserved and complete.

The biggest difficulty in implementing these analyses was the data management, especially with the shape data and morphometrics. I would have loved to see a phylogeny built out of my shape data, but with the increasing importance of genomic data and decreasing amount of taxonomic-focused paleontological research (because so many petinct groups have relatively well-resolved phylogenies predating the computational era), it is unsurprising that these tools do not yet exist. While thinking about how to compensate for both this lack of tools and my lack of R proficiency, and how to capture each "dial" in metastoma shape variation, I settled on discrete character coding, which I was very happy with. 

If I did these analyses again, I would reach out to other museums or take a trip to West Campus to gather more metastoma data for a broader range of species. I would also be curious to run a GPA on each family/genus, and to then character code that data and create a phylogeny from it.




## References

Adams D, Collyer M, Kaliontzopoulou A, Baken E (2024). “Geomorph: Software for geometric morphometric analyses. R package version 4.0.9.” https://cran.r-project.org/package=geomorph.

Baken E, Collyer M, Kaliontzopoulou A, Adams D (2021). “geomorph v4.0 and gmShiny: enhanced analytics and a new graphical interface for a comprehensive morphometric experience.” Methods in Ecology and Evolution, 12, 2355-2363.

Bicknell, R. D. C., Smith, P. M., & Poschmann, M. (2020). Re-evaluating evidence of Australian eurypterids. Gondwana Research, 86, 164–181. https://doi.org/10.1016/j.gr.2020.06.002

Bui Quang Minh, Heiko A. Schmidt, Olga Chernomor, Dominik Schrempf, Michael D. Woodhams, Arndt von Haeseler, and Robert Lanfear (2020) IQ-TREE 2: New models and efficient methods for phylogenetic inference in the genomic era. Mol. Biol. Evol., in press. https://doi.org/10.1093/molbev/msaa015

Diep Thi Hoang, Olga Chernomor, Arndt von Haeseler, Bui Quang Minh, and Le Sy Vinh (2018) UFBoot2: Improving the ultrafast bootstrap approximation. Mol. Biol. Evol., 35:518–522. https://doi.org/10.1093/molbev/msx281

Olsen Aaron M, Mark W Westneat. 2015. StereoMorph: an R package for the collection of 3D landmarks and curves using a stereo camera set-up.

Paradis E, Schliep K (2019). “ape 5.0: an environment for modern phylogenetics and evolutionary analyses in R.” Bioinformatics, 35, 526-528. doi:10.1093/bioinformatics/bty633.

Subha Kalyaanamoorthy, Bui Quang Minh, Thomas KF Wong, Arndt von Haeseler, and Lars S Jermiin (2017) ModelFinder: Fast model selection for accurate phylogenetic estimates. Nature Methods, 14:587–589. https://doi.org/10.1038/nmeth.4285

Tetlie, O. E. (2007). Distribution and dispersal history of Eurypterida (Chelicerata). Palaeogeography, Palaeoclimatology, Palaeoecology, 252(3), 557–574. https://doi.org/10.1016/j.palaeo.2007.05.011

Wickham H (2016). ggplot2: Elegant Graphics for Data Analysis. Springer-Verlag New York. ISBN 978-3-319-24277-4, https://ggplot2.tidyverse.org.

Yu G, Smith D, Zhu H, Guan Y, Lam TT (2017). “ggtree: an R package for visualization and annotation of phylogenetic trees with their covariates and other associated data.” Methods in Ecology and Evolution, 8, 28-36. doi:10.1111/2041-210X.12628, http://onlinelibrary.wiley.com/doi/10.1111/2041-210X.12628/abstract.



R Version 2024.4.2.764.
