<p align="center">
<img width="60%" height="60%" src="https://github.com/pharmbio/plaid/blob/main/images/plaid-logo.png?raw=true">
</p>

# PLAID: Plate Layouts using Artificial Intelligence Design

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
![with-coffee](https://img.shields.io/badge/made%20with-%E2%98%95%EF%B8%8F%20coffee-yellow.svg)
[![GitHub Repo stars](https://img.shields.io/github/stars/pharmbio/plaid?style=social)](https://github.com/pharmbio/plaid/stargazers)


**PLAID** is a flexible
constraint-programming model for creating highly-effective microplate
layouts.
**PLAID** was developed with the goal of helping
researchers plan well-designed experiments by creating robust
microplate layouts<sup>[1](#RefModRef2020)</sup> and thus improving
the quality of the data obtained from an experiment. A web version is available at [plaid.pharmb.io](https://plaid.pharmb.io/). 

**PLAID**  is easy and straightforward to use. The current
model allows:

* Choosing how many outermost rows and columns should be left empty in
order to reduce errors due to the edge effect.
* For each compound (or combination thereof):
  - all concentration levels of a given replica appear on the same
  plate.
  - each concentration level can be constrained to appear on a different row and column.
* The replicated compounds can be constrained to appear on the same plate or a
different plate.
* For each type of control and concentration, the difference in number
between plates is at most 1.
* Controls of the same kind are separated by at least 1 well in any
direction. Whenever possible (if the total number of controls falls below a given threshold),
controls are separated by at least 2 wells in any direction.
* Empty wells are balanced across the plate together with controls.


Using **PLAID** does not require any programming knowledge.
Users just need to write down the necessary information, such as the number
of compounds, combinations, controls, etc, in a simple text file and
click run!

The output is a list in CSV format containing plate ID, well, content
(compound, combination or control), concentration, and latex name,
meant to be used as input for automatic tools. (TODO: visualize the
layout using latex)

We believe **PLAID** is the first attempt to use constraint
programming to design microplate layouts. Due to the use of MiniZinc,<sup>[2](#RefMiniZinc)</sup>
a high-level constraint modelling language, **PLAID** is
highly customizable.



## Table of Contents
* [Installation and Usage](#installation)
  - [Using the MiniZinc IDE](#minizinc-ide)
  - [Using the command line](#command-line)
* [Contact](#contact)
* [Citation](#citation)
* [Other Publications](#publications)
* [Publications Using PLAID](#publications-using-plaid)
* [References](#references)
* [License](#license)


<a name="installation"></a>
## Installation and Usage

* Download and install [MiniZinc](https://www.minizinc.org/).
* Clone this repo OR download plate-design.mzn, layout_predicates.mzn, and empty-file.dzn.
* Fill in the specific details of your experiment in a
empty-file.dzn. Alternatively, you can download and modify any of the example
files in /dzn-examples or /JSON-examples.


<a name="minizinc-ide"></a>
### Using the MiniZinc IDE
* Open both plate-design.mzn and your .dzn file (if you have one) using the MiniZinc IDE
* In the dropdown menu called "Solver configuration", located in the
top middle area of the MiniZinc IDE, select
Gecode<sup>[3](#RefGecode)</sup> as solver (Do not select Gecode Gist,
which is used for debugging).
* Click the "Run" button, located to the
left of "Solver configuration".
* In the popup window, you can either select a data file (you can only
see those that are open in the IDE) or enter all parameters by hand.
Note that you need to scroll down inside the popup to be able to type
in all the values.
* Optional: you can change the random seed to obtain a different layout for the
same input data under "MiniZinc/Solver Configuration/Show
configuration editor...". 


<a name="command-line"></a>
### Using the command line

```bash
$ minizinc --solver Gecode plate-design.mzn pl-example01.dzn
```

For more details and options, read the [MiniZinc command line documentation](https://minizinc.org/doc-2.8.4/en/command_line.html).


<a name="contact"></a>
## Contact

This project is coordinated by
[Maria Andreina Francisco Rodriguez](https://katalog.uu.se/profile?id=N11-1772)
([@andreina-francisco](https://github.com/andreina-francisco)) and
[Ola Spjuth](https://katalog.uu.se/empinfo/?id=N2-878)
([@olas](https://github.com/olas)) and it is part of the joint research work
at the
[Pharmaceutical Bioinformatics Research Group](https://farmbio.uu.se/research/pharmaceutical-bioinformatics/),
Department of Pharmaceutical Biosciences, 
and the [Optimisation Research Group](https://www2.it.uu.se/itwiki.php?page=research/group/optimisation&action=browse), 
[Department of Information Technology](https://www.uu.se/en/department/information-technology), both at 
[Uppsala University](https://www.uu.se/en/), Sweden. 


Got ideas for improvement? We would love to hear about your suggestions!


<a name="citation"></a>
## Citation

The following manuscript in [Artificial Intelligence in the Life Sciences](https://doi.org/10.1016/j.ailsci.2023.100073) can be used to cite this project:

M. A. Francisco Rodríguez, J. Carreras Puigvert, and
O. Spjuth. *Designing Microplate Layouts Using Artificial
Intelligence*, Volume 3, 2023. DOI: 10.1016/j.ailsci.2023.100073 [[PDF](https://doi.org/10.1016/j.ailsci.2023.100073)]

```bibtex
@article{PLAID2023,
	author = {Francisco Rodr\'iguez, Mar\'ia Andre\'ina and Carreras Puigvert, Jordi and Spjuth, Ola},
	title = {Designing Microplate Layouts Using Artificial Intelligence},
	year = {2023},
	doi = {10.1016/j.ailsci.2023.100073},
	URL = {https://doi.org/10.1016/j.ailsci.2023.100073},
	journal = {Artificial Intelligence in the Life Sciences},
	volume = {3}
}
```

<a name="publications"></a>
## Other Publications
M. A. Francisco Rodríguez, and O. Spjuth. *A Constraint
Programming Approach to Microplate Layout Design* In: J. Espasa and N.
Dang (editors), Proceedings of ModRef 2020, the 19th International
Workshop on Constraint Modelling and Reformulation, held at CP 2020,
September 2020.
[[PDF](https://modref.github.io/papers/ModRef2020_A%20Constraint%20Programming%20Approach%20to%20Microplate%20Layout%20Design.pdf)]
[[Slides](https://modref.github.io/slides/ModRef2020_Slides_A%20Constraint%20Programming%20Approach%20to%20Microplate%20Layout%20Design.pdf)]
[[Video](https://www.youtube.com/watch?v=naddH2TQIjE&ab_channel=CP2020)]


<a name="publications-using-plaid"></a>
## Publications Using PLAID

* L. Ju, A. Hellander, O. Spjuth
[Federated Learning for Predicting Compound Mechanism of Action Based on Image-data from Cell Painting](https://doi.org/10.1101/2024.02.09.579629)
bioRxiv preprint, May 2024.

* P. J. Harrison, A. Gupta, J. Rietdijk, H. Wieslander,
J. Carreras-Puigvert, P. Georgiev, C. Wählby, O. Spjuth, I. M. Sintorn
[Evaluating the utility of brightfield image data for mechanism of
action prediction](https://doi.org/10.1371/journal.pcbi.1011323)
PLOS Computational Biology, e1011323, July 2023.

* G. Tian, P. J. Harrison, A. P. Sreenivasan, J. Carreras Puigvert, and O. Spjuth.
[Combining molecular and cell painting image data for mechanism of action prediction](https://doi.org/10.1016/j.ailsci.2023.100060)
Artificial Intelligence in the Life Sciences, Volume 3, 2023.

* A. Gupta, P. J. Harrison, H. Wieslander, J. Rietdijk, J. Carreras Puigvert, P. Georgiev, C. Wählby, O. Spjuth, and I-M Sintorn.
[Is brightfield all you need for mechanism of action prediction?](https://www.biorxiv.org/content/10.1101/2022.10.12.511869v1)
bioRxiv preprint, October 2022.

* J. Rietdijk, T. Aggarwal, P. Georgieva, M. Lapins, J. Carreras Puigvert, and O. Spjuth.
[Morphological profiling of environmental chemicals enables efficient and untargeted exploration of combination effects](https://www.sciencedirect.com/science/article/pii/S0048969722021519)
Science of The Total Environment, 832:155058, August 2022.




<a name="references"></a>
## References

<a name="RefModRef2020">1</a>: M. A. Francisco Rodríguez, and O. Spjuth. *A Constraint
Programming Approach to Microplate Layout Design* In: J. Espasa and N.
Dang (editors), Proceedings of ModRef 2020, the 19th International
Workshop on Constraint Modelling and Reformulation, held at CP 2020,
September 2020.

<a name="RefMiniZinc">2</a>: Nethercote, N., Stuckey, P.J., Becket, R., Brand, S., Duck, G.J.,
Tack, G.: MiniZinc: Towards a Standard CP Modelling Language. In:
Bessière, C. (ed.) Principles and Practice of Constraint Programming –
CP 2007. pp. 529–543. Lecture Notes in Computer Science, Springer,
Berlin, Heidelberg (2007)


<a name="RefGecode">3</a>: Gecode Team: Gecode: Generic constraint development environment
(2019), available from http://www.gecode.org


<a name="license"></a>
## License

PLAID has an Apache 2.0 LICENSE. The PLAID team
accepts no responsibility or liability for the use of PLAID or any
direct or indirect damages arising out of its use.
