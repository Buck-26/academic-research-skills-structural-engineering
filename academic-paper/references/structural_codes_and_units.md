# Structural Codes, Standards and Units

> **Civil/structural fork addition.** The civil/structural reviewer cards in `field_analyst_agent` name it, and `academic-paper/SKILL.md` lists it among the references for writing. It's advisory: it tells the writer and the reviewers what to check. It never asserts that a clause says something. Clause text must come from the code document the author supplies or cites.

## 1. Code registry (cite by edition and clause)

Always cite a code with its **designation, edition (year) and clause**. Chapter and clause numbers in this table are left out on purpose; take them from the code document itself, e.g. "EN 1998-1:2004, §4.3.3.2" or "TBDY 2018, §4.7.1". Never write "the Eurocode" or "the Turkish code" alone. When an edition changes the rule you are using, name the edition you used and say so.

| Material / topic | Europe (CEN) | Turkey | USA | Notes |
|---|---|---|---|---|
| Basis of design, actions | EN 1990, EN 1991 | TS 498, TS EN 1990 | ASCE/SEI 7 | Load combinations differ in form; don't mix partial factors across systems |
| Reinforced concrete | EN 1992-1-1 | TS 500 (2000), TBDY 2018 (cast-in-place RC buildings chapter) | ACI 318 | Concrete class notation: C30/37 (EN), C30 (TS 500), f′c in MPa (ACI) |
| Steel | EN 1993-1-1, -1-8 (joints), -1-5 | ÇYTHYE 2018 (Çelik Yapıların Tasarım, Hesap ve Yapım Esasları), TBDY 2018 (steel buildings chapter) | AISC 360, AISC 341 (seismic), AISC 358 | ÇYTHYE follows AISC (LRFD/ASD); grades S235/S275/S355 (EN 10025) |
| Composite | EN 1994 | TBDY 2018 (steel buildings chapter), ÇYTHYE | AISC 360 Ch. I | |
| Timber | EN 1995-1-1 | TS EN 1995-1-1; TBDY 2018 (timber buildings chapter) | NDS (AWC), SDPWS | Strength classes C24, GL28h (EN 338, EN 14080); CLT per EN 16351 |
| Masonry | EN 1996 | TBDY 2018 (masonry buildings chapter) | TMS 402 | |
| Seismic design | EN 1998-1 (buildings), -2 (bridges), -3 (assessment), -5 (foundations) | TBDY 2018 (Türkiye Bina Deprem Yönetmeliği) | ASCE/SEI 7 Ch. 11–23, ASCE/SEI 41 (existing) | Behaviour factor q (EN) vs R, Ω₀, C_d (ASCE 7) vs R, D (TBDY) aren't interchangeable |
| Hazard | National annexes, ESHM20 | AFAD Türkiye Deprem Tehlike Haritası (TDTH, 2018) | USGS NSHM via ASCE 7 Hazard Tool | Return period / exceedance probability must be stated (e.g. DD-2: 10% in 50 years) |
| Bridges | EN 1998-2 | Turkish highway bridge seismic design regulation (KGM; confirm title and edition) | AASHTO LRFD, AASHTO Guide Spec. Seismic | |
| Performance-based design, assessment | EN 1998-3 | TBDY 2018 (existing-building assessment chapter; deformation-based design, ŞGDT) | ASCE/SEI 41, FEMA P-58, FEMA P-695, PEER TBI | |
| Test protocols | EN 12512 (timber joints), EN 15129 (anti-seismic devices) | — | FEMA 461, ATC-24, AISC 341 Ch. K, ACI 374.1/374.2R | Name the loading protocol when reporting cyclic tests |

The panel checks that (a) every code reference carries an edition, (b) the code system used for design matches the one used for checking, and (c) any comparison between systems names the conversion, like partial factors, characteristic or nominal strengths, or behaviour factors.

## 2. Code citation in reference lists

Codes are cited as corporate-author documents. Examples in ASCE author-date style (see `citation_format_switcher.md` § ASCE):

```
CEN (European Committee for Standardization). 2004. Eurocode 8: Design of structures
    for earthquake resistance—Part 1: General rules, seismic actions and rules for
    buildings. EN 1998-1. Brussels: CEN.
AFAD (Disaster and Emergency Management Presidency). 2018. Türkiye bina deprem
    yönetmeliği [Turkish building earthquake code]. Ankara: AFAD.
ASCE. 2022. Minimum design loads and associated criteria for buildings and other
    structures. ASCE/SEI 7-22. Reston, VA: ASCE.
AISC. 2022. Specification for structural steel buildings. ANSI/AISC 360-22. Chicago: AISC.
```

For a Turkish code, give the original Turkish title, then an English translation in square brackets.

## 3. Units (SI by default)

- **Use SI throughout.** Use kN, kN·m, MPa (N/mm²), mm and m, and give mass in kg or t and accelerations in m/s² or in g (say which).
- If the source is US customary, convert it and keep the original in parentheses the first time you use it, e.g. "345 MPa (50 ksi)". Use exact conversion factors: 1 ksi = 6.895 MPa, 1 kip = 4.448 kN, 1 in. = 25.4 mm, 1 kip·ft = 1.356 kN·m.
- Spectral accelerations go in g, with the damping ratio stated (e.g. S_a(T₁, 5%)).
- Drift is a ratio or a %, never mixed in one table. Ductility (μ) is dimensionless, and the yield definition must be stated.
- Write a space between the number and the unit (250 mm), and use the same decimal separator throughout. For an English manuscript that's a point, even when the author is Turkish.
- Notation follows the code system used: f_ck, f_yk, γ_M0 (EN); f′c, f_y, φ (ACI/AISC). Don't mix symbols for the same quantity.

**Unit check (the reviewers and `draft_writer_agent` run this):** check every number that has a unit against its table or figure, check every converted value against its original, and flag a quantity that has no unit.

## 4. Engineering evidence quality signals

The `structural_engineering` evidence profile (`domain_evidence_profiles.md`) admits these sources. The reviewers check them like this:

| Evidence type | What to check |
|---|---|
| Experimental test | Specimen count and repeats, scale and similitude, boundary conditions, material coupon tests reported, loading protocol named, instrumentation, failure mode documented |
| Numerical / FE model | Software and version, element and material models, mesh or convergence study, **validated against independent tests (not only calibrated)**, damping model stated |
| Nonlinear time-history | Ground-motion selection and scaling method, number of records, target spectrum and code clause, record set given (e.g. PEER NGA-West2 RSNs, AFAD TADAS station codes) |
| Fragility / probabilistic | Intensity measure, damage-state definitions, uncertainty treatment (record-to-record, modelling), fitting method |
| Field / reconnaissance | Survey date, sampling of buildings (all or a convenience sample), damage scale used (e.g. EMS-98) |
| Code-based design example | Code edition, national annex or local parameters, hand check or software |
