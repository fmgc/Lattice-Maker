#Lattice Maker

##Requirements

*	Java (>= 6)
*	Python (>= 2.7, < 3.0)
*	GraphViz (>= 2.28)
	
##Installation

* For WINDOWS:
	1. Install [Java](http://www.java.com/), [Python](http://python.org/download/) and [GraphViz](http://www.graphviz.org/)
	2. Edit `run.bat` and update where Java & Graphviz are in your computer (lines 8-9)
	
* For UNIXes (including OSX):
	1. Install required packages
	2. have fun.

##Usage

To define the required lattice read `latticeMaker.cgs` initial comments and change the list of games and the number of days at the end of the file.

To use, execute batch `make` (if windows) or `run` (if *nix).

Three latex files are produced:
 * `graph.tex`		-- a pstricks lattice description
 * `graph_tiny.tex`   -- the same lattice but with short labels
 * `graph_labels.tex` -- a latex table with the caption for `graph_tiny.tex`
 
The descriptions use a list of newcommand's that need to be included in your latex file (check below for an eg)

##Appendix

Latex template (cf. `doc.tex`):

	\documentclass[11pt]{article}
	\usepackage{geometry}
	\geometry{a4paper}

	\usepackage{auto-pst-pdf}	
	\usepackage{pstricks}
	\usepackage{pstricks-add}
	\usepackage{pst-node}

	\newcommand{\Pow}[2]{{#1}^{#2}}
	\newcommand{\PowTo}[2]{{#1}^{-[#2]}}
	\newcommand{\Frac}[2]{\frac{#1}{#2}}
	\newcommand{\Miny}[1]{+_{#1}}
	\newcommand{\Tiny}[1]{-_{#1}}
	\newcommand{\UpGame}{\uparrow}
	\newcommand{\DownGame}{\downarrow}
	\newcommand{\StarGame}{\ast}
	\newcommand{\MoreLess}{\pm}
	
	\begin{document}
	
		\psset{unit=0.45cm}			   % adjust change space between nodes
		\begin{center}
			\scalebox{1.0}{			   % adjust overall scale
				\begin{pspicture}(30,40)  % adjust area where lattice appears
					\input{graph.tex}
				\end{pspicture}
			}
		\end{center}
		
		\psset{unit=0.4cm}				% adjust space between node
		\begin{center}
			\scalebox{0.8}{			   % adjust overall scale
				\begin{pspicture}(30,60)  % adjust area where lattice appears
					\input{graph_tiny.tex}
				\end{pspicture}
			}
		\end{center}
		
		\input{graph_labels.tex}
	\end{document}  
