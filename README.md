# Practical Computing for Population Health Research

Course materials for a **fictional** graduate course on computing practices for epidemiology and population health research. This was originally intended to be taught for the Department of Epidemiology and Population Health at Stanford University.

**[View the course website](https://mkiang.github.io/practical_computing/)** 

## What this is

I spent about 18 months interviewing PhD students, gathering notes, and cataloging gaps in what other Stanford courses cover. I wanted to make a class that would equip students with the basic computational skills I would want in a potential research assistant. The goal is a class that provides the meta-skills of computational work specific to population health research — project organization, reproducible workflows, version control, data wrangling at scale, and scientific communication.

I ended up being asked to teach a different course, so this is just a place to organize my thoughts and share them. I still think the material will be useful to new members of my lab.

## What this is not

**I have never actually taught any of this.** I don't know if the lectures are too long, the problem sets too easy, the slides too fast, or the notes in the wrong order. I'll keep updating as I assemble materials, but consider yourself warned. Use at your own risk.

This is not a statistics course, not a methods course, and not a coding course. It covers the workflows, tooling, and project infrastructure that make good science possible. R is the primary language but the principles generalize.

## A note on AI

This is also an exercise in incorporating AI into my workflow. I'm using AI to sort through my notes, flesh out outlines, find areas where my lecture notes lack clarity, draft Mermaid diagrams, check URLs, convert RMarkdown files to Quarto, and so on. I review everything, so all mistakes are my own.

## Planned schedule

| Week | Session | Type | Topic |
|-----:|--------:|------|-------|
| 1 | 01 | Lecture | The Scientific Computing Workflow |
| 1 | 02 | Lecture | Your Computer and the Shell |
| 2 | 03 | Lecture | Reproducible Research and Version Control with Git |
| 2 | 04 | Lab | Git/GitHub Setup Lab |
| 3 | 05 | Lecture | R Data Types, Structures, and Control Flow |
| 3 | 06 | Lab | R Foundations Lab |
| 4 | 07 | Lecture | Tidy Data and the Split-Apply-Combine Strategy |
| 4 | 08 | Lab | Tidy Data Lab |
| 5 | 09 | Lecture | Writing Functions and Abstraction |
| 5 | 10 | Lab | Functions Lab |
| 6 | 11 | Lecture | Data Visualization and Scientific Communication |
| 6 | 12 | Lab | Visualization Lab |
| 7 | 13 | Lecture | Working with Data Larger Than Memory |
| 7 | 14 | Lab | Big Data Lab |
| 8 | 15 | Lecture | Debugging, Profiling, and Speeding Up Your Code |
| 8 | 16 | Lab | Debugging Lab |
| 9 | 17 | Lecture | Working with Messy and Non-Tabular Data |
| 9 | 18 | Lab | Messy Data Lab |
| 10 | 19 | Lecture | Pipelines, HPC, and Putting It All Together |
| 10 | 20 | Lab | Pipelines Lab |

## Building the site

All materials are authored in [Quarto](https://quarto.org/) using [RStudio](https://posit.co/products/open-source/rstudio/). Lecture slides use the [quarto-revealjs-clean](https://github.com/grantmcdermott/quarto-revealjs-clean) extension by Grant McDermott. The site is deployed via GitHub Pages.

```bash
quarto render
```

Rendered HTML goes to `docs/`. Commit and push to update the live site.

## License

Materials are provided as-is for educational purposes. If you find them useful, great. If you find errors, let me know.
