# multiplate-designer

**LayoutCreator** (I'm still working on the name!) is a flexible
constraint-programming model representing the Plate Layout Design
problem. **LayoutCreator** was developed with the goal of helping
researchers plan well-designed experiments by creating a robust
microplate layout and thus reducing the rate of (partial) microplate
rejection.[^1]

**LayoutCreator**  is easy and straightforward to use. The current
model guarantees the following constraints:

* The outermost rows and columns can be left empty in order to reduce
errors due to the edge effect.
* For each compound or combination thereof:
  - all concentration levels of a given replica appear on the same
  plate.
  - each concentration level appears on a different row and column.
* If possible, the replicated compounds and combinations appear on a
different plate.
* For each type of control and concentration, the difference in number
between plates is at most 1.
* Controls of the same kind are separated by at least 1 well in any
direction.
* If empty wells are allowed (other than those used to reduce the edge
effect), they are placed as close to the border as possible.

Using **LayoutCreator** does not require any programming knowledge.
Users just need to write down the necessary information such as number
of compounds, combinations, controls, etc in a simple text file and
click run!

The output is a list in .csv format containing plate ID, well, content
(compound, combination or control), concentration, and latex name,
meant to be used as input for automatic tools. (TODO: visualize the
layout using latex)

We believe **LayoutCreator** is the first attempt to use constraint
programming to design microplate layouts. Due to the use of MiniZinc,[^2]
a high level constraint modelling language, **LayoutCreator** is
highly customizable.



## Table of Contents
* [Installation and Usage](#installation)
  - [Using the MiniZinc IDE](#minizinc-ide)
  - [Using the command line](#command-line)
* [References](#references)


<a name="installation"></a>
## Installation and Usage

* Download and install [MiniZinc](https://www.minizinc.org/).
* Clone this repo or download our model plate-design.mzn located in this repository.
* Fill in the specific details of your experiment in a a copy of
empty-file.dzn. Alternatively, you can modify any of the example .dzn
files. (TODO: add an example input file in JSON)


<a name="minizinc-ide"></a>
### Using the MiniZinc IDE 
* Select Gecode as solver.[^3]
* Run!
* You can change the random seed to obtain a different layout for the
same input file.


<a name="command-line"></a>
### Using the command line
* Type something and magic happens!


<a name="references"></a>
## References

[^1]: M. A. Francisco Rodríguez, and O. Spjuth. *A Constraint
Programming Approach to Microplate Layout Design* In: J. Espasa and N.
Dang (editors), Proceedings of ModRef 2020, the 19th International
Workshop on Constraint Modelling and Reformulation, held at CP 2020,
September 2020.
[PDF](https://modref.github.io/papers/ModRef2020_A%20Constraint%20Programming%20Approach%20to%20Microplate%20Layout%20Design.pdf)
[Slides](https://modref.github.io/slides/ModRef2020_Slides_A%20Constraint%20Programming%20Approach%20to%20Microplate%20Layout%20Design.pdf)
[Video](https://www.youtube.com/watch?v=naddH2TQIjE&ab_channel=CP2020)


[^2]: Nethercote, N., Stuckey, P.J., Becket, R., Brand, S., Duck, G.J.,
Tack, G.: MiniZinc:Towards a Standard CP Modelling Language. In:
Bessière, C. (ed.) Principles andPractice of Constraint Programming –
CP 2007. pp. 529–543. Lecture Notes inComputer Science, Springer,
Berlin, Heidelberg (2007)


[^3]: Gecode Team: Gecode: Generic constraint development environment
(2019), avail-able fromhttp://www.gecode.org
