---
title: Reproducible Science  
author:
- Andrés Aravena
- Patricio Reyes
date: 2021-11-05
slideOptions:
    transition: 'slide'
---

# Hello :hand:


<!-- .slide: data-background="https://media.giphy.com/media/26xBwdIuRJiAIqHwA/giphy.gif" -->

----

## Andrés Aravena

- Assistant Professor at Istanbul University (Molecular Biology and Genetics Department)
- [Blog of Andrés Aravena](http://dry-lab.org/)
    - [Methodology of Scientific Research](http://dry-lab.org/blog/2020/msr/)

----

## Patricio Reyes

- researcher at BSC, [Data&Vis Team](http://bsc.es/viz/)
- member of PyBCN
- urban mobility/planning
- repos
    - [cuentalo](https://github.com/BSCCNS/cuentalo-dataset)
    - [Landscape Steiner](https://github.com/pareyesv/landscape_steiner) ==looking for collaborators==
- twitter: @pareyesv
- github: [pareyesv](https://github.com/pareyesv)

----

## ==You ?==

---


## Summary 

----

- Reproducible and collaborative science
    - intro to reproducible, collaborative and transparent science
    - reproducible writing
        - tools: bibliography managers (Zotero), LaTeX, pandoc, markdown, Rmarkdown, version control, cloud services (Overleaf, Authorea)

----

- How to structure a data-driven project
    - tools: cookiecutter data-science template

----

- Ethics in Research
    - Research integrity
    - tools: ethics checklists for data science

----

- Open Access
    - open access guidelines at BSC
    - tools: zenodo, figshare, FAIR

---

# Questions

- [ ] data-driven thesis?
- [ ] do you have to write code?
    - which language? :nerd_face: 

---

# Intro

----

- `doc-v1-real-final2-4.docx`
    - [PHD Comics: notFinal.doc](https://phdcomics.com/comics/archive.php?comicid=1531)

---

# Reproducible Science

- Reproducible science ([repeatable/replicable/reproducible](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5778115/))
- Collaborative science
- Transparent science

---

# How to structure a data project

----

- Part of the course [ibda2021](https://github.com/pareyesv/ibda2021)
- [DataViz has a cookiecutter template](https://github.com/BSCCNS/cookiecutter-data-science-conda) (internal)

----

## collaboration :handshake:

- slack/rocket-chat is not enough!
- team, team, team

----

## 1. "I work alone. I don't care" :sunglasses: 

- you collaborate with yourself
- your _future self_ will need
    - documentation
    - debugging

----

## you always need to ==collaborate==

- looking for advice
    - blogs: bloggers share knowledge
    - books: authors share knowledge
- beta-testing
    - you are not the best programmer to test your own code
- why don't you ask for collaboration?!?!

----

## 2. "I work on a team"

- your _future self_ is part of the same team
    - smart member :nerd_face: 
    - your _future self_ will need documentation
- you (your code) have to interact with others
    - documentation
    - README file
    - end-user
        - how to run the code?
    - developer
        - how to start working on the code?

----

## reproducibility

- [Reproducibility PI Manifesto :: Lorena A. Barba Group](https://lorenabarba.com/gallery/reproducibility-pi-manifesto/)
- [slides](https://speakerdeck.com/labarba/how-to-run-a-lab-for-reproducible-research)

----

## Data Science Template

- [Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/)
    - [You will thank you](https://drivendata.github.io/cookiecutter-data-science/#:~:text=You%20will%20thank%20you)

----

## Install the template

- [data science template](https://drivendata.github.io/cookiecutter-data-science/#example)

----

## Directory Structure

- [structure](https://drivendata.github.io/cookiecutter-data-science/#directory-structure)

----

## Data is immutable

- ==Don't ever edit your raw data==
    - especially not manually...
    - ...and especially not in Excel 
- ==Don't overwrite your raw data==
- Treat the data (and its format) as immutable.
- data folder in `.gitignore`

----

## Data version control

- databases
- [Data Version Control · DVC](https://dvc.org/)
- [Git Large File Storage](https://git-lfs.github.com)
- [AWS Amazon Simple Storage Service (S3)](https://aws.amazon.com/s3/)

----

- Data science project template
    - templates
    - documentation
    - README files
    - LICENSE
    - semantic versioning
    - collaboration
        - issues
        - Pull Requests

----

- tools
    - Github
    - CookieCutter
        - See also: [Copier](https://github.com/copier-org/copier)
    - Sphinx
        - mkdocs

----

## Reproducible results

- data version control
- reproducible environment
    - pinned dependencies (python: `requirements.txt`, conda `environment.yaml`, [poetry `pyproject.toml`](https://python-poetry.org/docs/dependency-specification/))
      ```python
      # requirements.txt
      pandas==1.3.4
      ```

----

## Reproducible notebooks

- [IPython watermark](https://github.com/rasbt/watermark#examples)
    - [PyMC Jupyter Notebook Style Guide · pymc-devs/pymc Wiki](https://github.com/pymc-devs/pymc/wiki/PyMC-Jupyter-Notebook-Style-Guide#watermark)
    - [example notebook](https://github.com/rasbt/watermark/blob/master/docs/watermark.ipynb)
- papermill


----

### ==papermill== + nbconvert

- run notebooks from command line
    - parameterize
        - from command line
        - from yaml config file
    - inject variables into the notebook
        - [cell tagged `parameters`](https://papermill.readthedocs.io/en/latest/usage-parameterize.html)
- See [how Netflix uses papermill](https://netflixtechblog.com/scheduling-notebooks-348e6c14cfd6)

----

### papermill + ==nbconvert==

- jupyter notebook $\rightarrow$ webpage (html)
- [how to](https://nbconvert.readthedocs.io/en/latest/usage.html)

----

- further reading:
    - [Automated Report Generation with Papermill: Part 1 - Practical Business Python](https://pbpython.com/papermil-rclone-report-1.html) 
    - [Automated Report Generation with Papermill: Part 2 - Practical Business Python](https://pbpython.com/papermil-rclone-report-2.html)

---

# Versioning

----

## [Semantic Versioning](https://semver.org/) for your thesis?

- idea
    - start with `chore: first commit` $\rightarrow$ `v0.1.0`
    - `feat: add first draft of chapter 1` $\rightarrow$ `v0.2.0`
    - `fix: correct error in formula` $\rightarrow$ `v0.2.1`


----

- automatic bump-version software
    - local
    - github action or similar
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [commitizen](https://commitizen-tools.github.io/commitizen/)

---

## FAIR Data Management Plan

----

- European Union ==FAIR==
    - [How to make your data FAIR](https://www.openaire.eu/how-to-make-your-data-fair)
    - [Box 2: The FAIR Guiding Principles](https://www.nature.com/articles/sdata201618)
    - [data management, section 2](https://ec.europa.eu/research/participants/data/ref/h2020/grants_manual/hi/oa_pilot/h2020-hi-oa-data-mgt_en.pdf)

---

# The hard road to reproducibility

----

## Reproducibility

- [The hard road to reproducibility](https://www.science.org/doi/full/10.1126/science.354.6308.142)
- [[98] Evidence of Fraud in an Influential Field Experiment About Dishonesty - Data Colada](http://datacolada.org/98)
- [ReScience C](http://rescience.github.io/)
- [REANA - Reusable Analyses](https://reanahub.io)

----

## Reproducibility in HPC


- [12 Ways to Fool the Masses with Irreproducible Results :: Lorena A. Barba Group](https://lorenabarba.com/figshare/12-ways-to-fool-the-masses-with-irreproducible-results/)

---

# Ethics & AI

----

- [Data science ethics checking list](https://deon.drivendata.org/#default-checklist)
- [Ethics AI strategy](https://www.google.com/url?sa=t&source=web&rct=j&url=https://bionic-h2020.eu/wp-content/uploads/2020/08/D9.5-Ethics-Strategy.pdf&ved=2ahUKEwjj84_73anyAhUO14UKHZKXDC8QFnoECC0QAQ&usg=AOvVaw22awnXP9Boqtte3wVBxXwl)
- [Ethics & fairness assessment](https://op.europa.eu/es/publication-detail/-/publication/d3988569-0434-11ea-8c1f-01aa75ed71a)
- [Ethics self-assessment](https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/common/guidance/how-to-complete-your-ethics-self-assessment_en.pdf)


---

# Open Access

----

- who owns the rights to your articles?
    - the publisher?
    - the authors?
- [Why Open Access? - PLOS](https://plos.org/open-science/why-open-access/)
- [Gold open access and green open access: what's the difference?](https://www.publisso.de/en/no_cache/advice/publishing-advice-faqs/difference-between-gold-and-green-open-access/)

----


## Zenodo

- upload project versions to [Zenodo](https://zenodo.org/)
    - funded by EU
    - maintained by CERN

----

## Examples

- cuentalo dataset
    - [BSCCNS/cuentalo-dataset: Dataset used in http://proyectocuentalo.org/](https://github.com/BSCCNS/cuentalo-dataset#citing-the-dataset)
    - [v0.1.1](https://zenodo.org/record/2585527)
    - [all-versions](https://doi.org/10.5281/zenodo.2585526)
- [urbana](https://zenodo.org/record/5484501)

----

## Figures

- DOI for figures
    - Figshare
        - [How to Share, Cite or Embed your data - a help article for using figshare](https://help.figshare.com/article/how-to-share-cite-or-embed-your-data)

----

- examples: 
    - Alonso Silva's tweet
        - [Alonso Silva's figure](https://twitter.com/patagon_swing/status/1412470060833193986)
        - [Tasa de incidencia acumulada vs pobreza multidimensional](https://figshare.com/articles/figure/Tasa_de_incidencia_acumulada_vs_Pobreza_multidimensional/13010390/2)
            - Cite
                - DataCite
                - BibTeX

----

- Lorena Barba's papers
    - [[2008.05414] Reproducible Validation and Replication Studies in Nanoscale Physics](https://arxiv.org/abs/2008.05414), [p 16](https://arxiv.org/pdf/2008.05414.pdf)
- PLOS ONE figures
    - [A city of cities: Measuring how 15-minutes urban accessibility shapes human mobility in Barcelona](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0250080)
- PeerJ CS
    - [JOSS: design and first-year review. PeerJ Computer Science 4:e147](https://doi.org/10.7717/peerj-cs.147)

----

## Open Access at BSC

- [Info & guidelines](https://intranet.bsc.es/help-and-support/rstd-services/documentation-publications-unit) (intranet BSC)

----

The documentation unit goals are:

1. Ensure that BSC's Open Access obligations to publications are covered.
2. Provide help to compile and standardise bibliographic data of the centre's scientific production.
3. Provide support to BSC's researchers in the creation and update of their CV in ORCID or Researcher ID. (compulsory for all researchers).
4. Help with and inform about all BSC bibliographic and bibliometric issues in general. (Particular attention to correct use of affiliation).

----

> Katia Pistrin
> Documentalist and Personnel Grants Manager
> Barcelona Supercomputing Center
> documentation@bsc.es

---

# Cloud services for scientific writing

----

- Overleaf
    - LaTeX cloud
- Authorea
    - markdown, LaTeX cloud 

---

# References

----

- Bibliography managers
    - Zotero
        - [Tutorial: Getting Started with Zotero 4 - YouTube](https://www.youtube.com/playlist?list=PLXt-tu7G1H3vlRXLmGyOzeAp7ZKDK0pty)

----

- Scholarly Writing Environment
    - [Setting Up a Scholarly Writing Environment With Markdown, VSCodium and pandoc - YouTube](https://www.youtube.com/watch?v=J86Pm62XM_Q&t=5189s)

----

- notetaking systems/apps
    - [Markdown: Academic Writing in Plain Text - YouTube](https://www.youtube.com/playlist?list=PLXt-tu7G1H3tLeZgbbUmYjE0_kvbjA4YU)
    - [Markdown vs latex for thesis - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/418962/markdown-vs-latex-for-thesis)

---
