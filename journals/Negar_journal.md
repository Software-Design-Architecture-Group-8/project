# Individual Journal - Negar

* **Project:** Prettier
* **Group Number:** 8
* **Reporting Period:** Week 1 (May 2026)

---

## Activity Summary 1
* **Effort:** 4 hours
* **Activity:** Evaluation of Software Module Dependencies (Static Analysis)

### Tasks Performed:
* Partnered with **Shayan** to perform a static analysis of the Prettier codebase using the `dependency-cruiser` tool.
* Focused on isolating the core logic by refining the analysis scope; specifically excluded `node\_modules`, `docs`, and `\_\_tests\_\_` to obtain a clear view of the production architecture.
* Generated and interpreted various visualization outputs, including Dependency Matrices and collapsed folder-level graphs.
* Evaluated the structural role of specific "high-traffic" files, such as the ESTree and TypeScript dispatchers, to determine the rationale behind their high degree of coupling.
* Investigated isolated utility files (e.g., in `language-yaml`) to document examples of high modularity within the system.

### Contribution to the Main Report:
* Co-authored the **Software Design - Dependencies** section.
* Responsible for the "Static Dependency Results" subsection, focusing on the identification and justification of files with the most and least dependencies (In-degree/Out-degree analysis).

---



## Activity Summary 2
* **Effort:** 4 hours
* **Activity:** Evaluating co-change metrics and knowledge dependencies.
* **Reporting Period:** Week 2 (May 2026)

### Tasks Performed:
* Teamed up with **Shayan** to process the Git commit history of Prettier (`src/` directory) source to identify file couplings.

### Contribution to the Main Report:
* Drafted the methodology and findings for **Section 2: Knowledge Dependencies** within the Software Design Report.

---