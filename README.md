# CBE Assessment Operationalisation Review: Replication Package

Replication data for the systematic review:

> Heradio, R., & Vargas, H. (2026). *From Declared Competency to Graded Assessment:
> A Systematic Review of Operationalisation in Engineering and STEM Higher Education.*
> Journal of Engineering Education. (under review)

This repository archives every artifact produced during the **record identification**
and **study selection** phases of the review, enabling full replication of the
PRISMA 2020 study selection process.

---

## What this review is about

Engineering and STEM higher education programmes increasingly ground their
curricula in Competency-Based Education (CBE): a pedagogical approach in which
declared competencies drive assessment design rather than mere course completion.
A critical, underexamined question is *operationalisation* — how a declared
competency is translated into observable criteria, graded assessment activities,
and a defensible competency verdict.

This systematic review (Scopus + Web of Science, 2015–2026, PRISMA 2020) answers
that question by synthesising 25 eligible studies on a seven-dimension coding
frame: decomposition architecture, grading philosophy, aggregation transparency,
alignment explicitness, competency scope, temporal architecture, and level of
application. The review identifies three structural deficits (aggregation opacity,
transversal-competency rigour gap, programme-level absence) and a fourth
cross-cutting barrier (the reporting gap: 38 papers excluded because their
assessment designs could not be reconstructed from the text alone). It proposes
a minimum five-element reporting checklist as an actionable community norm.

---

## Repository structure

```
cbe-operationalisation-review/
│
├── record_identification/
│   ├── scopus.ris                  Raw Scopus export (307 records, RIS format)
│   ├── wos.ris                     Raw Web of Science export (150 records, RIS format)
│   └── scopus_and_wos_mixed.csv    Merged, deduplicated record set (361 unique records)
│
└── screening/
    ├── screening_phase1.md         Phase 1 decision log (title/abstract screening)
    ├── screening_phase2.md         Phase 2 decision log (full-text eligibility)
    └── non_retrieved_papers.md     The 9 papers that could not be accessed
```

---

## PRISMA 2020 study selection — summary

| Step | Records | Notes |
|------|--------:|-------|
| Scopus search | 307 | Query run May 2026 |
| Web of Science search | 150 | Same Boolean logic, WoS field syntax |
| Duplicates removed | 96 | |
| **Unique records for screening** | **361** | `scopus_and_wos_mixed.csv` |
| Phase 1 excluded (title/abstract) | 257 | Criteria E1–E9 |
| **Advanced to Phase 2** | **104** | `screening_phase1.md` |
| Full texts not retrieved | 9 | `non_retrieved_papers.md` |
| Phase 2 excluded (full text) | 70 | Criteria E1–E10; includes 3 late-stage duplicates |
| **Final eligible set** | **25** | `screening_phase2.md` |

---

## Search strategy

Both databases were queried with equivalent Boolean logic. The Scopus formulation
is reproduced below; the WoS version uses the same terms mapped to TS= field
syntax.

```
TITLE-ABS-KEY (
    "competenc*-based education" OR "competenc*-based learning"
    OR "competenc*-based teaching" OR "competenc*-based training"
    OR "competenc*-based instruction" OR "competenc*-based curriculum"
    OR "competenc*-based approach" OR "competenc*-based assessment"
  )
  AND TITLE-ABS-KEY (
    assess* OR evaluat* OR rubric* OR appraisal OR measurement OR "learning outcome*"
  )
  AND TITLE-ABS-KEY (
    course* OR curricul* OR program* OR module* OR subject OR syllab*
    OR classroom OR instructional
  )
  AND TITLE-ABS-KEY (
    engineer* OR STEM OR "computer science" OR "computing education"
    OR informatics OR robotics OR mechatronic*
  )
AND PUBYEAR > 2014 AND PUBYEAR < 2027
AND ( LIMIT-TO ( DOCTYPE , "ar" )
   OR LIMIT-TO ( DOCTYPE , "cp" )
   OR LIMIT-TO ( DOCTYPE , "re" ) )
AND ( LIMIT-TO ( LANGUAGE , "English" ) )
```

Filters: 2015–2026, document types article / conference paper / review,
English language.

---

## Eligibility criteria

Eligibility was assessed in two phases. In **Phase 1**, all five inclusion
criteria (I1–I5) and exclusion criteria E1–E9 were applied to titles, abstracts,
and keywords. In **Phase 2**, the same criteria were re-applied to full texts,
with one additional criterion (E10) assessing methodological transparency.

### Inclusion (all five must hold)

| Code | Criterion |
|------|-----------|
| I1 | CBE/CBL paradigm structurally operative: competencies drive assessment design, not merely named in accreditation documents |
| I2 | Engineering or STEM higher education (undergraduate or postgraduate); includes CS, informatics, software engineering |
| I3 | Assessment operationalisation is a primary or substantive secondary contribution: the design of the competency-assessment link, not only its outcome |
| I4 | At least one structural element of the competency-assessment chain: alignment mapping (a), rubric/indicator criteria (b), aggregation mechanism (c), or hierarchical decomposition (d) |
| I5 | Course- or programme-level application with sufficient detail for a practitioner to understand, replicate, or adapt the design |

### Exclusion (any single criterion is sufficient)

| Code | Phase | Criterion |
|------|-------|-----------|
| E1 | 1+2 | Non-target discipline (medicine, business, K-12) or pre-university population |
| E2 | 1+2 | Workforce or professional-certification "competency" only: no student-facing HE assessment component |
| E3 | 1+2 | No assessment design: competency maps, accreditation criteria, or perception surveys without rubric, indicator, or alignment mapping |
| E4 | 1+2 | Assessment incidental to a pedagogical intervention: pre/post scores used as outcome metrics without describing the grading structure |
| E5 | 1+2 | Standardised or external examination only, without course-level competency disaggregation by the authors |
| E6 | 1+2 | Technology tool without disclosing the underlying rubric, indicator, or alignment structure |
| E7 | 1+2 | Advocacy, conceptual position, or narrative review: no concrete course-level operationalisation |
| E8 | 1+2 | Excluded document type: abstract only, editorial, book chapter, or non-peer-reviewed report |
| E9 | 1+2 | Non-English full text |
| E10 | 2 only | Insufficient methodological detail: rubric criteria and/or aggregation path not traceable from the paper alone |

E10 operationalises the *reporting gap* finding of the review: a paper satisfies
E10 if a reader with standard engineering education knowledge cannot (1) identify
which competency or learning outcome each assessment activity targets, (2)
understand the criteria by which performance is judged, and (3) trace how
individual scores contribute to a competency-level verdict.

---

## Screening logs — file format

Both decision logs share a common per-entry structure:

```markdown
### {ID}
**Title:** {title} ({year})
**Decision:** INCLUDE | EXCLUDE | NOT RETRIEVED  |  **Criteria:** {codes}
**Rationale:** {free-text justification}
```

Each entry is keyed by the three-digit zero-padded record ID from
`scopus_and_wos_mixed.csv`. Rationales are written to support auditability:
a reviewer unfamiliar with the paper should be able to verify the decision from
the rationale alone.

---

## Screeners

| Phase | Screener | Date |
|-------|----------|------|
| Phase 1 (title/abstract) | Rubén Heradio, Héctor Vargas | May 2026 |
| Phase 2 (full text) | Rubén Heradio, Héctor Vargas | May 2026 |

---

## How to replicate

1. **Re-run the search** using the query above in Scopus and WoS (note: result
   counts will differ after May 2026 as new records are indexed).
2. **Deduplicate** the two `.ris` exports; the merged set is provided as
   `scopus_and_wos_mixed.csv` (361 records, columns: `id, title, authors, year,
   doi, abstract`).
3. **Apply Phase 1 criteria** (I1–I5, E1–E9) to titles, abstracts, and
   keywords; compare with `screening_phase1.md`.
4. **Retrieve full texts** for the 104 papers advancing from Phase 1; compare
   with `non_retrieved_papers.md` for the 9 that could not be accessed.
5. **Apply Phase 2 criteria** (I1–I5, E1–E10) to full texts; compare with
   `screening_phase2.md`.

---

## Citation

If you use these artifacts in your own research, please cite the review paper
(full reference above) and this repository.

---

## License

The screening logs and record data in this repository are released under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Raw database exports (`.ris` files) are subject to Scopus and Web of Science
terms of use; they are archived here solely for replication purposes.
