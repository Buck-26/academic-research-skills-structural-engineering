# Civil / Structural Engineering Fork

This repository is a fork of [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) by Cheng-I Wu, licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). It is used for non-commercial research only. All credit for the original suite belongs to the original author. The changes listed below adapt it for structural engineering (steel, reinforced concrete and timber), structural dynamics and earthquake engineering. They are made under the same license.

## What this fork changes

| Area | Change | Files |
|---|---|---|
| Reviewer panel | Persona library for civil/structural papers: methodology seats by method (testing, FE, nonlinear dynamic, fragility, SHM), domain seats by material (steel, RC, timber, dynamics, seismic codes), and a practising-engineer seat; adds engineering method types and a worked example | `academic-paper-reviewer/agents/field_analyst_agent.md`, `domain_reviewer_agent.md`, `methodology_reviewer_agent.md` |
| Evidence profile | New ship-ready `structural_engineering` profile that admits proceedings, design codes, agency technical reports, test and ground-motion datasets and reconnaissance reports (admit-only, so the universal relevance, methodology and predatory gates still apply) | `academic-paper/references/domain_evidence_profiles.md`, `academic-paper/agents/intake_agent.md`, `academic-paper/agents/literature_strategist_agent.md`, `scripts/check_domain_evidence_profile.py` |
| Databases | Civil/Structural/Earthquake row: Scopus, Web of Science, ASCE Library, ScienceDirect, Wiley, ICE; grey literature (PEER, FEMA, NIST, JRC, EERI/GEER); Turkish sources (TR Dizin, YÖK Tez, DergiPark, AFAD) | `academic-paper/agents/literature_strategist_agent.md` |
| Journals | Structural, earthquake and dynamics journals, including *J. Struct. Eng.*, *Engineering Structures*, *Thin-Walled Structures*, *Structures* and *Bulletin of Earthquake Engineering* | `academic-paper-reviewer/references/top_journals_by_field.md` |
| Citation style | ASCE author-date added as a supported style (report-only in citation-check, like the other non-APA styles) | `citation_format_switcher.md`, `citation_compliance_agent.md`, `formatter_agent.md`, `intake_agent.md`, `academic-paper/SKILL.md`, `shared/handoff_schemas.md` |
| Codes and units | Registry of Eurocodes, TBDY 2018, ÇYTHYE, TS 500, ACI, AISC, ASCE 7/41 and NDS, cited by edition and clause; how to cite codes; SI unit rules and conversions; quality checks for each kind of engineering evidence | `academic-paper/references/structural_codes_and_units.md` (new) |
| Glossary | English/Turkish structural terms aligned with TBDY 2018 wording | `academic-paper/references/structural_engineering_glossary.md` (new) |

## Installing this fork instead of the original

Uninstall the original plugin first, because both use the same plugin name:

```text
/plugin uninstall academic-research-skills
/plugin marketplace add Buck-26/academic-research-skills-structural-engineering
/plugin install academic-research-skills
```

## Keeping up with the original

The changes touch only a few files, so upstream releases can usually be merged with:

```bash
git remote add upstream https://github.com/Imbad0202/academic-research-skills
git fetch upstream main
git merge upstream/main
```

The startup update notice still compares against the original repository's version.
