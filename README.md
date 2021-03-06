# :maple_leaf: MAPLE: **M**emory **A**ccess **P**rofi**LE**r

MAPLE is a [Pin](https://software.intel.com/en-us/articles/pin-a-dynamic-binary-instrumentation-tool)-based profiler to provide dumping memory access traces of applications at page-level. Currently, it records the _accessed virtual page number_, _timestamp_ and _r/w_. 
> The supported output format is only **csv** at the moment; _binary_ and _vscsi_ will be added soon.

> MAPLE has a built-in LRU cache helping to eliminate redundant items which may get answered by front layer caches.

**[1]** Install the [Pin tool](https://software.intel.com/en-us/articles/pin-a-dynamic-binary-instrumentation-tool)  on your Linux machine. [Download](https://software.intel.com/en-us/articles/pin-a-binary-instrumentation-tool-downloads), unpack a kit and `cd` to the directory.

    $ tar zxf pin-[version].tar.gz
    $ cd pin-[version]/source/tools

**[2]** Clone the __MAPLE!__ :maple_leaf:

    $ git clone https://github.com/0xreza/maple-profiler.git

**[3]** Make the module (for your target architecture):

    $ cd maple-profiler
    $ mkdir obj-intel64
    $ make obj-intel64/maple.so TARGET=intel64

**[4]** Run the experiment:

    $ ../../../pin -t obj-intel64/maple.so -- [target_program]

**[5]** You can feed your trace into [Mimircache!](http://mimircache.info/) to get insightful heat-maps and hit-ratio curves! 


****

###### Example:

<div style="display:block; width: 100%;">


<img alt="mimircache maple hit-ratio curve" style="float: left;"  height="280" src="examples/hrc_ocean_ncp.png" />

<img alt="mimircache maple heatmap" height="280"  src="examples/heatmap_ocean_ncp.png" />

</div>

###### _plotted using traces gathered from [PARSEC, ocean_ncp](http://parsec.cs.princeton.edu) benchmark._

<div style="display:block; width: 100%;">

<img alt="mimircache maple hit-ratio curve" style="float: left;"  height="280" src="examples/hrc.png" />

<img alt="mimircache maple heatmap" height="280"  src="examples/heatmap.png" />

</div>

###### _plotted using traces gathered from [PARSEC, streamcluster](http://parsec.cs.princeton.edu) benchmark._

------------------------
### Work in Progress

-   Supporting compact output formats
-   Supporting spatio/temporal sampling 

------------------------
### Credits
Maple is released on public domain under GPLv3, created by [Reza Karimi](https://0xreza.com), PhD candidate at [SimBioSysLab, Emory University](https://simbiosyslab.github.io/), while interning at [INESC-ID, Lisbon](http://inesc-id.pt) (Summer 2018) with invaluable help of (and base code from) David Gureya (PhD student at Instituto Superior Técnico); and coaching by Joao Barreto, my internship mentor.

Contributions and suggestions are welcome!
