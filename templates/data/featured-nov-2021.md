# Featured Data

## Journey North – Hummingbird and Monarch Butterfly observations by volunteer community scientists across Central and North America (1996-2020)

November 2021

### Citation

Sheehan, N. and L. Weber-Grullon. 2021. Journey North – Monarch Butterfly and Milkweed observations by volunteer community scientists across Central and North America (1996-2020) ver 1. Environmental Data Initiative. [https://doi.org/10.6073/pasta/f7d7bef57f94b33b8a18a26954252412](https://doi.org/10.6073/pasta/f7d7bef57f94b33b8a18a26954252412).

Sheehan, N. and L. Weber-Grullon. 2021. Journey North – Hummingbird observations by volunteer community scientists across Central and North America (1996-2020) ver 1. Environmental Data Initiative. [https://doi.org/10.6073/pasta/a4bebd2b5fb5c1fd0757eac254a06357](https://doi.org/10.6073/pasta/a4bebd2b5fb5c1fd0757eac254a06357).

### Description

During the 2021 EDI summer fellowship, Luis Weber-Grullón, EDI Summer Fellow with [Journey North](https://journeynorth.org/), and his mentor Nancy Sheehan, Journey North’s Program Coordinator at the [University of Wisconsin-Madison Arboretum](https://arboretum.wisc.edu/) successfully published two data packages.

The data packages are a great example of community science data published and hosted in EDI. Journey North is a crowdsourced community science program of the University of Wisconsin-Madison Arboretum that encourages people from across North America in tracking wildlife migration and seasonal change to foster important scientific understanding, environmental awareness, and the land ethic in citizens. The data packages featured here focus on two of Journey North’s projects, the [Monarch & Milkweed Project](https://journeynorth.org/monarchs) and the [Hummingbird Migration Project](https://journeynorth.org/hummingbirds).

### The Projects

<figure class="figure_featured">
    <img src="/static/images/featured_data/monarchs.png" alt="monarch butterflies" width="50%">
    <figcaption>Fig. 1: Monarchs roosting at Spirit Lake, Iowa (photo credit: [Courtney, Journey North](https://journeynorth.org/sites/default/files/2021-09/Courtney_SpiritLakeIA.jpg)).</figcaption>
</figure>

Journey North Monarch & Milkweed Project: an ongoing study of monarch butterfly migration (species Danaus plexippus) and milkweed phenology, conducted at broad spatial and temporal scales. Participants from Canada, the US and Mexico track and submit observations on monarchs’ first arrival dates, breeding and feeding behavior as well as the onset of fall migration, roosts, and presence of monarchs found beyond official sanctuary locations on Mexico. Community scientists also track first emergence of milkweed in the spring and the presence of milkweed across the landscape, documenting milkweed species, if known. This data package featured here contains 24 years of monarch and milkweed data (1996 – 2020) collected by 42,518 community scientists

<figure  class="figure_featured">
    <img src="/static/images/featured_data/peak-immigration.png" alt="map of monarch fall roosts and peak migration" width="80%">
    <figcaption>Fig. 2: Monarch fall roosts (solid circle with white square) and peak migration (solid circle) through 10/31/2021, <img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle1.png">before Aug 16, <img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle2.png">Aug 16 &#8211; Aug 29, <img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle3.png"> Aug 30 &#8211; Sep 12, <img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle4.png"> Sep 13 &#8211; Sep 26,<img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle5.png"> Sep 27 &#8211; Oct 10,<img style="width:10px;" src="https://maps.journeynorth.org/map/symbols/YlOrRdWeekly/circle6.png"> Oct 11 &#8211; Oct 24 (map credit: <a rel="noreferrer noopener" href="https://maps.journeynorth.org/map/?map=monarch-roost-fall&amp;year=" target="_blank">Journey North</a>).</figcaption>
</figure>

Journey North Hummingbird Migration Project: an ongoing study of hummingbird migration. From 1996 to 2000, 30,703 community scientists from across North America submitted observational data on first arrival dates, breeding and feeding behavior, the onset of fall migration and presence of hummingbird species throughout the winter months in the United States. Focal species are the Ruby-throated hummingbird (Archilochus colubris) and Rufous hummingbird. Observational data is also available for Broad-tailed hummingbird (Selasphorus platycercus), Black-chinned hummingbird (Archilochus alexandri), Calliope hummingbird (Selasphorus calliope), Costa’s hummingbird (Calypte costae), Anna’s hummingbird (Calypte anna), Allen’s hummingbird (Selasphorus sasin).

<figure  class="figure_featured">
    <img src="/static/images/featured_data/hummingbird.png" alt="hummingbird" width="50%">
    <figcaption>Fig. 3: Hummingbird female (photo credit: [Janet Fender](https://journeynorth.org/sites/default/files/2021-10/1526550801.full_.jpg))</figcaption>
</figure>

**In addition to projects presented here, Journey North community scientists also track the migration of Common Loons & Ice-Out, American Robins, Barn Swallows, Red-winged Blackbirds, and Baltimore and Bullock’s Orioles. These datasets have yet to be published.*

### The Need and Process
Until recently, researchers who intended to use the Monarch & Milkweed Project and Hummingbird Project data had to contact Journey North staff to obtain the data and discuss any inaccuracies and biases.

During his fellowship, Luis, a recent graduate from Arizona State University’s Master of Environmental Life Sciences Program, took a deep dive into Journey North’s long-term monitoring data. He developed a workflow for data cleaning that enhanced data quality and provided a pathway for processing future observational data to update the EDI data packages. This workflow will assist Journey North in the future during a planned database restructuring. The workflow is programmed in Python and captured in a Jupyter notebook. Highlights from this workflow include:

- Recategorizing older syntax and matching “retired” data fields to current data collection fields.
- Harmonizing formats for dates, customer IDs and geographic locations. The semantic cleaning of the data was a challenging task, due to the extent of different syntax used over the course of this 24-year-old community science program.

In publishing these data packages, Journey North now aligns with best practice for data management recommended by the Citizen Science Association. In the EDI data repository, the data have a unique identifier, are unambiguous, well described by metadata & transparent and easily accessible. Credit is given to the creators. As Nancy Sheehan, Program Coordinator for Journey North, notes:

> “Since Journey North was acquired by the University of Wisconsin-Madison Arboretum in 2019, I have taken my responsibility as a data steward very seriously. I am grateful to EDI in providing the funding that enabled the work of Luis Weber and led to publishing of these two datasets. EDI and Luis helped Journey North meet FAIR guiding principles. This work honors the efforts of many hundreds of volunteers who have collected observational data over the past 25 years. On behalf of the wider Journey North community scientists (past and present), I hope that by ensuring that these datasets are “findable, accessible, interoperable and reusable” researchers will explore pressing questions in wildlife migration to guide conservation action for the migratory species we love.” 

Researchers have used the Journey North long-term observational data to investigate changes in phenology of migrating species and their early season nectar resources; spring recolonization rates; distribution of species during breeding and non-breeding periods; and spatio-temporal patterns in migration phenology. Having these data published and described with extensive metadata will make it easier for scientists to use the data in analyses as one researcher has already commented:

> “Hey Nancy, This is fantastic! Love this and so cool to see how the JN are being hosted. The links to R code, etc that allow one to pull in the data and clean it up are amazing… Super cool stuff you’ve done!”

### [All featured data contributions](/templates/data/featured)

