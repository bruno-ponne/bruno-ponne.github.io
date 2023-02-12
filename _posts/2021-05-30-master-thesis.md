---
title: "The Impact of Institutional Arrangements on Student Achievement: Evidence from Brazil"
author: "Bruno Gasparotto Ponne - bruno.ponne@gmail.com"
layout: project
abstract: This project was actually my Master thesis presented at the Hertie School in 2021 and tutored by Professor Christian Traxler. Two causal inference methodologies - fixed-effects and synthetic control method - were employed to examine the effect of the educational reforms implemented in Ceará, Brazil.
image: capa04.png
---


### Introduction

Ceará, a northeastern Brazilian state, put two new educational policies in place in 2007. The first is a performance-based financing scheme that conditions municipal tax transfers to education quality. The second consists of technical assistance to municipalities, including training for teachers and provision of textbooks.

My objective was to estimate the causal effect of these interventions on student achievement. To achieve that, I used two causal inference methodologies: fixed-effects and synthetic control method.


### Analytical Sample

The data for this research are provided by the Ministry of Education, Ministry of Health, Instituto de Pesquisa Econômica Aplicada (IPEA), a research department of the Brazilian government, and Instituto Brasileiro de Geografia e Estatística (IBGE), the statistics institute of Brazil.

### Descriptive Statistics

Here I present some descriptive statistics. Plots were developed with ggplot. Density, dot, line and spatial plots explore the characteristics of the sample before and after the intervention. In general, the plots suggest that education in Ceará has improved more compared to the rest of the country as I had already pointed out in my previous exploratory analysis.

- Density Plots
<img src="/assets/Figure5.png" width="550" height="auto" />

- Maps
<img src="/assets/Figure6.png" width="550" height="auto" />

- Dot Plot
<img src="/assets/Figure7.png" width="550" height="auto" />


### Synthetic Control Method

The R library *Synth* was used to estimate a synthetic Ceará, that is, a Ceará where the policy interventions did not occur. Since there were several levels of education and two subjects to be analyzed, I created functions to help me estimate six synthetic control: one for each level (primary, lower secondary and upper secondary) and for each subject (Portuguese and mathematics).

The authors of the package *Synth* provide a function to plot graphs in base R. However, since I wished to use colors to highlight my graphs, I developed the function *plot_scm()* that prepares the output of *Synth* to be used in ggplot.

The plots bellow shows the results of the synthetic control approach for primary and lower secondary education

<img src="/assets/Figure8.png" width="550" height="auto"/>

As seen, there is a gap between Ceará and synthetic Ceará, highlighting that the reforms seem to have improved Ceará performance compared to its synthetic version, not affected by the reforms. In upper secondary education there was no evidence of an effect on student scores.

Here I show the permutation test employed to examine statistical significance of the synthetic control findings.

<img src="/assets/Figure14.png" width="550" height="auto"/>


###  Results

The synthetic control findings are consistent with an increase in performance in Portuguese. More precisely, the method indicates that scores increased by 10% and 5%, respectively, in primary education and lower secondary education. Regarding mathematics, the findings were not statistically significant. Furthermore, there was no evidence that the new policies had an impact on upper secondary education.

<br>

<div class = "github">
    <div class = "github-img">
        <img src="/assets/github-mark.png"/>
    </div>
    <div class = "github-link">
        Visit the complete project at
        <a href='https://github.com/bruno-ponne/MasterThesis' target="_blank"> my Github repository.</a>
    </div>
</div>
<br>

### Important notes to replicate my thesis from my Git repository:

- To replicate my research, download this repository and open the R project in your computer. After that choose the script of interest and run it;
- All paths are already coded to load the necessary functions and data from the right folders;
- All necessary data is in the *data* and *map* folder.



