# Task2Test

**Tool-Support for Task-Based User Interface Testing**

Master’s thesis research prototype, Shahrukh Amanat, University of Rostock, 2026.

## Overview

Task2Test supports the reuse of ConcurTaskTrees (CTT) models for generating normative abstract test cases and representative mutated test cases, and preparing GUI test automation. It imports CTTE XML models, reconstructs task relationships, generates Gherkin-style scenarios, supports manual GUI action mapping and traceability, and exports CSV files, Playwright test skeletons and a reduction report.

## Getting started

1. Download this repository using **Code → Download ZIP** and extract it.
2. Open `index.html` in a modern browser (Chromium/Chrome or Edge).
3. Use the XML file chooser to import one of the files in `examples/`.
4. Inspect the automatically generated normative cases and mutation groups.
5. Enter application-specific selectors, test data and expected results in the GUI action mapping panel where applicable.
6. Inspect or export the scenarios, mappings, traceability information, Playwright skeletons and reduction report.

No backend or package installation is required. The Playwright export is a skeleton, not a ready-to-run test suite for a concrete application.

## Example models and reproduction

Use the default prototype settings. The following results were obtained by importing the supplied XML models in Chromium.

| Model | Normative cases | Raw mutation candidates | Reported mutation groups |
| --- | ---: | ---: | ---: |
| [ATM](examples/ATM.xml) | 22 | 156 | 11 |
| [Pizza ordering](examples/Pizza_ordering.xml) | 48 | 536 | 10 |
| [Basic Login](examples/Login_Basic.xml) | 4 | 12 | 3 |

The ATM and Pizza ordering models reproduce the normative and reported mutation-group counts in Chapter 4. The Basic Login model is a supplementary example and is not the extended Login model used in Chapter 3.

### Reproduction note

The available Pizza ordering XML and prototype produce 536 raw candidates (416 omission, 24 sequence, 48 Choice and 48 Disabling). Of these, 80 are exact duplicates, 104 match the generated normative set after exact deduplication, and 342 repeated target occurrences are collapsed, leaving 10 representative groups. The reviewed thesis version records 512 raw candidates and 398 grouped candidates; the current run reports 536 and 422 respectively. The normative count and representative group count match. The origin of this discrepancy in the earlier evaluation has not been established. See Chapter 4, Pizza ordering mutation results.

The reported groups are automated outputs. The thesis's manual review retains 9 ATM and 10 Pizza ordering groups, corresponding to 8 and 9 distinct executable sequences respectively. These manual results are not automatically produced by the prototype.

## Scope and limitations

Task2Test uses bounded expansion of supported CTT relationships. Exact comparison with generated normative sequences is not a complete semantic validity check. Application-specific GUI mappings and expected responses must be supplied by the tester. The prototype does not execute GUI tests. Semantic-aware mutation checking and linked views of mutation groups and distinct executable sequences are proposed future work, not implemented features.

## Model provenance

- ATM: adapted from the example model distributed with the ConcurTaskTrees Environment (CTTE), with the deposit and information branches decomposed into subtasks in the supplied evaluation model. Credit remains with the original model authors.
- Pizza ordering: model prepared for the thesis demonstration.
- Basic Login: supplied supplementary Login example.

The example XML files are preserved byte-for-byte; only their filenames have been changed. They retain CTTE export metadata, including legacy local paths and DTD declarations. These paths are not required for browser-based use in Task2Test. Redistribution permissions for third-party example material should be confirmed before public publication.

## Academic context

This repository accompanies the master's thesis *Tool-Support for Task-Based User Interface Testing*. The HTML prototype is the final cosmetically corrected submission version; the generation algorithms have not been intentionally changed for this package.
