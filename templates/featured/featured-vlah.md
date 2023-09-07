# Featured Data

## MacroSheds: a synthesis of long-term biogeochemical, hydroclimatic, and geospatial data from small watershed ecosystem studies

November XX, 2023

Michael Vlah

### Citation

Vlah, M., S. Rhea, W. Slaughter, E. Bernhardt, N. Gubbins, A. DelVecchia, A. Thellman, and M.R. Ross. 2023. MacroSheds:
a synthesis of long-term biogeochemical, hydroclimatic, and geospatial data from small watershed ecosystem studies
ver 1. Environmental Data Initiative. [https://doi.org/10.6073/pasta/c8d6d29703f14735bf24cd8cebe91f24](https://doi.org/10.6073/pasta/c8d6d29703f14735bf24cd8cebe91f24).

### Description

The MacroSheds project aims to catalyze large-scale and ongoing synthetic research by watershed ecosystem scientists,
with the goal of developing generalities and theories that apply across scales (McDonnell et al. 2007). The heart of the
project is the [MacroSheds dataset](https://portal.edirepository.org/nis/mapbrowse?scope=edi&identifier=1262), currently
harmonizing streamflow, precipitation, and chemistry data from the Long Term Ecological Research program (LTER), the
Critical Zone Network of observatories (CZO/CZ Net), the US Forest Service, and other programs from the national to the
municipal. It provides comprehensive watershed summary statistics wherever gridded products are available. These include
descriptions of terrain, vegetation, land use, soil and bedrock type, and climate: everything one needs in order to
compare, categorize, and build on the results of hundreds of watershed studies, some of which have been monitoring since
the 1950s (e.g. Niwot Ridge, Andrews, Hubbard Brook, Fernow LTER sites).

In addition to supplying high quality data, the MacroSheds project aims to lower barriers to data use. The dashboard at
[macrosheds.org](https://macrosheds.org/) provides flexible tools for visual exploration of the dataset, and the
[macrosheds R package](https://github.com/MacroSHEDS/macrosheds) simplifies access, analysis, and proper attribution of
primary sources. The full dataset, including rich metadata, is archived through the Environmental Data Initiative, with
a planned update release every January. [All project code](https://github.com/MacroSHEDS) is on GitHub, and we welcome
community contributions. In the next year, we will harmonize data from additional primary sources, including the
National Ecological Observatory Network (NEON), and publish monthly and annual load estimates for all chemical
constituents. We will also continue development of a community upload portal, complete with both automated and
manual-visual quality control. For a more thorough description of these components, please see our open-access data
paper.

An example of the kind of synthesis enabled by the MacroSheds dataset is shown in Figure 1. This figure shows the
distribution of Sulfate-S concentrations across 21 of the 25 "domains," or collections of monitored watersheds,
currently included in the MacroSheds dataset.

<div class="figure_featured" style="width: 75%;">
    <figure>
        <a href="/static/images/featured_data/chemdist.png">
            <img src="/static/images/featured_data/chemdist.png" alt="Distribution of Sulfate-S concentrations."/>
        </a>
        <figcaption class="figure-caption">
            Figure 1: Distribution of Sulfate-S concentrations across 21 of the 25 "domains."
        </figcaption>
   </figure>
</div>

The MacroSheds data processing workflow (Figure 2) for a single domain contains four phases: 1) retrieval, 2)
harmonization, 3) derivation, and 4) post-processing. Figure 2 illustrates the evolution of precipitation data (P) from
raw to final form as part of a domain dataset. Gold circles represent processing "kernels" — modular and customizable
sets of routines that carry out the core steps of the first three phases. Within each phase, zero or more kernels are
called in sequence, depending on which products need to be updated, as determined by the progress tracker. In Phase 1,
retrieval kernels download primary source data. During Phase 2, kernels are called by one of four "munge engines"
(pentagons) depending on whether primary source files are sepa-rated by site, by time, by product, or some combination.
After Phase 3, time-series and geospatial data are organized into one file for each of the core MacroSheds products
(discharge, stream chemistry, precipitation, precipitation chemistry, gauge locations, watershed boundaries). After
Phase 4, a complete dataset has been generated for a single domain, and the process repeats for the next domain.

<div class="figure_featured" style="width: 75%;">
    <figure>
        <a href="/static/images/featured_data/macrosheds-concept.jpg">
            <img src="/static/images/featured_data/macrosheds-concept.jpg" alt="Phases of the Macrosheds workflow."/>
        </a>
        <figcaption class="figure-caption">
            Figure 2: Four phases of the MacroSheds workflow: 1) Retrieve, 2) Harmonize, 3) Derivation, and 4) 
            Post-process.
        </figcaption>
   </figure>
</div>

### References

 - McDonnell, J. J., et al. (2007), Moving beyond heterogeneity and process complexity: A new vision for watershed
   hydrology, Water Resour. Res., 43, W07301, [https://doi.org/10.1029/2006WR005467](https://doi.org/10.1029/2006WR005467).

### Related Content

A data paper about this dataset:

Vlah, M.J., Rhea, S., Bernhardt, E.S., Slaughter, W., Gubbins, N., DelVecchia, A.G., Thellman, A. and Ross, M.R.V.
(2023), MacroSheds: A synthesis of long-term biogeochemical, hydroclimatic, and geospatial data from small watershed
ecosystem studies. Limnol. Oceanogr. Lett, 8: 419-452. https://doi.org/10.1002/lol2.10325

### [All featured data contributions](/templates/featured/featured-grid)
