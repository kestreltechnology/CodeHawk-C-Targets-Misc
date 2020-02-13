# CodeHawk-C-Targets-Misc
Small C projects as demonstration targets for the
[CodeHawk-C Analyzer](https://github.com/kestreltechnology/CodeHawk-C)

## Description
This repository contains small C applications that have been
pre-parsed (on linux) and are ready for analysis with the
CodeHawk C Analyzer. The reason to provide a pre-parsed
version of the application is that all analyses will be
comparable. Local configuration and versions of standard
library header files may affect the proof obligations generated
and thus result in different analysis results for different
computers.

## Access from the CodeHawk-C analyzer

Add the following line to your chc/util/ConfigLocal.py file (if not
present, copy from chc/util/ConfigLocal.template):
```
    config.targets = {
        "misc": os.path.join(misctargets_home,'CodeHawk-C-Targets-Misc/targets/misc.json")
        }
```
where misctargets_home is assumed to hold your local path to the
CodeHawk-C-Targets-Misc directory. When registered in this way the
path
to the project can be specified with **misc:** followed by the name
of the project, e.g., **misc:file**, in every
script in the chc/cmdline/c-project directory. For example, to analyze
the **file** project listed below:
```
> export PYTHONPATH=$HOME/CodeHawk-C
> python chc_analyze_project.py misc:file --verbose
```
and to view the results when analysis is completed
```
> python chc_report_project.py misc:file
```

## Contents

### file

- *description*: an older version of the linux file utility
  [https://github.com/file/file](https://github.com/file/file)
- *size*: 20 .c files, 287 functions, 14,966 LOC
- *semantic size*: 7637 statements, 1860 calls, 2852 assignments
- *primary proof obligations*: 54,410
- *current analysis status*: 7911 open primary proof obligations
  (14.5%) (not yet proven)
  ([more detailed results](targets/file/latestresults/summaryresults.txt),
  broken down by file and proof obligation kind)
- *analysis time*: approximately 20 mins (single core), or
  8 mins (4 cores).
