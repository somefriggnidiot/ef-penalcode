# Penal Code Hierarchy Analysis

## Scope

This review maps every charge degree in `ef-mdt-penal-code.json` into `penal-code-charge-degree-map.csv` and evaluates the current hierarchy using:

- classification
- base fine
- base time
- severity score
- cross-cutting tags

The analysis focuses on base sentencing. Modifiers, liability options, prior history, judicial discretion, and charge stacking can change the final case outcome.

## CSV Mapping

The generated CSV contains one row per charge degree. Total mapped rows: 165.

Default review columns:

| Column | Purpose |
| --- | --- |
| `degreeLabel` | Degree being evaluated |
| `classification` | Infraction, misdemeanor, or felony |
| `baseFine` | Base fine before modifiers |
| `baseTime` | Base time before modifiers |
| `severityScore` | Composite punishment score |
| `tags` | Semicolon-delimited attributes for filtering common charge features |

The CSV also keeps category, charge, source code, modifiers, liability options, and legal-principle fields for deeper review.

## Severity Score

The current severity score is:

```text
severityScore = baseTime * 10 + sqrt(baseFine)
```

This keeps custody time as the main severity signal while still letting fines matter. It also prevents high regulatory or commercial fines from automatically outranking violent crimes solely because they are expensive.

Formula options considered:

| Formula | Strength | Concern |
| --- | --- | --- |
| `baseTime * 10 + baseFine / 100` | Easy to explain. | High fines can overpower violent-crime severity. |
| `baseTime * 10 + sqrt(baseFine)` | Current choice; balances time and fine cleanly. | Fine differences are compressed. |
| `baseTime * 10 + log10(baseFine + 1) * 25` | Very stable against extreme fines. | Harder to explain to staff. |

## Classification Trends

| Classification | Count | Avg Severity | Min Severity | Max Severity | Avg Time | Avg Fine |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Felony | 69 | 306.1 | 64.1 | 2541.4 | 26.1 | 2918 |
| Misdemeanor | 61 | 119.1 | 17.3 | 285.4 | 9.3 | 889 |
| Infraction | 35 | 16.0 | 10.0 | 31.6 | 0.0 | 293 |

The broad classification ladder works: felonies average far above misdemeanors, and misdemeanors average far above infractions.

The boundary is still porous. The lowest felony is 64.1, while the highest misdemeanor is 285.4. There are 47 felonies at or below the highest misdemeanor score, and 50 misdemeanors at or above the lowest felony score. Some overlap is expected because felony status can express legal seriousness beyond raw punishment, but the overlap is broad enough to create hierarchy noise.

## Charge Family Trends

| Charge Family | Count | Avg Severity | Max Severity | Felonies | Misd. | Infractions |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Offenses Against Public Safety | 22 | 304.9 | 2541.4 | 14 | 7 | 0 |
| Offenses Involving Fraud | 8 | 286.7 | 509.2 | 4 | 4 | 0 |
| Offenses Involving Theft | 21 | 215.8 | 700.0 | 11 | 8 | 2 |
| Offenses Against Persons | 16 | 207.8 | 550.0 | 10 | 6 | 0 |
| Offenses Against Public Order | 19 | 164.1 | 444.7 | 7 | 8 | 4 |
| Offenses Against Public Administration | 14 | 153.7 | 350.0 | 5 | 7 | 2 |
| Offenses Against Health and Morals | 22 | 151.3 | 670.7 | 12 | 8 | 2 |
| Offenses Involving the Well-Being of Wildlife | 11 | 138.7 | 513.2 | 2 | 5 | 4 |
| Offenses Involving Damage to Property | 6 | 100.2 | 200.0 | 2 | 2 | 2 |
| Offenses Involving the Operation of a Vehicle | 26 | 52.5 | 238.7 | 2 | 6 | 18 |

Public Safety is the highest average family because it contains Insurrection, weapon sales, weapon trafficking, explosives, and firearm possession. That is understandable for GTA-style gameplay, but Insurrection is so high that it dominates the family.

Fraud is the second-highest average family despite having no violent conduct. That comes from high-scoring impersonation, money laundering, and extortion. This is defensible if fraud in this code means official-identity abuse and organized economic crime, but ordinary fraud should not drift too close to homicide and top-tier violence.

Theft and Persons are close. Theft has higher peaks due to law-enforcement vehicle theft and aircraft theft. Persons has the most morally serious conduct, but its max is First Degree Murder at 550.0, below several theft, public-safety, and health/morals offenses.

Vehicle Operation is correctly infraction-heavy. It has a low average because most traffic charges are fine-only, with Reckless Evading as the main serious outlier.

## Tag Trends

High-signal tags by average severity:

| Tag | Count | Avg Severity | Max Severity | Felonies | Misd. | Infractions |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| `organized-activity` | 1 | 2541.4 | 2541.4 | 1 | 0 | 0 |
| `public-safety` | 22 | 304.9 | 2541.4 | 14 | 7 | 0 |
| `fraud` | 8 | 286.7 | 509.2 | 4 | 4 | 0 |
| `explosive-related` | 8 | 276.4 | 709.5 | 7 | 1 | 0 |
| `public-order` | 24 | 251.5 | 2541.4 | 8 | 11 | 5 |
| `government` | 46 | 237.0 | 2541.4 | 21 | 20 | 5 |
| `homicide` | 13 | 223.6 | 550.0 | 7 | 3 | 3 |
| `theft` | 21 | 215.8 | 700.0 | 11 | 8 | 2 |
| `sale-transfer` | 31 | 211.7 | 709.5 | 17 | 8 | 6 |
| `economic` | 44 | 210.5 | 709.5 | 23 | 14 | 7 |
| `person` | 16 | 207.8 | 550.0 | 10 | 6 | 0 |
| `violent` | 36 | 199.8 | 550.0 | 21 | 10 | 5 |
| `commercial` | 39 | 198.6 | 709.5 | 20 | 12 | 7 |
| `weapon-related` | 31 | 176.4 | 709.5 | 15 | 13 | 3 |
| `controlled-substance` | 20 | 160.7 | 670.7 | 12 | 7 | 1 |
| `possession` | 36 | 154.8 | 470.7 | 18 | 17 | 1 |
| `regulatory` | 12 | 128.0 | 513.2 | 2 | 5 | 5 |
| `vehicle-related` | 48 | 120.6 | 700.0 | 14 | 12 | 22 |
| `traffic` | 26 | 52.5 | 238.7 | 2 | 6 | 18 |

The tags show a useful pattern: the highest severities are not purely violent. Public-safety, government, economic, sale-transfer, fraud, and commercial tags are frequently severe because they include organized, official, contraband, trafficking, and weapon-sale conduct.

That is fine for a simulation DOJ, but it should be intentional. If severity is meant to mirror California-style relative punishment, homicide and serious violence should generally sit above ordinary commercial, licensing, and property conduct unless the latter has exceptional public-danger facts.

## Highest Severity Degrees

| Degree | Classification | Fine | Time | Severity | Tags |
| --- | --- | ---: | ---: | ---: | --- |
| Insurrection | felony | 20000 | 240 | 2541.4 | `government;organized-activity;public-order;public-safety` |
| Criminal Sale of Weapon Class D | felony | 12000 | 60 | 709.5 | `commercial;economic;explosive-related;public-safety;sale-transfer;weapon-related` |
| Theft of a Law Enforcement Vehicle | felony | 10000 | 60 | 700.0 | `government;property;theft;vehicle-related` |
| Drug Trafficking | felony | 5000 | 60 | 670.7 | `commercial;controlled-substance;economic;health-morals;sale-transfer` |
| Operating an Unlicensed Import/Export Business | felony | 20000 | 50 | 641.4 | `commercial;economic;licensing-status;property;sale-transfer;theft` |
| Weapon Trafficking | felony | 11000 | 45 | 554.9 | `commercial;economic;firearm-related;public-safety;sale-transfer;weapon-related` |
| First Degree Murder | felony | 2500 | 50 | 550.0 | `homicide;person;victim-specific;violent` |
| Murder of a Police Working Dog | felony | 4000 | 45 | 513.2 | `homicide;regulatory;violent;wildlife;wildlife-animal` |
| Impersonating a Judge | felony | 3500 | 45 | 509.2 | `economic;fraud;government;identity-document` |
| Theft of an Aircraft | felony | 5000 | 40 | 470.7 | `property;theft;vehicle-related` |

The top ten show the main hierarchy tension: First Degree Murder is below weapon sale, drug trafficking, law-enforcement vehicle theft, import/export business, and weapon trafficking. California's relative punishment ladder would usually put intentional murder at or near the top of ordinary non-exceptional crimes.

## Classification Overlap

Highest-scoring misdemeanors:

| Degree | Classification | Fine | Time | Severity | Tags |
| --- | --- | ---: | ---: | ---: | --- |
| Impersonating | misdemeanor | 1250 | 25 | 285.4 | `commercial;economic;fraud;government;identity-document` |
| Embezzlement | misdemeanor | 1000 | 20 | 231.6 | `commercial;economic;government;justice-system;sale-transfer` |
| Possession of Government-Issued Items | misdemeanor | 1000 | 20 | 231.6 | `firearm-related;government;identity-document;licensing-status;possession;property;theft;vehicle-related;weapon-related` |
| Illegal Fishing | misdemeanor | 6250 | 15 | 229.1 | `commercial;economic;possession;regulatory;sale-transfer;wildlife` |
| Violation of a Restraining Order | misdemeanor | 525 | 20 | 222.9 | `government;justice-system;public-order` |
| Harboring a Fugitive | misdemeanor | 375 | 20 | 219.4 | `government;justice-system;public-order` |
| Possession of Stolen Government Identification | misdemeanor | 200 | 20 | 214.1 | `economic;fraud;government;identity-document;licensing-status;possession` |
| Criminal Use of Weapon | misdemeanor | 4000 | 15 | 213.2 | `explosive-related;firearm-related;public-safety;weapon-related` |

Lowest-scoring felonies:

| Degree | Classification | Fine | Time | Severity | Tags |
| --- | --- | ---: | ---: | ---: | --- |
| Possession of Contraband in a Government Facility | felony | 200 | 5 | 64.1 | `controlled-substance;government;justice-system;possession;weapon-related` |
| Criminal Possession of Weapon Class A | felony | 250 | 5 | 65.8 | `firearm-related;licensing-status;possession;public-safety;weapon-related` |
| Criminal Possession of Ammunition | felony | 500 | 5 | 72.4 | `firearm-related;government;justice-system;licensing-status;possession;public-safety;weapon-related` |
| Unlawful Production of Moonshine | felony | 750 | 7 | 97.4 | `alcohol-intoxication;health-morals;licensing-status;manufacturing-production` |
| Possession of Drug Manufacturing Materials | felony | 750 | 7 | 97.4 | `controlled-substance;health-morals;manufacturing-production;possession` |
| Grand Theft Auto A | felony | 120 | 10 | 111.0 | `government;possession;property;theft;vehicle-related` |
| Smuggling of Contraband | felony | 4000 | 5 | 113.2 | `commercial;economic;property;sale-transfer;theft` |
| Flying into Restricted Airspace | felony | 750 | 10 | 127.4 | `licensing-status;public-safety;vehicle-related` |
| Escaping | felony | 1005 | 10 | 131.7 | `government;justice-system;licensing-status` |
| Criminal Possession of Weapon Class B | felony | 2000 | 10 | 144.7 | `firearm-related;licensing-status;possession;public-safety;weapon-related` |

This overlap is the strongest evidence that classification and punishment are carrying different meanings. Low-scoring felonies are mostly status, possession, licensing, or contraband offenses. High-scoring misdemeanors are mostly government, identity, public-order, weapon-use, or regulatory/economic offenses.

Recommended policy: keep low-score felonies only where felony status itself matters, such as firearms, government-facility contraband, escape, or public-safety access. Otherwise, consider misdemeanor treatment or raise the penalty enough that felony classification reads coherently.

## Tag-Based Findings

### Violent and Homicide Tags

Violent offenses average 199.8, while homicide-tagged offenses average 223.6. That is lower than public-safety, fraud, explosive-related, public-order, government, theft, sale-transfer, and economic tags.

This is mostly because the violent tag includes low-level assault, brandishing, harassment, and infraction/misdemeanor wildlife or public-order conduct. Still, the highest homicide/person offenses do not dominate the hierarchy. First Degree Murder at 550.0 is below several non-homicide offenses.

Recommendation: either raise First Degree Murder and Second Degree Murder, or reduce the 60-time non-homicide offenses so homicide regains its expected place near the top of ordinary crimes.

### Commercial, Economic, and Sale-Transfer Tags

Commercial/economic offenses are high because they include weapon sales, trafficking, import/export, smuggling, money laundering, and some regulatory wildlife conduct.

That trend is defensible if the DOJ wants organized market crimes to matter. The risk is that ordinary business/licensing or commercial conduct can begin to look more serious than violence. Operating an Unlicensed Import/Export Business at 641.4 is above First Degree Murder at 550.0, which should be reviewed unless that offense is intended to represent major organized contraband operations.

Recommendation: split ordinary licensing/business violations from organized contraband import/export if the facts are meant to cover both.

### Weapon and Public Safety Tags

Public-safety offenses average 304.9. Weapon-related offenses average 176.4, but the tag has a wide spread because it includes possession, brandishing, criminal use, sale, explosives, trafficking, and insurrection.

The internal ordering mostly works: sale/trafficking and Class D conduct are much higher than simple Class A/B possession. The weak point is that some low-end possession felonies score below many misdemeanors. That may still be correct if felony status is policy-driven.

Recommendation: preserve low-time felony status for firearm possession if desired, but make weapon manufacturing and sale consistently higher than simple possession.

### Government and Justice-System Tags

Government-tagged offenses are common and serious: 46 rows with an average severity of 237.0. Justice-system tags average 146.8.

This shows the code treats official authority, court process, custody, identity, and facility control as major institutional interests. That is coherent for an MDT, especially where roleplay often turns on official process.

Recommendation: distinguish field-level interference from formal-process corruption. Misdemeanor obstruction, disobeying an officer, and resisting should remain lower than witness tampering, evidence tampering, jailbreak, and judicial impersonation.

### Vehicle and Traffic Tags

Traffic-tagged offenses average 52.5 and vehicle-related offenses average 120.6. This split is useful: ordinary traffic stays low, while vehicle-related serious crimes include theft, aircraft theft, law-enforcement vehicle theft, reckless evading, and DUI.

Recommendation: keep ordinary traffic infractions low. Review vehicle theft penalties separately from traffic penalties, because the vehicle-related tag spans both minor driving conduct and serious property/public-safety conduct.

### Regulatory and Wildlife Tags

Regulatory and wildlife tags average 128.0, but the max is 513.2 because Murder of a Police Working Dog is included. Ordinary wildlife offenses are generally fine-heavy and lower-custody.

Recommendation: reserve the highest wildlife/regulatory fines for commercial, protected-species, repeat, or organized conduct. Ordinary illegal fishing should not visually outrank too many violent misdemeanors unless deterrence is the explicit goal.

## Recommended Cutoff Bands

Using severity score instead of base time alone gives a cleaner review scale:

| Severity Band | Suggested Meaning |
| --- | --- |
| 0-35 | Infraction or citation-only conduct |
| 35-100 | Low misdemeanor or low-time felony status offense |
| 100-200 | Ordinary misdemeanor, serious citation alternative, or low felony |
| 200-350 | Serious misdemeanor, wobbler, or ordinary felony |
| 350-550 | Serious felony |
| 550-750 | Top-tier felony below exceptional/state-crisis conduct |
| 750+ | Exceptional conduct or charges that should be rare and tightly defined |

Current pressure points:

- Misdemeanors above 200 should be reviewed for felony treatment or reduced punishment.
- Felonies below 150 should be reviewed to confirm felony status is intentional.
- Ordinary non-homicide crimes above 550 should be reviewed against First Degree Murder.
- Any base score above 750 should either be exceptional or rebalanced.

## California-Style Calibration

The goal is not to copy California sentencing literally. GTA roleplay needs compressed and playable punishments. The useful California comparison is the relative ladder:

- murder is life-tier and should sit near the top
- manslaughter is below murder but still serious
- robbery/carjacking are serious felonies below murder
- simple assault/battery are misdemeanor-level unless aggravated
- possession is below sale/transport/trafficking
- weapon sale/manufacturing/trafficking is above simple possession
- DUI without injury is below injury DUI, vehicular manslaughter, and homicide

Sources checked:

- California Penal Code: [190](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=190), [193](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=193), [213](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=213), [215](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=215), [243](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=243), [245](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=245), [461](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=461), [489](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=489)
- California Health and Safety Code: [11350](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11350), [11351](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11351), [11352](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11352)
- California Vehicle Code: [23152](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=VEH&sectionNum=23152), [23153](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=VEH&sectionNum=23153)

## Bottom Line

Severity scoring confirms the same broad picture as base time, but the tags reveal why the hierarchy feels uneven: commercial, government, public-safety, and sale-transfer conduct often outranks person and violent conduct.

That can be a valid simulation choice, especially for organized weapons, explosives, trafficking, official corruption, and government-security offenses. The main recommendation is to make that choice explicit and then rebalance outliers:

1. Put intentional homicide nearer the top of ordinary offenses.
2. Keep exceptional state-crisis conduct, like Insurrection, separate from the ordinary ladder.
3. Review high-score misdemeanors over 200.
4. Review low-score felonies under 150.
5. Split ordinary commercial/licensing conduct from organized contraband or trafficking conduct where the same charge family is carrying both ideas.
