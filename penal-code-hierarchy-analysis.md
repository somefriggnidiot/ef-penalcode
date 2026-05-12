# Penal Code Hierarchy Analysis

## Scope

This review maps every charge degree in `ef-mdt-penal-code.json` into `penal-code-charge-degree-map.csv` and evaluates the current sentencing hierarchy using each degree's base classification, base fine, and base time.

The analysis below focuses on base sentencing only. Modifiers, liability options, enhancements, and judicial discretion can change a final sentence, but the base values should still communicate a coherent severity ladder.

## CSV Mapping

The generated CSV contains one row per charge degree.

Columns included:

| Column | Purpose |
| --- | --- |
| `categoryId` / `categoryTitle` | Penal code category placement |
| `chargeId` / `chargeCode` / `chargeTitle` | Charge identity |
| `chargeDescription` | Charge-level wording |
| `degreeId` / `degreeLabel` | Degree identity |
| `sourceCode` / `sourceTitle` | Degree-specific code and title |
| `classification` | Infraction, misdemeanor, or felony |
| `tags` | Semicolon-delimited attributes for filtering common charge features |
| `severityScore` | Composite score based on base time and base fine |
| `baseFine` / `baseTime` | Base punishment values |
| `modifierIds` | Modifiers available to the degree |
| `liabilityOptions` | Attempt, accessory, conspiracy, or related liability options |
| `legalOverview` / `legalPrinciples` | Degree-level legal principle text |
| `hasLegalPrinciples` | Whether the degree includes the legal principles object |

Total mapped rows: 165 charge degrees.

## Tags and Severity Scoring

The CSV now includes a `tags` column to make cross-category filtering easier. Tags are semicolon-delimited and are intended to answer questions like whether a degree is `violent`, `commercial`, `weapon-related`, `controlled-substance`, `vehicle-related`, `government`, `property`, `regulatory`, or `justice-system` related.

The CSV also includes `severityScore`, currently calculated as:

```text
severityScore = baseTime * 10 + sqrt(baseFine)
```

This formula intentionally makes custody time the main severity driver while still allowing fines to matter. The square-root fine component prevents high regulatory or commercial fines from overpowering violent offenses solely because they are expensive.

Formula options considered:

| Formula | Example Use | Concern |
| --- | --- | --- |
| `baseTime * 10 + baseFine / 100` | Easy to read; every 100 fine equals 1 severity point. | High fines can make regulatory/economic crimes outrank serious violence too easily. |
| `baseTime * 10 + sqrt(baseFine)` | Current choice; time dominates while fine still contributes. | Fine differences are compressed, so economic harm is less visible than custody time. |
| `baseTime * 10 + log10(baseFine + 1) * 25` | Very stable against extreme fines. | Fine contribution may feel too abstract and harder to explain to staff. |

Example scores using the current formula:

| Degree | Time | Fine | Severity Score |
| --- | ---: | ---: | ---: |
| Insurrection | 240 | 20000 | 2541.4 |
| Criminal Sale of Weapon Class D | 60 | 12000 | 709.5 |
| Theft of a Law Enforcement Vehicle | 60 | 10000 | 700.0 |
| Drug Trafficking | 60 | 5000 | 670.7 |
| First Degree Murder | 50 | 2500 | 550.0 |
| Second Degree Murder | 40 | 1750 | 441.8 |
| Robbery | 25 | 1000 | 281.6 |
| Illegal Fishing | 15 | 6250 | 229.1 |
| Battery | 15 | 275 | 166.6 |
| Simple Assault | 1 | 150 | 22.2 |

## Overall Sentencing Shape

| Classification | Count | Base Time Range | Average Base Time | Base Fine Range | Average Base Fine |
| --- | ---: | ---: | ---: | ---: | ---: |
| Infraction | 35 | 0 | 0.0 | 100-1000 | 293 |
| Misdemeanor | 61 | 0-25 | 9.3 | 100-6250 | 889 |
| Felony | 69 | 5-240 | 26.1 | 120-20000 | 2918 |

The broad hierarchy is mostly legible: infractions are fine-only, misdemeanors usually carry shorter custody exposure, and felonies carry the highest average punishment.

The main issue is not the average. It is the overlap. The current misdemeanor/felony boundary is not clean because some felonies carry only 5-10 time while many misdemeanors carry 10-25 time.

## Highest Base Time Offenses

| Charge Degree | Classification | Fine | Time |
| --- | --- | ---: | ---: |
| Insurrection | Felony | 20000 | 240 |
| Theft of Law Enforcement Vehicle | Felony | 10000 | 60 |
| Criminal Sale of Weapon, Class D | Felony | 12000 | 60 |
| Drug Trafficking | Felony | 5000 | 60 |
| First Degree Murder | Felony | 2500 | 50 |
| Operating an Unlicensed Import/Export Business | Felony | 20000 | 50 |
| Impersonating a Judge | Felony | 3500 | 45 |
| Weapon Trafficking | Felony | 11000 | 45 |
| Murder of a Police Working Dog | Felony | 4000 | 45 |
| Theft of Aircraft | Felony | 5000 | 40 |
| Second Degree Murder | Felony | 1750 | 40 |
| Government Corruption | Felony | 2000 | 40 |
| Robbery | Felony | 1000 | 25 |

## California Benchmark

The goal is not to copy California sentencing literally. GTA roleplay needs shorter, more playable punishments. The useful California comparison is the relative ladder: which offenses sit above or below each other.

Primary California reference points:

| California area | Relative signal for this penal code |
| --- | --- |
| Murder | California places murder at the top of the ordinary criminal hierarchy: first degree murder is life-tier punishment and second degree murder is 15 years to life. |
| Manslaughter | Voluntary manslaughter is far below murder but still above many property and simple weapon offenses. |
| Robbery and carjacking | Robbery and carjacking are serious felonies, but they sit below murder and generally below the most serious homicide punishments. |
| Burglary and grand theft | Residential burglary is more serious than ordinary theft; grand theft can be felony or county-jail territory depending on facts. |
| Assault and battery | Simple assault/battery are misdemeanor-level; weapon assault or injury to protected victims can become felony-level. |
| Controlled substances | Simple possession is generally lower than possession for sale, sale, transport, or trafficking. |
| Firearms | Illegal possession can be misdemeanor or felony depending on weapon type and aggravating facts; manufacturing, trafficking, assault weapons, altered identifiers, or prohibited-person conduct are treated more seriously. |
| DUI | Simple DUI is below injury DUI, repeat DUI, vehicular manslaughter, and homicide. |

Sources checked:

- California Penal Code: [190](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=190), [193](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=193), [213](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=213), [215](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=215), [243](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=243), [245](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=245), [461](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=461), [489](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=489), [23900](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=23900), [25400](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=25400), [30605](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=30605)
- California Health and Safety Code: [11350](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11350), [11351](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11351), [11352](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=HSC&sectionNum=11352)
- California Vehicle Code: [23152](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=VEH&sectionNum=23152), [23153](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=VEH&sectionNum=23153), [23550](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=VEH&sectionNum=23550)

## Hierarchy Findings

### Top-Tier Crimes

The current top of the simulated code is mixed between public safety, weapons, drug trafficking, homicide, and high-value theft/economy crimes.

That can work for gameplay, but California's hierarchy would generally put intentional homicide above ordinary weapons trafficking, drug sales, and vehicle theft unless those offenses involve mass-casualty, terrorism, organized criminal enterprise, or other special aggravation.

Current concern points:

| Charge Degree | Fine | Time | California-style concern |
| --- | ---: | ---: | --- |
| Insurrection | 20000 | 240 | Sensible as exceptional top-tier conduct, but exceeds the JSON's global max time of 120. |
| Criminal Sale of Weapon, Class D | 12000 | 60 | Plausibly severe, but currently exceeds First Degree Murder. |
| Drug Trafficking | 5000 | 60 | Plausibly severe, but currently exceeds First Degree Murder. |
| Theft of Law Enforcement Vehicle | 10000 | 60 | Serious, but should usually sit below intentional murder. |
| First Degree Murder | 2500 | 50 | Should be near the top of the ordinary sentencing ladder. |
| Operating an Unlicensed Import/Export Business | 20000 | 50 | Economic/contraband harm is high, but matching First Degree Murder by time may overstate it unless facts are organized or dangerous. |

Recommended top-tier ladder:

| Tier | Recommended Simulated Position |
| --- | --- |
| Exceptional state/security crisis | Insurrection, terrorism-style conduct, mass-casualty explosives. These may exceed ordinary homicide if the code intentionally treats them as exceptional. |
| Intentional homicide | First Degree Murder should be the highest ordinary non-exceptional offense. |
| Serious homicide / extreme violence | Second Degree Murder, police working dog murder if treated as a special public safety offense, major explosive use, serious aggravated kidnapping if present. |
| Organized danger | Weapon trafficking, Class D weapon sale, major drug trafficking, large-scale smuggling. |
| Serious violent/property felonies | Robbery, carjacking, burglary, high-value theft, aircraft theft, major fraud/extortion. |

### Homicide and Serious Violence

The code is directionally right because murder is above robbery and most person crimes. The gap is not strong enough when compared to the highest non-homicide felonies.

California benchmark: first degree murder is life-tier; second degree murder is also life-term; voluntary manslaughter is a years-based felony; simple assault/battery are misdemeanor-level unless aggravated by weapon, injury, or protected victim.

Recommended adjustment:

| Degree | Current Time | Recommended Time Band |
| --- | ---: | ---: |
| First Degree Murder | 50 | 70-90 |
| Second Degree Murder | 40 | 55-70 |
| Voluntary Manslaughter | 20 | 30-40 |
| Vehicular Manslaughter | 25 | 25-35, with higher values for gross negligence or DUI-related facts |
| Battery | 15 | 5-10 unless serious injury/protected victim facts apply |
| Assault | 10 | 5-10 for simple assault; 15-25 for aggravated/deadly weapon assault |

### Robbery, Burglary, Theft, and Vehicle Theft

California treats robbery as a serious felony below murder. Carjacking is generally higher than ordinary robbery. Residential burglary is above ordinary theft, and grand theft is less severe than robbery because robbery includes force or fear.

The simulated code mostly follows this pattern, but some vehicle and special-theft offenses are unusually high:

| Charge Degree | Fine | Time | Finding |
| --- | ---: | ---: | --- |
| Robbery | 1000 | 25 | Reasonable as a serious felony baseline. |
| Armed robbery, estimated via `weapon-used` | 1350 | 33.75 | Reasonable if it remains below homicide and near other aggravated violence. |
| Theft of Aircraft | 5000 | 40 | High but plausible for rare/high-risk conduct. |
| Theft of Law Enforcement Vehicle | 10000 | 60 | Likely too high if it exceeds intentional murder. |
| Grand Theft Auto, Class A | 120 | 10 | Low for felony vehicle theft if the vehicle class has meaningful value/risk. |
| Grand Larceny | 1000 | 30 | Reasonable if reserved for high-value theft. |

Recommended adjustment: keep robbery around 25, let armed robbery land around 30-35 after modifiers, and keep the most serious theft/vehicle offenses below intentional homicide unless the facts involve public safety danger beyond the taking itself.

### Drugs

California's rough ladder is simple possession below possession for sale, which is below sale/transport/trafficking. The simulated code follows that structure for most controlled substances.

The main inconsistency is simple possession:

| Charge Degree | Fine | Time | Finding |
| --- | ---: | ---: | --- |
| Possession of Cocaine | 500 | 0 | Consistent with low-custody simple possession policy. |
| Possession of Amphetamines | 300 | 0 | Consistent with low-custody simple possession policy. |
| Possession of Opioids | 350 | 0 | Consistent with low-custody simple possession policy. |
| Possession of Marijuana | 200 | 15 | Inconsistent if other simple possession charges are 0-time misdemeanors. |
| Sale of Controlled Substance | 800 | 10 | Lower than trafficking; plausible. |
| Drug Trafficking | 5000 | 60 | Very high; should either sit just below homicide or be reserved for major trafficking facts. |

Recommended adjustment: either reduce marijuana possession to match other simple possession charges, or define the marijuana degree as aggravated possession beyond personal use. Keep trafficking high, but consider 45-55 if First Degree Murder remains near 70-90.

### Weapons and Public Safety

California distinguishes simple possession, aggravated possession, altered/illegal weapons, assault weapons, manufacturing, and trafficking. The simulated code captures that structure, but a few values need hierarchy tuning.

| Charge Degree | Fine | Time | Finding |
| --- | ---: | ---: | --- |
| Criminal Possession of Weapon, Class A | 250 | 5 | Felony status may be right if this covers dangerous weapons, but punishment is lighter than many misdemeanors. |
| Criminal Possession of Weapon, Class B | 2000 | 10 | Plausible low felony if Class B includes firearms. |
| Criminal Sale of Weapon, Class B | 5000 | 10 | Sale should usually sit above possession. |
| Criminal Sale of Weapon, Class D | 12000 | 60 | Top-tier, but should generally sit below intentional murder unless mass-danger facts are built in. |
| Illegal Manufacturing of Firearms | 5000 | 10 | Low for manufacturing; consider moving closer to trafficking/sale. |
| Possession of Firearms Without Serial Numbers | 2500 | 5 | Plausible as lower felony or serious misdemeanor depending on local policy. |
| Possession of Illegal Firearm Modifications | 4000 | 5 | Fine-heavy; consider felony if it covers automatic conversion or suppressors. |

Recommended adjustment: preserve firearm status offenses as lower felonies where needed, but make sale/manufacturing/trafficking clearly higher than possession and clearly lower than homicide unless exceptional danger is present.

### Regulatory, Wildlife, and Economic Crimes

California often uses high fines for regulatory and resource crimes, so high wildlife or commercial fines are not inherently wrong. The issue is whether those fines distort the visible severity ladder in the MDT.

| Charge Degree | Fine | Time | Finding |
| --- | ---: | ---: | --- |
| Illegal Fishing | 6250 | 15 | Fine exceeds many violent felonies; plausible only if this represents serious commercial/protected-resource conduct. |
| Fishing in Unauthorized Zone | 3275 | 5 | Fine-heavy but plausible as regulatory deterrence. |
| Operating an Unlicensed Import/Export Business | 20000 | 50 | Very high; should be organized/high-value conduct, not mere licensing failure. |
| Smuggling Precious Metals | 6000 | 15 | Plausible economic felony. |

Recommended adjustment: use high fines for economic deterrence, but keep custody time lower than serious violence unless the offense creates major public danger or organized criminal harm.

### Insurrection and Global Maximum

The JSON sentencing guidelines set `maxTime` to 120, but Insurrection has a base time of 240.

That is a structural inconsistency. If 240 is meant to be available, the global guideline should be updated. If 120 is the intended ceiling, Insurrection should be reduced to 120 or placed in a special exception framework.

Recommended adjustment: set Insurrection to 120 unless the penal code intentionally allows exceptional sentences beyond the global maximum.

### Insurrection Exceeds the Global Sentencing Guideline

The JSON sentencing guidelines set `maxTime` to 120, but Insurrection has a base time of 240.

That is a structural inconsistency. If 240 is meant to be available, the global guideline should be updated. If 120 is the intended ceiling, Insurrection should be reduced to 120 or placed in a special exception framework.

Recommended adjustment: set Insurrection to 120 unless the penal code intentionally allows exceptional sentences beyond the global maximum.

### Fines Sometimes Communicate a Different Hierarchy Than Time

Fine hierarchy is less coherent than custody hierarchy.

Examples:

| Charge Degree | Classification | Fine | Time | Concern |
| --- | --- | ---: | ---: | --- |
| Illegal Fishing | Misdemeanor | 6250 | 15 | Higher fine than many felonies, including murder |
| Criminal Use of Weapon | Misdemeanor | 4000 | 15 | Very high fine for a misdemeanor weapon-use offense |
| Possession of Illegal Firearm Modifications | Misdemeanor | 4000 | 5 | High fine, low time |
| Operating an Unlicensed Import/Export Business | Felony | 20000 | 50 | Fine is tied for highest ordinary non-insurrection penalty |

High regulatory fines can make sense, especially for wildlife or commercial offenses. The issue is whether the code wants fines to reflect moral seriousness, economic deterrence, or both. Right now, fines appear to do both in different places.

Recommended standard: use time to express public danger and moral blameworthiness; use fines to express economic harm, profit motive, contraband value, and regulatory deterrence.

## Current Misdemeanor/Felony Cutoff

The current practical cutoff is inconsistent.

Observed boundaries:

| Boundary | Current Pattern |
| --- | --- |
| Infraction | Always 0 base time |
| Misdemeanor | 0-25 base time |
| Felony | 5-240 base time |
| Lowest felony time | 5 |
| Highest misdemeanor time | 25 |

Because the ranges overlap, classification is currently based more on charge type than on punishment severity.

That can work when the classification expresses legal status rather than only sentence length. For example, a weapons offense may be a felony even at 5 time because felony status itself matters. But the overlap is broad enough that two similarly punished offenses may feel arbitrarily classified.

Examples of misdemeanors at or above 15 time:

| Charge Degree | Fine | Time |
| --- | ---: | ---: |
| Impersonating | 1250 | 25 |
| Possession of Stolen Government Identification | 200 | 20 |
| Possession of Government-Issued Items | 1000 | 20 |
| Embezzlement | 1000 | 20 |
| Harboring a Fugitive | 375 | 20 |
| Violation of Restraining Order | 525 | 20 |
| Possession of Marijuana | 200 | 15 |
| Illegal Fishing | 6250 | 15 |
| Forgery | 650 | 15 |
| Criminal Use of Weapon | 4000 | 15 |
| Vehicle Tampering | 175 | 15 |
| Battery | 275 | 15 |
| Aiding and Abetting | 140 | 15 |
| Unlawful Practice | 1500 | 15 |

Examples of felonies at or below 10 time:

| Charge Degree | Fine | Time |
| --- | ---: | ---: |
| Criminal Possession of Ammunition | 500 | 5 |
| Criminal Possession of Weapon, Class A | 250 | 5 |
| Possession of Contraband in a Government Facility | 200 | 5 |
| Smuggling Contraband | 4000 | 5 |
| Possession of Drug Manufacturing Materials | 750 | 7 |
| Unlawful Production of Moonshine | 750 | 7 |
| Criminal Possession of Weapon, Class B | 2000 | 10 |
| Criminal Sale of Weapon, Class B | 5000 | 10 |
| Escaping | 1005 | 10 |
| Grand Theft Auto, Class A | 120 | 10 |
| Illegal Manufacturing of Firearms | 5000 | 10 |

## Recommended Cutoff Standard

Recommended baseline:

| Classification | Recommended Base Time Standard | Recommended Use |
| --- | ---: | --- |
| Infraction | 0 | Fine-only traffic, licensing, minor regulatory, and low-level public order violations |
| Misdemeanor | 1-15 | Low-to-moderate harm, non-serious possession, disorder, minor violence, ordinary obstruction, and lower-value property crimes |
| Serious misdemeanor / wobbler review zone | 10-15 | Conduct that may become felony with aggravating facts, repeat behavior, weapons, protected victims, or organized activity |
| Felony | 20+ | Serious violence, major theft/fraud, burglary/robbery, trafficking, government-security offenses, and dangerous weapons conduct |
| Low-time felony exception | 5-15 | Reserved for offenses where felony status matters even if the base jail time is modest |

Recommended rule:

1. If a degree has 0 base time, classify it as an infraction unless there is a strong reason for misdemeanor status.
2. If a misdemeanor has more than 15 base time, review it for either felony classification or a reduced base time.
3. If a felony has less than 10 base time, keep it felony only if felony status itself is important to the offense.
4. Use 20 base time as the normal point where felony classification begins.
5. Use 30+ base time for major violent felonies, serious organized crime, and major government/security offenses.
6. Use 45+ base time for homicide, top-tier trafficking, terrorism/insurrection-type conduct, and the most serious public safety offenses.

## Specific Review Recommendations

| Area | Recommendation |
| --- | --- |
| Homicide | Raise First Degree Murder to 60-75 and Second Degree Murder to 45-60, or reduce non-homicide 60-time offenses so intentional murder remains higher. |
| Insurrection | Bring base time within the global 120 max or explicitly revise the global guideline to allow exceptional sentences. |
| Drug possession | If simple possession is intended to be cite-and-release, keep 0-time misdemeanor possession for controlled substances; if not, make all drug possession degrees consistent. Marijuana possession at 15 time stands out against cocaine, amphetamines, and opioids at 0 time. |
| Weapon possession | Low-time felonies can remain if felony status is important, but Class A weapon possession at 5 time and 250 fine may feel lighter than several misdemeanors involving actual harm. |
| Weapon use | Criminal Use of Weapon at misdemeanor 15 time and 4000 fine should be reviewed. If the conduct is use during a crime or against a person, felony treatment may be more coherent. If it is broader brandishing/misuse, the fine can be reduced and other charges can carry the main punishment. |
| Wildlife fines | High fines may be appropriate for conservation deterrence, but ordinary Illegal Fishing at 6250 exceeds many felonies. Consider reserving that fine level for commercial, organized, protected-species, or repeat conduct. |
| Government/public administration possession offenses | Several misdemeanors sit at 20 time. These may be good felony candidates if they involve fraudulent use, facility security, or impersonation. If they are mere possession offenses, consider reducing to 10-15. |
| Vehicle offenses | Vehicle Operation is mostly coherent as infraction-heavy. Reckless Speeding 40+ is a misdemeanor with 0 time; either classify it as an infraction or assign a small custody value if misdemeanor status is intended. |

## Bottom Line

The penal code's hierarchy is broadly usable, and the most serious crimes generally sit above ordinary offenses. The recommended calibration point is California's relative sentencing ladder, not any single comparison: homicide should sit near the top, aggravated violence should outrank ordinary property crime, trafficking/sale should outrank simple possession, and regulatory/economic crimes should use fines more heavily than custody unless they create major public danger.

The two biggest cleanup opportunities are:

1. Make homicide and top-tier violence sit more clearly above ordinary trafficking, theft, and regulatory crimes.
2. Normalize the misdemeanor/felony boundary so classification and base time tell the same story more often.

The recommended cutoff is: infractions at 0 time, misdemeanors generally at 1-15 time, felonies generally at 20+ time, and a narrow 10-15 review zone for wobblers or low-time felonies where felony status is independently important.
