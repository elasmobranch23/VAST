Description
=============

VAST
* Is an R package for implementing a spatial delta-generalized linear mixed model (delta-GLMM) for multiple categories (species, size, or age classes) when standardizing survey or fishery-dependent data.
* Has built in diagnostic functions and model-comparison tools
* Is intended to improve analysis speed, replicability, peer-review, and interpretation of index standardization methods

Regions available in the [example script](https://github.com/james-thorson/VAST/blob/master/examples/Example--simple.R): 
![alt text](https://github.com/nwfsc-assess/geostatistical_delta-GLMM/raw/master/examples/global_coverage.png "Global data coverage")
and see [FishViz.org](http://www.FishViz.org) for visualization of results for regions with a public API for their data.

Background
* This tool is designed to estimate spatial variation in density using spatially referenced data, with the goal of habitat associations (correlations among species and with habitat) and estimating total abundance for a target species in one or more years.  
* The model builds upon spatio-temporal delta-generalized linear mixed modelling techniques (Thorson Shelton Ward Skaug 2015 ICESJMS), which separately models the proportion of tows that catch at least one individual ("encounter probability") and catch rates for tows with at least one individual ("positive catch rates").  
* Submodels for encounter probability and positive catch rates by default incorporate variation in density among years (as a fixed effect), and can incorporate variation among sampling vessels (as a random effect, Thorson and Ward 2014) which may be correlated among categories (Thorson Fonner Haltuch Ono Winker In press).  
* Spatial and spatiotemporal variation are approximated as Gaussian Markov random fields (Thorson Skaug Kristensen Shelton Ward Harms Banante 2014 Ecology), which imply that correlations in spatial variation decay as a function of distance.  

Installation Instructions
=============
This function depends on R version >=3.1.1 and a variety of other tools.

First, install the "devtools" package from CRAN

    # Install and load devtools package
    install.packages("devtools")
    library("devtools")

Second, please install the following:
* TMB (Template Model Builder): https://github.com/kaskr/adcomp
* INLA (integrated nested Laplace approximations): http://www.r-inla.org/download

Note: at the moment, TMB and INLA can be installed using the commands 

    # devtools command to get TMB from GitHub
    install_github("kaskr/adcomp/TMB") 
    # source script to get INLA from the web
    source("http://www.math.ntnu.no/inla/givemeINLA.R")  
    
Next, please install the geostatistical_delta-GLMM package from this GitHub repository using a function in the "devtools" package:

    # Install package
    install_github("james-thorson/VAST") 
    # Load package
    library(VAST)

Known installation/usage issues
=============
none

Example code
=============
Please see examples folder for an example of how to run the model:
https://github.com/james-thorson/VAST/blob/master/examples/Example--simple.R

This code illustrates how to loop through different default model configurations,
plot diagnostics for each model, and obtain the AIC for each model.

Please also read the instructions from the single-species `SpatialDeltaGLMM` package, [Guidelines for West Coast users](https://github.com/nwfsc-assess/geostatistical_delta-GLMM/wiki/West-Coast-Guidelines)
wiki page, which is a living document and will evolve over time as best practices
become apparent.


Description of package
=============
### Please cite if using the software (this will be updated when a reference-paper is accepted)
* Thorson, J.T., Ianelli, J.N., Larsen, E., Ries, L., Scheuerell, M.D., Szuwalski, C., and Zipkin, E. In press. Joint dynamic species distribution models: a tool for community ordination and spatiotemporal monitoring. Glob. Ecol. Biogeogr.

Description of individual features
=============
### Correlated spatio-temporal variation among species
* Thorson, J.T., Scheuerell, M.D., Shelton, A.O., See, K.E., Skaug, H.J., and Kristensen, K. 2015. Spatial factor analysis: a new tool for estimating joint species distributions and correlations in species range. Methods Ecol. Evol. 6(6): 627–637. doi:10.1111/2041-210X.12359.

### Index standardization
* Thorson, J.T., Shelton, A.O., Ward, E.J., Skaug, H.J., 2015. Geostatistical delta-generalized linear mixed models improve precision for estimated abundance indices for West Coast groundfishes. ICES J. Mar. Sci. J. Cons. 72, 1297–1310. doi:10.1093/icesjms/fsu243
* Shelton, A.O., Thorson, J.T., Ward, E.J., Feist, B.E., 2014. Spatial semiparametric models improve estimates of species abundance and distribution. Can. J. Fish. Aquat. Sci. 71, 1655–1666. doi:10.1139/cjfas-2013-0508. URL: http://www.nrcresearchpress.com/doi/abs/10.1139/cjfas-2013-0508#.VMafDf7F_h4

### Vessel targeting
* Thorson, J.T., Fonner, R., Haltuch, M., Ono, K., and Winker, H. In press. Accounting for spatiotemporal variation and fisher targeting when estimating abundance from multispecies fishery data. Can. J. Fish. Aquat. Sci. doi:10.1139/cjfas-2015-0598.

### Range shift metrics
* Thorson, J.T., Pinsky, M.L., Ward, E.J., In press. Model-based inference for estimating shifts in species distribution, area occupied, and center of gravity. Methods Ecol. Evol.

### Spatio-temporal statistical methods
* Thorson, J.T., Skaug, H.J., Kristensen, K., Shelton, A.O., Ward, E.J., Harms, J.H., Benante, J.A., 2014. The importance of spatial models for estimating the strength of density dependence. Ecology 96, 1202–1212. doi:10.1890/14-0739.1. URL: http://www.esajournals.org/doi/abs/10.1890/14-0739.1

### Accounting for fish shoals using robust observation models
* Thorson, J. T., I. J. Stewart, and A. E. Punt. 2012. Development and application of an agent-based model to evaluate methods for estimating relative abundance indices for shoaling fish such as Pacific rockfish (Sebastes spp.). ICES Journal of Marine Science 69:635–647. URL: http://icesjms.oxfordjournals.org/content/69/4/635
* Thorson, J. T., I. Stewart, and A. Punt. 2011. Accounting for fish shoals in single- and multi-species survey data using mixture distribution models. Canadian Journal of Fisheries and Aquatic Sciences 68:1681–1693. URL: http://www.nrcresearchpress.com/doi/abs/10.1139/f2011-086#.VMafcf7F_h4

### Accounting for variation among survey vessels
* Helser, T.E., Punt, A.E., Methot, R.D., 2004. A generalized linear mixed model analysis of a multi-vessel fishery resource survey. Fish. Res. 70, 251–264. doi:10.1016/j.fishres.2004.08.007
* Thorson, J.T., Ward, E.J., 2014. Accounting for vessel effects when standardizing catch rates from cooperative surveys. Fish. Res. 155, 168–176. doi:10.1016/j.fishres.2014.02.036

### Bias-correction of estimated indices of abundance
* Thorson, J.T., and Kristensen, K. 2016. Implementing a generic method for bias correction in statistical models using random effects, with spatial and population dynamics examples. Fish. Res. 175: 66–74. doi:10.1016/j.fishres.2015.11.016.



