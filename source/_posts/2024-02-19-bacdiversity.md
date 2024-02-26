---
title: "Supplementary material to the talk ME53A-01 -- Ocean Science Meeting 2024"
categories: [Research, OSM]
tags: [OSM]
date: 2024-02-19
---

Supplementary material following the presentation ["ME53A-01 A mechanistic species coexistence theory explains the observed increase in marine microbial biodiversity with"](https://agu.confex.com/agu/OSM24/meetingapp.cgi/Paper/1490335) at OSM 2024 is provided here:


<!--more-->


# Preprint "Predictable functional biogeography of marine microbial heterotrophs"

The work is archived on [bioRxiv](https://www.biorxiv.org/content/10.1101/2024.02.14.580411v1) and under review in a peer-review journal. 

> **Abstract**

>Microbial heterotrophs (‘picoheterotrophs’) drive global carbon cycling, but how to quantitatively organize their functional complexity remains unclear. Here, we generate a global-scale, mechanistic understanding of marine picoheterotrophic functional biogeography with a novel model-data synthesis. We build picoheterotrophic diversity into a trait-based marine ecosystem model along two axes: substrate lability and optimization for growth rate (copiotrophy) vs. substrate affinity (oligotrophy). Using genetic sequences along an Alaska-to-Antarctica Pacific Ocean transect, we compile 21 picoheterotrophic guilds and estimate their degree of copiotrophy. Data and model agreement suggests that gradients in predation and substrate lability predominantly set biogeographical patterns, and identifies ‘slow copiotrophs’ subsisting at depth. Results demonstrate the predictability of the marine microbiome and connect ecological dynamics with carbon storage, crucial for projecting changes in a warming ocean.

## Poster session at OSM 2024

[OB14B-0686 Emergent structure and function of microbial heterotrophic communities in a model ocean](https://agu.confex.com/agu/OSM24/meetingapp.cgi/Paper/1484300)

# Theoretical exploration

The manuscript is on progress, coming soon!

## The general food web model

The mechanistic model of three trophic levels are given by:

{% mathjax %}
\begin{align}
\frac{1}{P_k} \frac{dP_k}{dt} &= \sum_{i} f_{ik} N_i - m_{pk} \\
\frac{1}{N_i} \frac{dN_i}{dt} &= \mu_i (R_1, \cdots, R_l) - m_i - g_i (P_1, \cdots, P_h) - m_{qi} N_i^{(x-1)} \\
\frac{dR_j}{dt} &= s(R_j) - \sum_{i} V_{ji} N_{ji} R_j.
\end{align}
{% endmathjax %}

N<sub>i</sub> denotes the density of prey, including bacteria and phytoplankton. 

## The top-down food web module

The top-down food web module assumes that one common predator (zooplankton) grazes on all bacteria and phytoplankton of similar sizes. Thus, we can simplify the model as 

{% mathjax %}
\begin{align}
\frac{1}{P} \frac{dP}{dt} &= \sum_{i} f_i N_i - m_p \tag{4}\\
\frac{1}{N_i} \frac{dN_i}{dt} &= \mu_i (R_1, R_2, \cdots, R_l) - g_i (P) - m - m_q N_i. \tag{5}
\end{align}
{% endmathjax %}

The equilibrium between the predator and prey can be reached if the prey are majorly limited by the predation pressure. Based on this assumption, we derived the top-down control formula:

{% mathjax %}
\begin{align}
N_i^* = \frac{m_p}{\sum_{j}^{n} f_j} + \frac{1}{m_q} (G_i - \bar{G}_{TD}) \tag{6}
\end{align}
{% endmathjax %}

where 
{% mathjax %}
G_i = \mu_i (R_1, R_2, \cdots, R_l) - g_i (P) - m
{% endmathjax %}
and 

{% mathjax %}
\bar{G}_{TD} = \frac{\sum_{j}^{n} f_j G_i}{\sum_{j}^{n} f_j}
{% endmathjax %}

is the community average of G<sub>i</sub> weighted by the predation rates. 

## The bottom-up food web module

Similarly, we can assume a food web where the consumer species at the middle trophic level are limited by the shared resource. This yields a bottom-up control module:

{% mathjax %}
\begin{align}
\frac{1}{N_i} \frac{dN_i}{dt} &= \mu_i (R) - m - g_i (P_1, \cdots, P_h) - m_q N_i \tag{7}\\
\frac{dR}{dt} &= s(R) - \sum_{i} V_i N_i R. \tag{8}
\end{align}
{% endmathjax %}

Again, based on the equilibrium state, we can derive a bottom-up control fomula:

{% mathjax %}
\begin{align}
N_i^* = \frac{s(R^*)}{\sum_{j}^{n} V_j R^*} + \frac{1}{m_q} (G_i - \bar{G}_{BU}) \tag{9}
\end{align}
{% endmathjax %}

where G<sub>i</sub> has the same definition and 

{% mathjax %}
\bar{G}_{BU} = \frac{\sum_{j}^{n} V_j G_j}{\sum_{j}^{n} V_j},
{% endmathjax %}

a community average of G_i for each species weighted by their consumption rates.


## Empirical estimation of m<sub>q</sub>

If the mixing processes are random and independent of the density of prey N<sub>i</sub>, the control formula indicates an approach to estimate m<sub>q</sub> and G<sub>i</sub> empirically. 

From the formula 5 and 7, we know that

{% mathjax %}
\begin{align}
F := \frac{dN}{dt} &= \frac{N_{t+1} - N_t}{h_t} \tag{10}\\
m_q &= -\frac{d^2 F}{dN^2} \tag{11}\\
G_i &= \frac{dF}{dN} \tag{12}
\end{align}
{% endmathjax %}

Here, N<sub>i</sub> is the time searies of the density of the focal consumer species, which can be measured in the field. 

Using the 1D simulation model, we estimated m<sub>q</sub> across the water column. The red dashed line indicates the true value of m<sub>q</sub>. The distribution is the estiamtes of m<sub>q</sub> using Eqns. 10-12 at different depths from the simulated results. 

<img src="Sim1D_DOM_est_mqb_100s_30y.png" width="60%" height="60%">


# About me

I am currently a Postdoctoral Researcher collaborating with Prof. Emily Zakem at Carnegie Science. My expertise spans theoretical modeling, bioinformatics, and machine learning, with a keen interest in exploring diverse topics such as species interactions on macro eco-evolutionary scales, species coexistence theory, oceanic modeling, and trait-based modeling. I am particularly intrigued by the application of machine learning techniques in ecology and evolution. For further details, please refer to my CV [**HERE**](./Liang_CV.pdf), with a Chinese version available [**HERE**](./CV_Liang_Chinese.pdf).

Current status: **Hunting for jobs!**
