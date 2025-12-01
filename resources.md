---
layout: page
title: Resources
subtitle: Potentially useful resources that I've collected over the years
---


# Research
## Databases
* X-ray Spectroscopy:
  * [X-ray Data Booklet](https://xdb.lbl.gov/) - Binding Energies, Emission Energies, Subshell Cross-Sections, almost too much info to list
  * [Center for X-ray Optics](https://henke.lbl.gov/optical_constants/) - X-ray Interactions with Matter (Transmission, Reflectivity, attenuation length, ect) 
  * [The International XPS Database](https://xpsdatabase.net/) - 5-10 X-ray Photoemission Spectra for most elements on the peridic table and many of their compounds
  * [International XAFS Database](https://ixdb.jxafs.org/) - Over 3000 X-ray Absorption Spectra organized by element and absorption edge. Pulls spectra from many other localized databases.
* Crystal Structures:
  * [Materials Project](https://materialsproject.org/) - Giant compendium of results from automated calculations (Band Structure, XANES, EXAFS) across crystal structures, as well as just a fast and easy place to spin around a crystal in 3D.
  * [Crystallography Open Database](http://www.crystallography.net/cod/) - Many crystalographic information files (CIFs). All materials are real.
  * [WebAtoms](https://millenia.cars.aps.anl.gov/webatoms) - Generate FEFF input files from crystallographic data

## Software
* Electronics Structure, DFT, Multiplets, ect:
  * [FEFF](https://feff.phys.washington.edu/) - XAS and EELS based on Cumulant Green's Function. Appropriate for excited states, NOT full potential.
  * [Abinit](https://www.abinit.org/) - Fundamentally a DFT code with a strong user base, but with a some many-body Green's function techniques stacked on (GW and DMFT)
  * Full potential DFT codes
    * [Wein2k](http://susi.theochem.tuwien.ac.at/) - Full-potential, linear augmented plane wave (LAPW) + local orbital
    * [FPLO](https://www.fplo.de/) - Full-potential local-orbital, minimal basis set, comparable accuracy to LAPW
    * [RSPt](https://www.physics.uu.se/research/materials-theory/ongoing-research/code-development/rspt-main/) - Full-potential Linear Muffin-Tin Orbital, beyond DFT methods DFT+U and DFT+DMFT
  * [Quanty](https://quanty.org/) - 2nd quantization multiplet code, written in C/C++, but has a scripting language written in Lua. It focuses on tools to solve the mathematics of quantum mechanics so you can focus on the physics.
  * [CTM4XAS](https://anorg.chem.uu.nl/CTM4XAS/software.html) - Similar to Quanty, but only interface is through a GUI, good for beginnners in the world of Multiplet Ligand Field Theory.
  * [MISSING](https://www.esrf.fr/computing/scientific/MISSING/) - Multiplet Inner-Shell Spectroscopy INteractive GUI (MISSING) provides a user interface for the famous "Cowan's Code" for performing atomic multiplet calculations.
  * [Gaussian](https://gaussian.com/) A very robust molecular quantum chemistry code with Hartree-Fock, DFT, and RASSCF capabilities. Also includes many tools for molecule building and visualizing outputs.
* X-ray Spectra Analysis
  * [Demeter Suite (Athena, Artemis, and Hephaestus)](https://bruceravel.github.io/demeter/) - Used for processing (background subtraction, Fourier transforming) and fitting of XAS data
  * [X-ray Larch](https://xraypy.github.io/xraylarch/) - Python based data analysis tool for processing XAS data with capabilities for visualizing multiple other types of spectroscopy (XRF, RIXS)

## Pedagogy
* [Bruce Ravel XAS Educational Materials](https://github.com/bruceravel/XAS-Education) - Source files for talks and demos done by Bruce Ravel

# Academics
## Textbooks
* Undergraduate
  * An Introduction to Mechanics 2nd Edition, Kleppner and Kolenkow, ISBN-13: 978-0521198110
  * Electricity and Magnetism 3rd Edition, Purcell and Morin, ISBN-13: 978-1107014022
  * A Modern Approach to Quantum Mechanics 2nd Edition, Townsend, ISBN-13: 978-1891389788
  * Introduction to Electrodynamics 2nd Edition, Griffiths, ISBN-13: 978-1108420419
  * Introduction to Quantum Mechanics 2nd Edition, Griffiths, ISBN-13: 978-1107179868
  * Gravity: An Introduction to Einstein's General Relativity 1st Edition, Hartle, ISBN-13: 978-1316517543
  * Thermal Physics 2nd Edition, Kittel and Kroemer, ISBN-13: 978-0716710882
  * Structure and Dynamics: An Atomic View of Materials 1st Edition, Dove, ISBN-13: 978-0198506782
  * Introduction to Elementary Particles 2nd Edition, Griffiths, ISBN-13: 978-3527406012
  * Physics at Surfaces 1st Edition, Zangwill, ISBN-13: 978-0521321471

* Graduate
  * Modern Electrodynamics 1st Edition, Zangwill, ISBN-13: 978-0521896979
  * Classical Electrodynamics 1st Edition, Jackson, ISBN-13: 978-0471431329
  * Modern Quantum Mechanics 3rd Edition, Sakurai and Napolitano, ISBN-13: 978-1108473224
  * Quantum Mechanics: Fundamentals 2nd Edition, Gottfried and Yan, ISBN-13: 978-0387220239
  * Elementary Statistical Physics Dover Edition, Kittel, ISBN-13: 978-0486435145
  * Chaotic Dynamics: An Introduction 2nd Edition, Baker and Gollub, ISBN-13: 978-0521476850
  * Theoretical Mechanics of Particles and Continua Dover Edition, Fetter and Walecka, ISBN-13: 978-0486432618 - *Sounds scary, but is really just graduate classical mechanics*
  * Nonlinear Dynamics and Chaos 2nd Edition, Strogatz, ISBN-13: 978-0813349107
  * Quantum Field Theory 1st Edition, Srednicki, ISBN-13: 978-0521864497
  * Quantum Field Theory and the Standard Model 1st Edition, Schwartz, ISBN-13: 978-1107034730
  * Many Body Quantum Theory in Condensed Matter Physics, Bruus and Flensberg, ISBN-13: 978-0198566335

## Notes, Lectures, and Talks
  * [David Tong Notes](http://www.damtp.cam.ac.uk/user/tong/teaching.html) - Everything from Vector Calculus to String Theory
  * [MIT Open Courseware](https://ocw.mit.edu/) - Recorded lectures on almost every possible topic, often with accompanying lecture notes, problem sets, and worked examples
  * [Kevin S. Huang Notes](https://kevinshuang.com/) - Slapdash of notes from various topics, as well as solutions to Townsend's A Modern Approach to Quantum Mechanics

## Research Experience for Undergraduates (REU) Applications
  * [Excellent Adventures, 5 tips for Summer Physics Research Opportunities](https://youtu.be/aSYsn3P_Hco) - *A somewhat juvenile but honest talk about summer research, with a focus on REUs*
  * [Excellent Adventures Talk Slide Deck](https://drive.google.com/file/d/1-nw-8L9PzAn2qfmek9cfqmXe9jiOuD5h/view?usp=share_link)
  * [REU Application Tips](https://drive.google.com/file/d/1H1ACHJCRNRPdC0QZ7B4cCSBkycVFqGnE/view?usp=share_link)
  * [Example Cold Email to a Professor](https://docs.google.com/document/d/1Zjh04BGa9egDgLRK97geXcvnTQCiOfid/edit?usp=share_link&ouid=104204760268694891005&rtpof=true&sd=true)
    ### Examples
    * [Charles Cardot (2019-2020)](https://drive.google.com/file/d/1EHmoTRgPilexVZcAXNTgHj-8U_1xFTyo/view?usp=share_link)
    * [Anonymous (2020-2021)](https://drive.google.com/file/d/1Om6tCMGfymb5nsQf-iHNLCSLTQ7mACDf/view?usp=share_link)
    * [Lazersmoke (2020-2021)](https://drive.google.com/file/d/1b4fI9Vefvsy61Cdjhj8bhuGPQQNYbS6-/view?usp=share_link)
    

## Graduate School Applications
* ### Random Literature
  * Getting In to Grad School for Physics: (or another physical science), Vincent Klug, ISBN-13: 978-1499732245 - *Would highly recommend*
  * [Applying to STEM Ph.D. Programs](https://github.com/gwisk/gradguide), George Iskander
  * [Get in to Grad School (General Advice)](https://docs.google.com/document/d/1Hx1L_4YAlQOxll7GBkSMxHfp2wTQMJT5/edit?usp=sharing&ouid=104204760268694891005&rtpof=true&sd=true), Unknown
* ### Example CV's
  * [Charles Cardot (2021)](https://drive.google.com/file/d/1VxjD6yLO4nmJDYrTyN2vFZi5PzU5IEL7/view?usp=share_link)
  * [Dmitriy Kim (2021)](https://drive.google.com/file/d/11cm2e3nHQtuDbk-l1Jyf7NVBvAFVGRR_/view?usp=share_link)
  * [Jonathan Destefano (2021)](https://drive.google.com/file/d/1if4UwBUyM1JmeqP5zg9iwi4aSyKuNvtJ/view?usp=share_link)
* ### Example Personal Statements
  * [Charles Cardot (2020-2021) Various](https://drive.google.com/drive/folders/1GWDzuJlerCClDG_0f1JR2akTs6gGau_I?usp=share_link)
  * [Dmitriy Kim (2020-2021) University of Michigan](https://drive.google.com/file/d/1scIEhiqds0LBsKycFBQ7Kka6Lj7OWgJJ/view?usp=share_link)
  * [Jonathan Destefano (2020-2021) Cornell](https://drive.google.com/file/d/1bIjHzJqnTxyjib1TNjrUwLCaZTz4R32f/view?usp=share_link)
  * [Robin Glefke (2020-2021) Template](https://drive.google.com/file/d/1fVpWfbc4LBix4DJWmeuFul3mpBey36Cb/view?usp=share_link)
  * [Robin Glefke (2020-2021) Berkley](https://drive.google.com/file/d/1o8GNFzq5EYKKoefvB_QQofbVSMwmW_k0/view?usp=share_link)
  * [Anonymous (2020-2021) Berkley](https://drive.google.com/file/d/1X-7uVzwiKu7VJcJ866VQ8N7HGZKYHVkk/view?usp=share_link)
* ### NSFGRFP
  * [Alex Hunter Lang's Website](https://www.alexhunterlang.com/nsf-fellowship)
