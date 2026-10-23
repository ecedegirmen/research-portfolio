# Research workflow and publication plan

[Back to portfolio](../README.md)

This guide sets out the workflow I intend to use as the portfolio develops. It is a working standard, not a claim that every project has already completed every step.

## 1. Start with a question that the evidence can answer

For each project, record the question, motivation, population, unit of observation, time period, outcomes, and intended audience. Identify whether the aim is description, prediction, causal inference, or model-based explanation. Revise the question when the data cannot support the original scope, and record why.

**Evidence to retain:** a short research plan and dated notes on major decisions.

## 2. Document the data before transforming it

Maintain a source register containing:

| Field | What to record |
| --- | --- |
| Source and file | Publisher, exact URL, file/table name, release/version |
| Access | Retrieval date, access conditions, and any redistribution limits |
| Coverage | Population, geography, years, frequency, and unit of observation |
| Measures | Definitions, units, denominators, and uncertainty where applicable |
| Comparability | Changes in definitions, boundaries, collection, or coverage |
| Processing | Input filename, transformation script, and resulting output |

Keep original inputs unchanged. Share public data only when redistribution is permitted; otherwise provide access or download instructions. Do not include credentials, personal records, or confidential employer materials.

## 3. Build a traceable preparation process

Use scripts for repeatable cleaning. Document type conversions, missing-value decisions, duplicate handling, joins, exclusions, and constructed variables. Check row counts and key uniqueness before and after joins. Investigate implausible values rather than silently removing them.

**Evidence to retain:** cleaning code, a variable dictionary, and a brief data-quality summary.

## 4. Make the analysis match the question

- **Descriptive work:** state the sample, denominator, missingness, and uncertainty.
- **Prediction:** separate training and evaluation data appropriately; compare with a useful baseline and check leakage.
- **Causal inference:** explain the comparison, identification assumptions, potential confounding, and relevant diagnostics.
- **Numerical modeling:** document equations, assumptions, convergence, and sensitivity to computational choices.
- **Accessibility analysis:** state travel assumptions, schedule versions, origins, and the feasibility of return journeys.

These are project-dependent choices. A sophisticated method is useful only when its assumptions and data requirements are defensible.

## 5. Make results reproducible

When code is added, each project should include:

- Exact input sources or access instructions.
- An environment/dependency specification appropriate to its tools.
- An ordered set of commands or notebook instructions.
- Relative paths and a documented output location.
- Random seeds where relevant.
- A record of a successful fresh run and any remaining limitations.

Do not describe a project as reproducible until someone can follow those instructions and obtain the reported outputs.

## 6. Present the same work at two levels

**Overview:** the question, why it matters, the main supported result when available, and the most important limitation.

**Technical detail:** data construction, methods, assumptions, diagnostics, interpretation, references, and execution instructions.

Figures should state units, sample/time coverage, sources, and uncertainty where relevant. Keep outputs visibly tied to the code that generates them. Credit collaborators and distinguish supplied coursework code from original contributions.

## 7. Maintain an honest progress record

Use stages that describe what is actually available:

1. Question and scope.
2. Data inventory and feasibility.
3. Cleaning and exploratory analysis.
4. Main analysis and diagnostics.
5. Reproduction and written interpretation.
6. Public release.

Record meaningful decisions and new evidence as the work happens. Label preliminary outputs and update conclusions when the evidence changes.

## First development milestones

| Project | Next concrete evidence to add |
| --- | --- |
| Opportunity Scholarship | Exact source inventory, available years/geographies, and a feasible research question |
| Transportation access | Selected geography and a verified sample of destinations, class times, and transit schedules |
| Austin Animal Center | Current team question, contribution statement, and a documented cleaning/analysis example |
| Firm-investment model | Original notebook, assignment context, and a verified fresh run |

## Suggested structure as analysis files become available

Create these directories only when there is content to place in them:

- `src/`: reusable preparation and analysis scripts.
- `notebooks/`: exploratory or explanatory notebooks.
- `data/`: documentation and permitted inputs; keep restricted files out of Git.
- `outputs/figures/`: selected generated figures.
- `reports/`: research notes, briefs, or papers.
- `environment/`: dependency files and setup instructions.

Each project's README should link directly to its strongest available artifacts and state what remains in progress.
