# EPI XXX: Essential Computing in Epidemiology — Proposed Syllabus

> **Status:** DRAFT — awaiting instructor review.
> **Quarter:** Fall (10-week quarter + finals period)
> **Schedule:** 2× 1.5h sessions per week (flexible lecture/lab split)
> **Prerequisites:** Introductory R, introductory statistics

---

## Course Description

This course teaches the practical computing skills that epidemiologists and population health researchers need to do transparent, reproducible, and efficient work. It is not a statistics course or a methods course — it is a course about the infrastructure, workflows, and tools that make good science possible. Students will learn to organize projects, write clean code, work with data at scale, communicate results, and collaborate using modern tools. The course uses R as its primary language but the principles generalize.

---

## Weekly Schedule

### Week 1: The Scientific Computing Workflow / Your Computer and the Shell
**Theme:** What does a well-organized research project look like, and how does your computer actually work?
**Format:** Two lectures, no lab.

- **Lecture 1 (Session A):** Course overview. The research computing lifecycle. Why plain-text workflows matter. Project-oriented workflows vs. `setwd()` scripts. The `here` package. Introduction to the course project structure. How to get help: reading documentation, Google, Stack Overflow, making a reprex.
- **Lecture 2 (Session B):** What is a file system? Files, folders, paths (absolute vs. relative). The shell (bash/zsh). Essential bash commands (`ls`, `cd`, `pwd`, `cp`, `mv`, `rm`, `mkdir`, `cat`, `head`, `wc`, `grep`, `find`, pipes and redirection). Naming things well (Jenny Bryan's rules, hive-style naming, HMS conventions). Environment variables and dotfiles.
- **Key resources:** R4DS Ch. 6–8 (Workflow), rstats.wtf/projects, Good Enough Practices §1–2, MPTC Ch. 1–3, Jenny Bryan's "How to Name Files."

### Week 2: Reproducible Research and Version Control with Git
**Theme:** Making your work trustworthy, trackable, and collaborative.

- **Lecture:** What makes research reproducible vs. replicable? The reproducibility crisis in science. Principles of computational reproducibility: deterministic environments, literate programming, separation of code and data, documentation as a first-class output. Introduction to version control — why scientists need it. Git concepts: commits, branches, diffs, the staging area. GitHub: remotes, push/pull, cloning. `.gitignore` for sensitive data. Markdown for README files. Brief overview of collaborative flows (issues, pull requests) — to be used lightly for the rest of the quarter.
- **Lab:** Set up course infrastructure — install R/RStudio/Quarto (if not already done). Clone and configure a course project from the kianglab template. Initialize git, make commits, push to GitHub. Practice writing good commit messages. Set up SSH keys. Render a "hello world" Quarto document within the project.
- **Key resources:** Good Enough Practices §3–5, Sandve et al. (2013) Ten Simple Rules, Marwick et al. (2018) Research Compendium, Jenna Jordan's Git Novice Speedrun, MPTC Ch. 4–5.

### Week 3: R Foundations — Data Types, Structures, and Control Flow
**Theme:** Solidify the R fundamentals that everything else builds on.

- **Lecture:** Fast review of atomic types, vectors, lists, data frames, and tibbles. Logical indexing. Control flow: `if`/`else`, `for` loops, `while`. The difference between interactive use and programmatic use. When loops are fine and when they are not. Introduction to `purrr::map()` as an alternative.
- **Lab:** Exercises on vector operations, list manipulation, writing loops that process multiple files. Debug a broken script that has type coercion issues.
- **Key resources:** R4DS Ch. 1–5 (review), Advanced R Ch. 2–5.

### Week 4: Tidy Data and the Split-Apply-Combine Strategy
**Theme:** Most problems in public health can be broken into smaller problems.

- **Lecture:** What is tidy data? The three rules. `pivot_longer()` / `pivot_wider()`. The split-apply-combine paradigm. `dplyr` verbs: `filter`, `select`, `mutate`, `summarize`, `group_by` (and `.by=`). Joins with `join_by()`. Running example: calculate state-age-race-cause-specific mortality rates over time.
- **Lab:** Take a messy public health dataset (e.g., CDC WONDER extract or NVSS data), reshape it into tidy format, compute stratified summary statistics, and produce a clean output table.
- **Key resources:** R4DS Ch. 3–5 (Transform), Wickham (2014) "Tidy Data."

### Week 5: Writing Functions and Abstraction
**Theme:** If you copy-paste code more than twice, write a function.

- **Lecture:** Why abstraction matters. Anatomy of an R function. Arguments, defaults, return values. Scope and environments (brief). Defensive programming: input validation, informative error messages with `cli_abort()`. Iterating over functions with `purrr::map()` and friends. When to write a function vs. when to use `across()`.
- **Lab:** Refactor a long, repetitive analysis script into a set of well-documented functions. Write unit tests for one function using `testthat`. Apply the function across multiple datasets/subgroups.
- **Key resources:** R4DS Ch. 25–26, Advanced R Ch. 6.

### Week 6: Data Visualization and Scientific Communication
**Theme:** Figures, tables, and documents that communicate your findings.

- **Lecture:** Grammar of graphics and `ggplot2`. Choosing the right plot type for the data and audience. Color palettes for accessibility (colorblind-safe, print-safe). Multi-panel figures with `patchwork`. Publication-quality tables with `tinytable`. Quarto documents: YAML metadata, cross-references, citations, parameterized reports.
- **Lab:** Take the analysis from Weeks 4–5 and produce a complete Quarto report with a multi-panel figure, a formatted table, and proper cross-references. Render to HTML and PDF.
- **Key resources:** R4DS Ch. 1 (Visualize), ggplot2 book, tinytable docs, Quarto guide.

### Week 7: Working with Data Larger Than Memory
**Theme:** What to do when `read.csv()` isn't enough.

- **Lecture:** When and why data get big. Introduction to SQL and relational thinking. DuckDB as an embedded analytical database. `dbplyr` for writing SQL from dplyr. Apache Arrow and the `arrow` package for out-of-core computation. Strategies: sampling, stratifying the problem, lazy evaluation. Brief mention of cloud data warehouses.
- **Lab:** Load a large dataset (~10 GB) that does not fit in memory. Write SQL queries via DuckDB. Use `arrow` to filter and aggregate a partitioned Parquet dataset. Compare performance to naive `read.csv()` + `dplyr`.
- **Key resources:** Scaling Up with R and Arrow, DuckDB docs, dbplyr vignette.

### Week 8: Debugging, Profiling, and Speeding Up Your Code
**Theme:** When your code is wrong or slow.

- **Lecture:** Debugging strategies: `browser()`, `debug()`, `traceback()`, RStudio breakpoints. Reading error messages. Common R pitfalls. Profiling with `profvis`. Benchmarking with `bench::mark()`. Vectorization. Parallelization with `furrr` and `future`. When to optimize and when not to.
- **Lab:** Profile a slow analysis script, identify the bottleneck, and optimize it. Practice using the debugger on a script with a subtle bug. Parallelize a simulation study.
- **Key resources:** Advanced R Ch. 23–24, profvis docs.

### Week 9: Working with Messy and Non-Tabular Data
**Theme:** Not all data arrive as clean CSVs.

- **Lecture:** APIs and web data: `httr2` for REST APIs, `rvest` for web scraping (ethical considerations). Working with JSON and nested lists (`jsonlite`, `tidyr::unnest()`). Free text and string processing with `stringr` and regular expressions. Brief intro to other data formats: spatial (sf), dates/times (lubridate/clock), survey data.
- **Lab:** Pull data from a public health API (e.g., CDC SODA API or WHO GHO), parse the JSON response, clean it, and merge it with a local dataset. Practice regex on a messy text field.
- **Key resources:** R4DS Ch. 14–16 (Strings, Regex, Factors), httr2 vignette.

### Week 10: Pipelines, HPC, and Putting It All Together
**Theme:** Tools for scaling and automating your workflow.

- **Lecture:** Analytic pipelines with `targets` — why and how. SSH and remote servers. Introduction to SLURM and high-performance computing. Job arrays for embarrassingly parallel problems. Environment management (`renv`). A brief look forward: Docker, continuous integration, R packages as research compendiums.
- **Lab:** Convert a multi-script analysis into a `targets` pipeline. Submit a SLURM job array that runs a simulation across parameter values. Use `renv` to snapshot the project environment.
- **Key resources:** targets manual, SLURM docs, renv vignette.

### Finals Period: Project Presentations
- Students present their independent projects to the class.
- Projects must be fully reproducible by a different person (verified by peer review).
- Brief Q&A and constructive feedback.

---

## Assessment Structure (Proposed)

| Component | Weight | Notes |
|-----------|--------|-------|
| Weekly labs | 40% | Submitted via GitHub; graded on completion and code quality |
| Problem sets (3–4) | 20% | Roughly every 2–3 weeks; more challenging than labs |
| Final project | 30% | Reproducible analysis; includes code, Quarto report, GitHub repo |
| Participation | 10% | Attendance, peer code review, class discussion |

---

## Final Project (Hybrid Model)

- **Weeks 1–5:** Scaffolded assignments build components of a reproducible project (project setup, version control, data pipeline, functions, tests).
- **Weeks 6–10:** Students propose an independent project related to their own research. Must incorporate: version control, tidy data principles, at least one function, a Quarto report with figures/tables, and a reproducible workflow.
- **Finals:** Oral presentation + peer reproducibility review.

---

## Course Materials Per Week

For each of the 10 content weeks, the following materials will be produced:

1. **Lecture notes / reading** — a Quarto document (`.qmd`) serving as the primary reference.
2. **Slide deck** — a Quarto Reveal.js presentation using the `quarto-revealjs-clean` theme.
3. **Problem set / exercises** — practice problems with a corresponding answer key.
4. **Lab handout** — step-by-step lab instructions (may be combined with the problem set for some weeks). Note: Week 1 has no lab (two lectures instead).

---

## Open Questions

1. **Computing environment:** Will students use their own laptops, or will Stanford provide a shared environment (e.g., via FarmShare, Stanford JupyterHub, or an LTS/UIT solution per Kenji's suggestion)?
2. **Grading:** S/NC vs. letter grade? This may affect enrollment.
3. **TA support:** Will there be a TA or course assistant for grading and office hours?
4. **Course proposal:** Still need to write up the formal proposal — get example from Steve Goodman.
5. **Cross-listing:** Should this be cross-listed with another department (e.g., STATS, BIOMEDIN)?
6. **AI policy:** What is the course stance on AI-assisted coding (Copilot, ChatGPT)? (Note the bookmarked paper on cognitive debt from AI assistants.)
