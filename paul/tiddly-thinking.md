I actually think this is one of the most important changes to make.

Right now the document jumps from:

> Generate multiple products...

to

> Here are some examples...

But those examples shouldn't be invented. They should emerge from a **systematic literature review**. That makes the toolkit defensible.

I'd replace that section with something like this.

```markdown
### Experimental Generation

For each case study, the project generates multiple AI-produced analytical products under controlled experimental conditions. The purpose is not simply to recreate the historical document, but to explore the range of analytical products that could reasonably be produced from the same analytical assignment and information environment.

The experimental products are organized into a standardized library of analytical templates. These templates are not developed ad hoc. Instead, they are identified, documented, and refined through a structured literature review of defense, intelligence, policy, and related analytic practice.

#### Literature Review of Analytical Products

The first objective is to identify the types of analytical products commonly produced by defense analysts, intelligence organizations, policy analysts, and related professional communities.

Sources may include

- Intelligence Community tradecraft publications
- DoD doctrine
- Joint Publications
- Army Techniques Publications
- Structured Analytic Techniques literature
- RAND reports
- Defense journals
- Think tank publications
- Government analytical guidance
- Academic literature on intelligence analysis
- Policy analysis textbooks and manuals

The review seeks to answer questions such as

- What analytical products are commonly produced?
- What purpose does each product serve?
- What information is expected?
- What organizational structure is used?
- What reasoning process does it embody?
- How is quality assessed?

#### Template Development

Each identified analytical product is converted into a standardized template suitable for experimental generation.

Each template documents

- product name
- intended audience
- analytical purpose
- expected inputs
- standard organizational structure
- required analytical components
- expected outputs
- evaluation criteria
- representative examples
- literature references supporting the template

Templates become reusable project artifacts and form part of the Analytical Toolkit.

#### Initial Template Library

The literature review is expected to identify products such as

Defense and Intelligence

- Intelligence Assessment
- Intelligence Information Report
- Situation Report (SITREP)
- Executive Summary
- Threat Assessment
- Warning Memorandum
- Strategic Estimate
- Risk Assessment
- Analysis of Competing Hypotheses
- Alternative Futures Analysis
- Indicators and Warning Assessment
- Decision Support Brief

Policy

- Policy Brief
- White Paper
- Congressional Testimony
- Executive Briefing

Research

- Literature Review
- Research Summary
- Technical Report
- Journal Article
- Annotated Bibliography

Additional analytical products may be incorporated as the literature review expands.

#### Experimental Matrix

Each historical case study is evaluated by generating every analytical product template under one or more controlled experimental conditions.

Experimental variables may include

- language model
- prompting strategy
- evidence package
- supporting data availability
- analytical framework
- model parameters

The resulting collection of analytical products provides a standardized basis for subsequent comparison and evaluation.
```

**I think there's an even larger architectural opportunity here.**

Every major section of the project could have this same pattern:

```
Overview

↓

Methodology Literature Review

↓

Toolkit Development

↓

Experimental Application

↓

Outputs
```

For example:

* **Corpus Construction**

  * Overview
  * Literature on corpus construction
  * Corpus protocol
  * Case-study implementation

* **Analytical Templates**

  * Overview
  * Literature review of analytic products
  * Template library
  * Experimental generation

* **Evaluation**

  * Overview
  * Literature review of evaluation frameworks
  * Scoring toolkit
  * Comparative analysis

That creates an **expandable document** where every high-level concept eventually grows into its own methodology chapter, and every methodology chapter is explicitly grounded in the literature rather than in project-specific decisions. I think that's a stronger research design and will make writing both the proposal documentation and the eventual publications much easier.
