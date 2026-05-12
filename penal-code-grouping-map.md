# Penal Code Grouping Map

This map proposes a conservative category-by-category migration from one-charge-per-statute records into charge families with degrees and liability options. It is review-only and does not change `ef-mdt-penal-code.json`.

## Conventions

- Proposed family codes use `EF-PC-{categoryIndex}-{familyIndex}`.
- `Degree` rows become charge degrees in a later JSON migration.
- `Liability Option` rows represent existing attempted/accessory statutes that should become liability options when the related offense family is migrated.
- Existing source codes, classifications, base fines, base times, and descriptions are preserved for review.
- Charge/modifier overlap is intentionally deferred; every existing statute is still mapped here.

## 1. Offenses Against Persons

Source charges: 29. Mapped entries: 29.

### EF-PC-01-001 - Assault

Source charges being condensed: PC-1001 Simple Assault; PC-1002 Assault; PC-1003 Aggravated Assault; PC-1004 Assault with a Deadly Weapon

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1001 | Simple Assault | misdemeanor | 150 | 1 | A person who intentionally puts another in the reasonable belief of imminent physical harm or offensive contact is guilty under this code section. |
| Degree | PC-1002 | Assault | misdemeanor | 285 | 10 | A person who intentionally puts another in the reasonable belief of imminent serious physical harm or offensive contact is guilty under this code section. |
| Degree | PC-1003 | Aggravated Assault | felony | 325 | 15 | A person who uses intentional and unlawful force or violence to cause physical harm to another person is guilty under this code section. |
| Degree | PC-1004 | Assault with a Deadly Weapon | felony | 475 | 20 | A person who attempts to cause or threaten immediate harm to another while using a weapon, tool, or other dangerous item to communicate that threat is guilty under this code section. |

Notes: Clear severity family from simple assault through deadly-weapon assault.

### EF-PC-01-002 - Battery

Source charges being condensed: PC-1005 Battery; PC-1006 Aggravated Battery; PC-1029 Battery on a Public Servant or Peace Officer

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1005 | Battery | misdemeanor | 275 | 15 | A person who unlawfully applies force directly or indirectly upon another person or their personal belongings, causing bodily injury or offensive contact is guilty under this code section. |
| Degree | PC-1006 | Aggravated Battery | felony | 375 | 20 | A person who intentionally and unlawfully applies force directly or indirectly upon another person or their personal belongings, causing bodily injury or offensive contact is guilty under this code section. |
| Degree | PC-1029 | Battery on a Public Servant or Peace Officer | felony | 1250 | 25 | A person who intentionally and unlawfully applies force directly or indirectly upon a public servant or peace officer, while in the execution of their duties, is guilty under this code section. |

Notes: Public-servant battery remains a degree in this pass; charge/modifier overlap is deferred.

### EF-PC-01-003 - Manslaughter

Source charges being condensed: PC-1007 Involuntary Manslaughter; PC-1008 Vehicular Manslaughter

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1007 | Involuntary Manslaughter | felony | 750 | 20 |  A person who unintentionally kills another, with or without a quarrel or heat of passion is guilty under this code section. A person who, through a criminal accident or negligence, causes someones death is guilty under this code section. |
| Degree | PC-1008 | Vehicular Manslaughter | felony | 750 | 25 | A person who, while operating a vehicle, through a criminal accident or negligence, causes someones death is guilty under this code section. |

### EF-PC-01-004 - Murder

Source charges being condensed: PC-1010 Second Degree Murder; PC-1012 First Degree Murder; PC-1014 Murder of a Public Servant or Peace Officer; PC-1009 Attempted Murder of a Civilian; PC-1011 Accessory to Second Degree Murder; PC-1013 Accessory to First Degree Murder; PC-1015 Attempted Murder of a Public Servant or Peace Officer; PC-1016 Accessory to the Murder of a Public Servant or Peace Officer

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1010 | Second Degree Murder | felony | 1750 | 40 | A person who unlawfully kills another person either by intentional malice or reckless disregard that occurs in the spur of the moment is guilty under this code section. |
| Degree | PC-1012 | First Degree Murder | felony | 2500 | 50 | A person who commits the intentional killing which is done in a way that is willful, deliberate and premeditated is guilty under this code section. Additionally, a person who kills another individual while engaging in a felony offense, that has been proved to be a premeditated act, is guilty under this code section. |
| Degree | PC-1014 | Murder of a Public Servant or Peace Officer | felony | 12000 | 120 | A person who commits the intentional killing of a public servant or peace officer, while in the execution of their duties, in a way that is willful, deliberate and premeditated is guilty under this code section. |
| Liability Option | PC-1009 | Attempted Murder of a Civilian | felony | 1500 | 30 | A person who takes a direct step towards killing another person and intended to kill that person is guilty under this code section. A person who is hired to murder, slay, or execute another person for material or financial gain, even if a direct step towards the killing is not taken, is guilty under this code section. |
| Liability Option | PC-1011 | Accessory to Second Degree Murder | felony | 500 | 25 | A person who assists another person to commit murder of the second degree is guilty under this code section. |
| Liability Option | PC-1013 | Accessory to First Degree Murder | felony | 1500 | 35 | A person who assists another person to commit murder of the first degree is guilty under this code section. |
| Liability Option | PC-1015 | Attempted Murder of a Public Servant or Peace Officer | felony | 9500 | 80 | A person who attempts to unlawfully kill or cause great bodily harm to a public servant or peace officer, while in the execution of their duties, is guilty under this code section. |
| Liability Option | PC-1016 | Accessory to the Murder of a Public Servant or Peace Officer | felony | 5000 | 50 | A person who assists another person who attempts to unlawfully kill or cause great bodily harm to a public servant or peace officer, while in the execution of their duties, is guilty under this code section. |

Notes: Attempted/accessory murder charges become liability options tied to the relevant murder degree during migration.

### EF-PC-01-005 - Unlawful Imprisonment

Source charges being condensed: PC-1017 Unlawful Imprisonment; PC-1023 Unlawful Imprisonment of a Public Servant or Peace Officer.

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1017 | Unlawful Imprisonment | misdemeanor | 300 | 1 | A person who intentionally restricts anothers freedom of movement without their consent is guilty under this code section |
| Degree | PC-1023 | Unlawful Imprisonment of a Public Servant or Peace Officer. | felony | 750 | 25 | A person who intentionally restricts a public servant or peace officers freedom of movement without their consent is guilty under this code section |

Notes: Public-servant victim variant remains a degree in this pass.

### EF-PC-01-006 - Kidnapping and Hostage Taking

Source charges being condensed: PC-1018 Kidnapping; PC-1021 Hostage Taking; PC-1019 Accessory to Kidnapping; PC-1020 Attempted Kidnapping; PC-1022 Accessory to Hostage Taking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1018 | Kidnapping | felony | 500 | 15 | A person who abducts or confines another individual against their will by force, threat, or deception, is guilty under this code section.  |
| Degree | PC-1021 | Hostage Taking | felony | 750 | 20 | A person who kidnaps someone in an attempt to gain the power to attain something, with threat of their life is guilty under this code section. |
| Liability Option | PC-1019 | Accessory to Kidnapping | misdemeanor | 150 | 7 | A person who, without directly committing the act of kidnapping, knowingly aids, assists, encourages, or facilitates the commission of the kidnapping by another person is guilty under this code section. |
| Liability Option | PC-1020 | Attempted Kidnapping | felony | 150 | 10 | A person who takes a direct step towards the kidnapping of another person is guilty under this code section. |
| Liability Option | PC-1022 | Accessory to Hostage Taking | misdemeanor | 150 | 10 | A person who helps someone commit hostage taking is guilty under this code section. |

Notes: Attempt/accessory variants become liability options.

### EF-PC-01-007 - Criminal Threats

Source charges being condensed: PC-1024 Criminal Threats

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1024 | Criminal Threats | misdemeanor | 200 | 1 | A person who communicates to another that they will physically harm or kill such other, placing such other in a reasonable state of fear for their own safety is guilty under this code section. Such communication can be not just verbal, but also in writing or transmitted through other media is guilty under this code section. |

### EF-PC-01-008 - Reckless Endangerment

Source charges being condensed: PC-1025 Reckless Endangerment

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1025 | Reckless Endangerment | misdemeanor | 175 | 10 | A person who consciously disregards the potential risks or dangers of their actions which create a substantial serious risk of injury to another person is guilty under this code section. |

### EF-PC-01-009 - Gang Related Enhancement

Source charges being condensed: PC-1026 Gang Related Enhancement

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1026 | Gang Related Enhancement | felony | 500 | 10 | This charge is added to another charge, when the individualâ€™s actions are connected to or motivated by gang activity, which the individual is associated with. |

Notes: Kept as a singleton source mapping; later charge/modifier cleanup may convert this to a modifier.

### EF-PC-01-010 - Desecration of a Human Corpse

Source charges being condensed: PC-1027 Desecration of a Human Corpse

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1027 | Desecration of a Human Corpse | felony | 1000 | 30 | Any act committed after the death of a human being including, but not limited to, dismemberment, disfigurement, mutilation, burning, or any act committed to cause the dead body to be devoured, scattered or dissipated |

### EF-PC-01-011 - Torture

Source charges being condensed: PC-1028 Torture

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-1028 | Torture | felony | 1500 | 20 | A person who intentionally causes extreme pain and suffering to someone for reasons such as punishment, extracting a confession, interrogation, revenge, extortion, or any sadistic purpose, is guilty under this code section. |

## 2. Offenses Involving Theft

Source charges: 27. Mapped entries: 27.

### EF-PC-02-001 - Theft by Property Value

Source charges being condensed: PC-2001 Petty Theft; PC-2002 Grand Theft; PC-2013 Grand Larceny

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2001 | Petty Theft | infraction | 400 | 0 | A person who steals or takes the personal property of another worth $2000 or less is guilty under this code section. |
| Degree | PC-2002 | Grand Theft | misdemeanor | 850 | 10 | A person who steals or takes the personal property of another worth more than $2,000 but less than $15,000 or a firearm of any value is guilty under this code section. |
| Degree | PC-2013 | Grand Larceny | felony | 1000 | 30 | A person who steals or takes the personal property of another worth more than $15000 is guilty under this code section. |

### EF-PC-02-002 - Vehicle Theft

Source charges being condensed: PC-2003 Grand Theft Auto A; PC-2004 Grand Theft Auto B; PC-2005 Carjacking; PC-2019 Theft of an Aircraft; PC-2021 Theft of a Law Enforcement Vehicle

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2003 | Grand Theft Auto A | felony | 120 | 10 | A person who commits the theft of any motor vehicle, no matter the value is guilty under this code section. |
| Degree | PC-2004 | Grand Theft Auto B | felony | 400 | 15 | A person who commits the theft of any motor vehicle, no matter the value, while armed or committing another felony, is guilty under this code section. |
| Degree | PC-2005 | Carjacking | felony | 400 | 20 | A person who commits the theft of a motor vehicle from another person while it is being operated is guilty under this code section. |
| Degree | PC-2019 | Theft of an Aircraft | felony | 5000 | 40 | A person who commits the theft of an aircraft is guilty under this code section. |
| Degree | PC-2021 | Theft of a Law Enforcement Vehicle | felony | 10000 | 60 | A person who commits the theft of any motor vehicle owned by a law enforcement agency is guilty under this code section. |

Notes: Includes vehicle-specific theft degrees; carjacking is included because the core act is vehicle theft from a person.

### EF-PC-02-003 - Burglary

Source charges being condensed: PC-2006 Burglary

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2006 | Burglary | misdemeanor | 500 | 10 | A person who enters a structure without the permission of the owner or agent of the owner, typically with the intention of committing a criminal offense, is guilty under this code section. |

### EF-PC-02-004 - Robbery

Source charges being condensed: PC-2007 Robbery; PC-2010 Armed Robbery; PC-2008 Accessory to Robbery; PC-2009 Attempted Robbery; PC-2011 Accessory to Armed Robbery; PC-2012 Attempted Armed Robbery

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2007 | Robbery | felony | 1000 | 25 | A person who, acting alone or in concert with others, unlawfully takes personal property belonging to an individual or business from another person or their immediate presence, against their will, by means of force, intimidation, or fear, is guilty under this code section. |
| Degree | PC-2010 | Armed Robbery | felony | 1500 | 25 | A person who, acting alone or in concert with others, unlawfully takes personal property belonging to an individual or business from another person or their immediate presence, against their will, by means of force, intimidation, or fear, while using, displaying, or brandishing a firearm or other deadly weapon, is guilty under this code section. |
| Liability Option | PC-2008 | Accessory to Robbery | felony | 200 | 12 | A person who, without directly committing the act of robbery, knowingly aids, assists, abets, or facilitates the commission of a robbery by another person is guilty under this code section. |
| Liability Option | PC-2009 | Attempted Robbery | felony | 300 | 15 | A person who, acting alone or in concert with others, attempts to unlawfully take personal property belonging to an individual or business from another person or their immediate presence, against their will, by means of force, intimidation, or fear, is guilty under this code section. |
| Liability Option | PC-2011 | Accessory to Armed Robbery | felony | 300 | 12 | A person who, without directly committing the act of armed robbery, knowingly aids, assists, abets, or facilitates the commission of an armed robbery by another person, is guilty under this code section. |
| Liability Option | PC-2012 | Attempted Armed Robbery | felony | 300 | 25 | A person who, acting alone or in concert with others, attempts to unlawfully take personal property belonging to an individual or business from another person or their immediate presence, against their will, by means of force, intimidation, or fear, while using, displaying, or brandishing a firearm or other deadly weapon, is guilty under this code section. |

Notes: Attempt/accessory variants become liability options; armed robbery remains a degree.

### EF-PC-02-005 - Leaving Without Paying

Source charges being condensed: PC-2014 Leaving Without Paying

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2014 | Leaving Without Paying | infraction | 300 | 0 | A person who leaves a billed premises without paying the total amount of their bill is guilty under this code section. |

### EF-PC-02-006 - Possession of Nonlegal Currency

Source charges being condensed: PC-2015 Possession of Nonlegal Currency

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2015 | Possession of Nonlegal Currency | misdemeanor | 750 | 10 | A person who is in possession of, or attempts to use a fraudulent currency in the attempt to pass it off as legal tender is guilty under this code section. The fraudulent currency is subject to confiscation. |

### EF-PC-02-007 - Possession of Government-Issued Items

Source charges being condensed: PC-2016 Possession of Government-Issued Items

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2016 | Possession of Government-Issued Items | misdemeanor | 1000 | 20 | A person who is unlawfully in possession of a goverment issued firearm, vehicle, or other item is guilty under this code section. |

### EF-PC-02-008 - Items Used in the Commission of a Crime

Source charges being condensed: PC-2017 Possession of Items Used in the Commission of a Crime; PC-2018 Sale of Items Used in the Commission of a Crime

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2017 | Possession of Items Used in the Commission of a Crime | misdemeanor | 500 | 10 | A person in possession of tools used by that person to commit another crime, such as a firearm or burglary tools, is guilty under this code section. |
| Degree | PC-2018 | Sale of Items Used in the Commission of a Crime | misdemeanor | 100 | 15 | A person who is in possession of, or attempts to use a fraudulent currency in the attempt to pass it off as legal tender is guilty under this code section. The fraudulent currency is subject to confiscation. |

Notes: Grouped by title family; PC-2018 description appears to duplicate nonlegal currency text and should be reviewed later.

### EF-PC-02-009 - Criminal Possession of Stolen Property

Source charges being condensed: PC-2020 Criminal Possession of Stolen Property

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2020 | Criminal Possession of Stolen Property | misdemeanor | 200 | 10 | A person who has possession of stolen items, with knowledge that the item is stolen, is guilty under this code section. |

### EF-PC-02-010 - Customs and Smuggling Offenses

Source charges being condensed: PC-2022 Smuggling of Contraband; PC-2023 Smuggling of Precious Gemstones; PC-2024 Smuggling of Precious Metals; PC-2025 Customs Fraud; PC-2026 Operating an Unlicensed Import/Export Business; PC-2027 Accessory to Smuggling

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-2022 | Smuggling of Contraband | felony | 4000 | 5 | A person who, acting alone or in concert with others, unlawfully transports, imports, exports, or conceals valuable goods, luxury items, electronics, art, or other contraband materials across jurisdictional boundaries without proper documentation, licensing, or declaration to customs authorities is guilty under this code section. |
| Degree | PC-2023 | Smuggling of Precious Gemstones | felony | 5000 | 10 | A person who, acting alone or in concert with others, unlawfully transports, imports, exports, or conceals precious gemstones including but not limited to diamonds, emeralds, rubies, sapphires, and other valuable stones across jurisdictional boundaries without proper documentation, licensing, or declaration to customs authorities is guilty under this code section. |
| Degree | PC-2024 | Smuggling of Precious Metals | felony | 6000 | 15 | A person who, acting alone or in concert with others, unlawfully transports, imports, exports, or conceals precious metals including but not limited to gold, silver, platinum, and other valuable metals across jurisdictional boundaries without proper documentation, licensing, or declaration to customs authorities is guilty under this code section. |
| Degree | PC-2025 | Customs Fraud | misdemeanor | 1500 | 1 | A person who knowingly provides false information, false documentation, or misrepresents the nature, value, or quantity of goods to customs or other government authorities for the purpose of evading duties, taxes, or regulations is guilty under this code section. |
| Degree | PC-2026 | Operating an Unlicensed Import/Export Business | felony | 20000 | 50 | A person who operates a commercial import or export business without proper licensing, permits, or registration required by government authorities, or who conducts import/export activities on a commercial scale while evading regulatory oversight, is guilty under this code section. Transportation personnel including drivers, pilots, or vessel operators who knowingly participate in unlicensed commercial import/export operations are also guilty under this code section. Commercial scale is defined as: (1) importing/exporting goods valued at $100,000+ per transaction or $250,000+ aggregate over one month, (2) conducting 4+ import/export transactions within one month, (3) importing/exporting goods exceeding 200 kg per shipment, (4) operating with dedicated business infrastructure or commercial documentation, or (5) clear evidence of conducting activities for financial gain as a business venture. |
| Liability Option | PC-2027 | Accessory to Smuggling | misdemeanor | 1000 | 5 | A person who, without directly committing the act of smuggling, knowingly aids, assists, abets, or facilitates the commission of smuggling by another person, including providing transportation, storage, documentation, or other support services, is guilty under this code section. |

Notes: Accessory to smuggling becomes a liability option; customs fraud and unlicensed import/export remain degrees in the same import/export family.

## 3. Offenses Involving Fraud

Source charges: 8. Mapped entries: 8.

### EF-PC-03-001 - Impersonation

Source charges being condensed: PC-3001 Impersonating; PC-3002 Impersonating a Peace Officer or Public Servant; PC-3003 Impersonating a Judge

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-3001 | Impersonating | misdemeanor | 1250 | 25 | A person who attempts to assume the identity of someone else is guilty under this code section. |
| Degree | PC-3002 | Impersonating a Peace Officer or Public Servant | felony | 2050 | 30 | A person who attempts to assume the identity, or state that they are a peace officer or public servant, when they are not, are guilty under this code section. |
| Degree | PC-3003 | Impersonating a Judge | felony | 3500 | 45 | A person who attempts to assume the identity, or state that they are a judge, when they are not, are guilty under this code section. |

### EF-PC-03-002 - Possession of Stolen Government Identification

Source charges being condensed: PC-3005 Possession of Stolen Government Identification

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-3005 | Possession of Stolen Government Identification | misdemeanor | 200 | 20 | A person who is in possession of a piece of government identification that does not belong to them, who has not made any attempt to dispose of the item, is guilty under this section. |

### EF-PC-03-003 - Extortion

Source charges being condensed: PC-3006 Extortion

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-3006 | Extortion | felony | 1500 | 30 | A person who intimidates or influences another to provide or hand over properties or services is guilty under this code section. A person who utilizes or threatens their power or authority with demonstrated malice aforethought in order to compel action by another is guilty under this code section |

### EF-PC-03-004 - Fraud and Forgery

Source charges being condensed: PC-3007 Fraud; PC-3008 Forgery

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-3007 | Fraud | misdemeanor | 150 | 10 | A person who knowingly alters, creates, or uses a written document with the intent to defraud or deceive another is guilty under this code section.  |
| Degree | PC-3008 | Forgery | misdemeanor | 650 | 15 | A person who knowingly signs a document or agreement, electronic or otherwise, without the consent or authority of whom they are signing for is guilty under this code section. A person who creates fake government documents is guilty under this code section. |

### EF-PC-03-005 - Money Laundering

Source charges being condensed: PC-3009 Money Laundering

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-3009 | Money Laundering | felony | 4000 | 25 | A person who possesses, hides, transfers, receives, or maintains the storage of funds earned through comprehensive criminal activities is guilty under this code. A person who maintains an establishment with a purpose to launder funds collected through comprehensive criminal activities is guilty under this code. |

## 4. Offenses Involving Damage to Property

Source charges: 6. Mapped entries: 6.

### EF-PC-04-001 - Trespassing

Source charges being condensed: PC-4001 Trespassing; PC-4002 Felony Trespassing

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-4001 | Trespassing | misdemeanor | 455 | 5 | A person who remains on a property after being told to leave by the property owner, an agent of the property owner, or a peace officer, or returns to a property after having been previously trespassed from the property is guilty under this code section. |
| Degree | PC-4002 | Felony Trespassing | felony | 1500 | 15 | A person who, without proper authorization, enters any government-owned or managed facility that is secured with the intent of keeping ordinary citizens outside is guilty under this code section. |

### EF-PC-04-002 - Arson

Source charges being condensed: PC-4003 Arson

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-4003 | Arson | felony | 2500 | 15 | A person who intentionally and maliciously sets fire to or burns any structure, forest land, or property without prior authorization is guilty under this code section. A person who intentionally aids, counsels, or helps facilitate the burning of any structure, forest land, or property without proper authorization is guilty under this code section. |

### EF-PC-04-003 - Vandalism

Source charges being condensed: PC-4004 Vandalism; PC-4005 Vandalism of Government Property

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-4004 | Vandalism | infraction | 100 | 0 | A person that defaces, damages, or destroys property which belongs to another is guilty under this code section. |
| Degree | PC-4005 | Vandalism of Government Property | misdemeanor | 350 | 10 | A person that defaces, damages, or destroys property which belongs to a government agency is guilty under this code section. |

### EF-PC-04-004 - Littering

Source charges being condensed: PC-4006 Littering

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-4006 | Littering | infraction | 150 | 0 | As used in this section, "litter" means garbage, trash, waste, ashes, cans, bottles, wire, paper, cartons, vessel parts, vehicle parts, furniture, glass, or anything else of an unsightly or unsanitary nature. No person shall place any waste, refuse, litter or foreign substance in any area or receptacle except those provided for that purpose. |

## 5. Offenses Against Public Administration

Source charges: 17. Mapped entries: 17.

### EF-PC-05-001 - Bribery of a Government Official

Source charges being condensed: PC-5001 Bribery of a Government Official

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5001 | Bribery of a Government Official | felony | 200 | 20 | A person who offers or gives a monetary gift, gratuity, valuable goods, or other reward to a public official, a government employee, or peace officer in an attempt to influence their duties or actions is guilty under this code section. |

### EF-PC-05-002 - Anti-Mask Law

Source charges being condensed: PC-5002 Anti-Mask Law

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5002 | Anti-Mask Law | infraction | 150 | 0 | A person who wears a mask or face covering while committing a crime is guilty under this code section. A person who wears a mask in a government facility, after being asked to remove it, is guilty under this code section. |

### EF-PC-05-003 - Possession of Contraband in a Government Facility

Source charges being condensed: PC-5003 Possession of Contraband in a Government Facility

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5003 | Possession of Contraband in a Government Facility | felony | 200 | 5 | A person who possesses a controlled substance, illegal firearm, or any other illegal item while on the premesis of a government facility is guilty under this code section. |

### EF-PC-05-004 - Escape and Jailbreak

Source charges being condensed: PC-5004 Escaping; PC-5005 Jailbreak; PC-5006 Accessory to Jailbreak; PC-5007 Attempted Jailbreak

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5004 | Escaping | felony | 1005 | 10 | Any person arrested, detained, booked, charged, or convicted of any crime who thereafter escapes from a county or city jail, prison, community service, or custody of a Correctional or Parole Officer, Peace Officer, Police Officer, or Federal Agent is guilty under this code section. |
| Degree | PC-5005 | Jailbreak | felony | 2500 | 30 | A person who breaks out a prisoner from a correctional facility without authorization is guilty under this code section. |
| Liability Option | PC-5006 | Accessory to Jailbreak | felony | 500 | 20 | A person who helps someone to break out a prisoner from a correctional facility without authorization is guilty under this code section. |
| Liability Option | PC-5007 | Attempted Jailbreak | felony | 1000 | 20 | A person who attempts to break out a prisoner from a correctional facility without authorization is guilty under this code section. |

Notes: Accessory/attempted jailbreak become liability options.

### EF-PC-05-005 - Perjury

Source charges being condensed: PC-5008 Perjury

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5008 | Perjury | felony | 4000 | 20 | A person who willfully gives false information while testifying in court, during a deposition, or on a signed document presented to a court is guilty under this section. |

### EF-PC-05-006 - Court Order and Appearance Violations

Source charges being condensed: PC-5009 Violation of a Restraining Order; PC-5014 Violating a Court Order; PC-5015 Failure to Appear; PC-5016 Contempt of Court

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5009 | Violation of a Restraining Order | misdemeanor | 525 | 20 | A person who knowingly and intentionally violates the parameters of a restraining order against them is guilty under this code section. |
| Degree | PC-5014 | Violating a Court Order | misdemeanor | 800 | 10 | A person who fails to abide by a court order ruled by a judge of San Andreas is guilty under this code section. |
| Degree | PC-5015 | Failure to Appear | misdemeanor | 650 | 10 | A person who fails to appear to a lawfully binding court summons or order for appearance is guilty under this code section. |
| Degree | PC-5016 | Contempt of Court | misdemeanor | 300 | 5 | A person who is disrespectful of the court process, such as being excessively loud or belligerent, refusing to be sworn in as a witness, refusing to comply with a judges request, is guilty under this code section. Repeated offenses can result in multiplication of the maximum fine and sentence. |

Notes: Grouped as court compliance conduct while preserving each source as its own degree.

### EF-PC-05-007 - Embezzlement

Source charges being condensed: PC-5010 Embezzlement

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5010 | Embezzlement | misdemeanor | 1000 | 20 | A person who steals or misappropriates funds in their trust or belonging to their employer is guilty under this code section. |

### EF-PC-05-008 - Unlawful Practice

Source charges being condensed: PC-5011 Unlawful Practice

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5011 | Unlawful Practice | misdemeanor | 1500 | 15 | A person who practices medical procedures that they are not licenced or lawfully allowed to practice is guilty under this code section. |

### EF-PC-05-009 - Misuse of Emergency Systems

Source charges being condensed: PC-5012 Misuse of Emergency Systems

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5012 | Misuse of Emergency Systems | infraction | 600 | 0 | A person who misuses an emergency system, such as 911 or panic buttons, to waste police time or resources, is guilty under this code section |

### EF-PC-05-010 - Conspiracy

Source charges being condensed: PC-5013 Conspiracy

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5013 | Conspiracy | misdemeanor | 0 | 0 | A person who conspires to commit a crime, either alone or with a group, is guilty under this section. A person charged with this can be charged up to half of the fine and sentence of the conspired crime. |

### EF-PC-05-011 - Resisting Arrest

Source charges being condensed: PC-5017 Resisting Arrest

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-5017 | Resisting Arrest | misdemeanor | 750 | 10 | A person who avoids apprehension from an officer by non-vehicular means or resists apprehension by any physical means is guilty under this code section is guilty under this code section. |

## 6. Offenses Against Public Order

Source charges: 19. Mapped entries: 19.

### EF-PC-06-001 - Peace Officer Compliance

Source charges being condensed: PC-6001 Disobeying a Peace Officer; PC-6013 Failure to Provide Identification

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6001 | Disobeying a Peace Officer | infraction | 175 | 0 | A person who fails to comply with a lawful order given from an on duty peace officer or public servant is guilty under this code section. |
| Degree | PC-6013 | Failure to Provide Identification | misdemeanor | 350 | 1 | A person who fails to identify when lawfully ordered to by a Law Enforcement Officer is guilty under this code section. |

### EF-PC-06-002 - Public Disorder

Source charges being condensed: PC-6002 Disorderly Conduct; PC-6003 Disturbing the Peace; PC-6008 Inciting a Riot; PC-6015 Unlawful Assembly

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6002 | Disorderly Conduct | infraction | 125 | 0 | A person who commits such acts that are of a nature to corrupt the public morals, or outrage the sense of public decency, or affect the peace and quiet of persons who may witness them, or engages in brawling or fighting, or engages in such conduct as to constitute a breach of the peace is guilty under this code section. |
| Degree | PC-6003 | Disturbing the Peace | infraction | 100 | 0 | A person who violates a reasonable expectation of peace in a public area is guilty under this code section. |
| Degree | PC-6008 | Inciting a Riot | felony | 500 | 25 |  A person who with the intent to cause a riot does an act or engages in conduct that urges a riot, or urges others to commit acts of force or violence, or the burning or destroying of property, and at a time and place and under circumstances that produce a clear and present and immediate danger of acts of force or violence or the burning or destroying of property is guilty under this code section. |
| Degree | PC-6015 | Unlawful Assembly | misdemeanor | 750 | 10 | Whenever two or more persons, assembled and acting together, make any attempt or advance toward the commission of an act which would be a riot if actually committed. Whenever two or more persons assemble together to do an unlawful act, or do a lawful act in a violent, boisterous, or tumultuous manner is guilty under this code section. |

Notes: Includes escalating public-order conduct from disorder through riot incitement/unlawful assembly.

### EF-PC-06-003 - False Reporting

Source charges being condensed: PC-6004 False Reporting

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6004 | False Reporting | misdemeanor | 175 | 10 | A person who reports to any peace officer that a felony or misdemeanor has been committed knowing the report to be false is guilty under this code section. |

### EF-PC-06-004 - Harassment and Stalking

Source charges being condensed: PC-6005 Harassment; PC-6017 Stalking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6005 | Harassment | misdemeanor | 250 | 10 | A person who makes communication, whether in person or by means of internet, phone, or other devices (may also apply to circumventing a block on a phone number) with the repeated intent to cause annoyance. |
| Degree | PC-6017 | Stalking | felony | 350 | 30 | A person who intentionally and maliciously follows or harasses another person who has made it known that they do not consent to such following or harassment is guilty under this code section. A person whose actions cause another person to reasonably fear for their safety, or the safety of any person is guilty under this code section. |

### EF-PC-06-005 - Obstruction of Justice

Source charges being condensed: PC-6006 Misdemeanor Obstruction of Justice; PC-6007 Felony Obstruction of Justice

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6006 | Misdemeanor Obstruction of Justice | misdemeanor | 500 | 10 | A person who shows a clear and motivated attempt to prevent a peace officer from conducting their duties or completing an investigation is guilty under this code section. |
| Degree | PC-6007 | Felony Obstruction of Justice | felony | 900 | 15 | A person who shows a clear and motivated attempt to prevent an official government proceeding or government officer from completing their assigned duties is guilty under this code section. |

### EF-PC-06-006 - Loitering on Government Properties

Source charges being condensed: PC-6009 Loitering on Government Properties

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6009 | Loitering on Government Properties | infraction | 100 | 0 | Criminal loitering refers to anyone who is lingering or hanging around in a public or private area, with the intent to commit criminal activity, or who is assisting and/or aiding another with a crime |

### EF-PC-06-007 - Vehicle Tampering

Source charges being condensed: PC-6010 Vehicle Tampering

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6010 | Vehicle Tampering | misdemeanor | 175 | 15 | A person who intentionally tampers or damages a vehicle without the consent of the owner is guilty under this code section. |

### EF-PC-06-008 - Tampering

Source charges being condensed: PC-6011 Evidence Tampering; PC-6012 Witness Tampering

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6011 | Evidence Tampering | felony | 150 | 20 | A person who willfully and intentionally destroys or attempts to destroy, creates or attempts to create false evidence, conceal, or alter any evidence that can later potentially be used in a Criminal investigation or court proceeding is guilty under this code section. |
| Degree | PC-6012 | Witness Tampering | felony | 1000 | 25 | This pertains to a person who knowingly and maliciously prevents or encourages any witness or victim from attending or giving testimony at any trial, proceeding, or inquiry authorized by law with the use of bribery, fear, or other tactics. |

### EF-PC-06-009 - Vigilantism

Source charges being condensed: PC-6014 Vigilantism

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6014 | Vigilantism | felony | 150 | 30 | A person who unlawfully attempts to enforce law, or act as law enforcement, is guilty under this code section. |

### EF-PC-06-010 - Government Corruption

Source charges being condensed: PC-6016 Government Corruption

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6016 | Government Corruption | felony | 2000 | 40 | The deliberate abuse of authority by any public official, government employee, or elected representative for personal, financial, political, or organizational gain. This includes, but is not limited to: accepting bribes, engaging in quid pro quo arrangements, falsifying official records, misappropriating public resources, interfering with law enforcement investigations, or using official status to shield oneself or others from lawful accountability. |

### EF-PC-06-011 - Aiding and Harboring

Source charges being condensed: PC-6018 Aiding and Abetting; PC-6019 Harboring a Fugitive

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-6018 | Aiding and Abetting | misdemeanor | 140 | 15 | A person who assists in the committing of a crime, or assists in the fleeing of a wanted person is guilty under this code section. |
| Degree | PC-6019 | Harboring a Fugitive | misdemeanor | 375 | 20 | A person who knowingly and intentionally hides, harbours or prevents law enforcement from finding a wanted felon is guilty under this code section. |

## 7. Offenses Against Health and Morals

Source charges: 22. Mapped entries: 22.

### EF-PC-07-001 - Marijuana Offenses

Source charges being condensed: PC-7001 Illegal Cultivation of Marijuana; PC-7002 Illegal Cultivation of Marijuana; PC-7003 Possession of Marijuana; PC-7004 Possession of Marijuana with Intent to Distribute

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7001 | Illegal Cultivation of Marijuana | misdemeanor | 2500 | 5 | Any individual who is found to be cultivating marijuana in an amount greater than 6 marijuana plants or is cultivating marijuana on public property is in violation of this code. Cultivation of marijuana plants for personal use is restricted to private property, and no greater than 6 plants per property/owner. Plants can be confiscated and/or destroyed by police upon receipt of warrant (for private property) for seizure. |
| Degree | PC-7002 | Illegal Cultivation of Marijuana | felony | 5000 | 10 | Any individual who is found to be cultivating marijuana in an amount greater than 6 marijuana plants under the following conditions is classified as a felony: If the individual has two or more prior convictions for cultivating more than six marijuana plants, if the individual has a prior conviction for a serious violent felony, and or the cultivation activity involves violation of environmental laws. Cultivation of marijuana plants for personal use is restricted to private property, and no greater than 6 plants per property/owner. Plants can be confiscated and/or destroyed by police upon receipt of a warrant (private property) for seizure. |
| Degree | PC-7003 | Possession of Marijuana | misdemeanor | 200 | 15 | A person who is in possession of illegal marijuana that weighs more than 10 kg, but less than 100 kg is guilty under this code section. |
| Degree | PC-7004 | Possession of Marijuana with Intent to Distribute | felony | 500 | 20 | A person found in possession of over 100 kg of illegal marijuana, with more than 30 kg of marijuana individually packaged for sale (e.g., in joints, baggies, or bricks), and/or also possesses items commonly used in drug distribution (such as scales, empty baggies, etc.), weighing more than 50 kg, is guilty under this code section. |

### EF-PC-07-002 - Cocaine Possession and Distribution

Source charges being condensed: PC-7005 Misdemeanor Possession of Cocaine; PC-7006 Felony Possession of Cocaine; PC-7007 Possession of Cocaine with Intent to Distribute

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7005 | Misdemeanor Possession of Cocaine | misdemeanor | 500 | 0 | A person who is in possession of cocaine, either in powder or crack formulations, under 10 kg is guilty under this code section. |
| Degree | PC-7006 | Felony Possession of Cocaine | felony | 750 | 15 | A person who is in possession of cocaine, either in powder or crack formulations, greater than 10kg but less than 100kg is guilty under this code section. |
| Degree | PC-7007 | Possession of Cocaine with Intent to Distribute | felony | 1300 | 20 | A person who is in possession of cocaine, either in powder or crack formulations, that exceeds 100 kg in weight, or is packaged individually for sale, and possesses items used in the distribution of drugs (ie. scale, empty baggies, etc.) and weighs more than 50 kg, is guilty under this code section. |

### EF-PC-07-003 - Amphetamine Possession and Distribution

Source charges being condensed: PC-7008 Misdemeanor Possession of Amphetamines; PC-7009 Felony Possession of Amphetamines; PC-7010 Possession of Amphetamines with Intent to Distribute

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7008 | Misdemeanor Possession of Amphetamines | misdemeanor | 300 | 0 | A person who is in possession of amphetamines, including but not limited to methamphetamine and adderall, under 10 kg is guilty under this code section. |
| Degree | PC-7009 | Felony Possession of Amphetamines | felony | 750 | 15 | A person who is in possession of amphetamines, including but not limited to methamphetamine and adderall, greater than 10kg but less than 100kg is guilty under this code section. |
| Degree | PC-7010 | Possession of Amphetamines with Intent to Distribute | felony | 1500 | 20 | A person who is in possession of amphetamines, including but not limited to methamphetamine and adderall, that exceeds 100 kg in weight, or is packaged individually for sale, and possesses items used in the distribution of drugs (ie. scale, empty baggies, etc.) and weighs more than 50 kg, is guilty under this code section. |

### EF-PC-07-004 - Opioid Possession and Distribution

Source charges being condensed: PC-7011 Misdemeanor Possession of Opioids; PC-7012 Felony Possession of Opioids; PC-7013 Possession of Opioids with Intent to Distribute

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7011 | Misdemeanor Possession of Opioids | misdemeanor | 350 | 0 | A person who is in possession of opioids, including but not limited to morphine, heroin, hydrocodone, oxycodone, under 10 kg is guilty under this code section. |
| Degree | PC-7012 | Felony Possession of Opioids | felony | 450 | 15 | A person who is in possession of opioids, including but not limited to morphine, heroin, hydrocodone, oxycodone, greater than 10kg but less than 100kg is guilty under this code section |
| Degree | PC-7013 | Possession of Opioids with Intent to Distribute | felony | 1450 | 20 | A person who is in possession of amphetamines, including but not limited to opioids, including but not limited to morphine, heroin, hydrocodone, oxycodone, or is packaged individually for sale, and possesses items used in the distribution of drugs (ie. scale, empty baggies, etc.) and weighs more than 50 kg, is guilty under this code section. |

### EF-PC-07-005 - Possession of Drug Paraphernalia

Source charges being condensed: PC-7014 Possession of Drug Paraphernalia

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7014 | Possession of Drug Paraphernalia | misdemeanor | 350 | 5 | A person who is in possession of any equipment, product or material of any kind which is primarily intended or designed for use in injecting, ingesting, inhaling, or otherwise introducing into the human body a controlled substance. |

### EF-PC-07-006 - Possession of Drug Manufacturing Materials

Source charges being condensed: PC-7015 Possession of Drug Manufacturing Materials

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7015 | Possession of Drug Manufacturing Materials | felony | 750 | 7 | A person who is in possession of any equipment, product or material of any kind which could be used in manufacturing, compounding, converting, concealing, producing, processing, preparing a controlled substance. |

### EF-PC-07-007 - Controlled Substance Sale and Trafficking

Source charges being condensed: PC-7016 Sale of a controlled substance; PC-7017 Drug Trafficking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7016 | Sale of a controlled substance | misdemeanor | 800 | 10 | A person who sells, offers to sell, transports with the intent to sell, or gives away a controlled substance to another person, regardless of whether or not they possess that controlled substance is guilty under this code section. |
| Degree | PC-7017 | Drug Trafficking | felony | 5000 | 60 | A person who unlawfully transports a large quantity of a controlled substance, defined as greater than 250 kg, across, into, or out of the state is guilty under this section. |

### EF-PC-07-008 - Driving Under the Influence of Narcotics

Source charges being condensed: PC-7018 Driving Under the Influence of Narcotics

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7018 | Driving Under the Influence of Narcotics | felony | 300 | 20 | A person who operates a motor vehicle on a public roadway while under the influence of narcotics, or other medicine that inhibits your ability to drive safely is guilty under this code section. |

### EF-PC-07-009 - Public Intoxication

Source charges being condensed: PC-7019 Public Intoxication

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7019 | Public Intoxication | infraction | 150 | 0 | A person who is under the influence of alcohol in a public place, and disturbing the natural expectation of peace, is guilty under this code section. |

### EF-PC-07-010 - Public Indecency

Source charges being condensed: PC-7020 Public Indecency

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7020 | Public Indecency | infraction | 200 | 0 | A person who fails to appropriately dress themselves in a public place, or displays themselves to unconsenting parties in public areas, is guilty under this code section. |

### EF-PC-07-011 - Moonshine Offenses

Source charges being condensed: PC-7021 Unlawful Production of Moonshine; PC-7022 Possession or Distribution of Illegal Moonshine

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-7021 | Unlawful Production of Moonshine | felony | 750 | 7 | The act of manufacturing, distilling, or fermenting alcoholic beverages, such as moonshine, without proper licensing or permits as required by law. |
| Degree | PC-7022 | Possession or Distribution of Illegal Moonshine | misdemeanor | 350 | 5 | The act of possessing, transporting, or distributing unlicensed alcoholic beverages, such as moonshine, with the intent to sell or consume. |

## 8. Offenses Against Public Safety

Source charges: 22. Mapped entries: 22.

### EF-PC-08-001 - Criminal Possession of Weapons

Source charges being condensed: PC-8001 Criminal Possession of Weapon Class A; PC-8002 Criminal Possession of Weapon Class B; PC-8003 Criminal Possession of Weapon Class C; PC-8004 Criminal Possession of Weapon Class D

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8001 | Criminal Possession of Weapon Class A | felony | 250 | 5 | A person who illegally possesses a weapon of Class A is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class A weapons are defined as melee or blunt instruments that are designed to inflict damage, defined to include switchblades, knife, or brass knuckles. The charge of possessing a Class A weapon is a secondary offense. |
| Degree | PC-8002 | Criminal Possession of Weapon Class B | felony | 2000 | 10 | A person who illegally possesses a weapon of Class B is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class B weapons are defined as semi-automatic handguns or rifles. |
| Degree | PC-8003 | Criminal Possession of Weapon Class C | felony | 5000 | 15 | A person who illegally possesses a weapon of Class C is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class C weapons are defined as automatic handguns or rifles. |
| Degree | PC-8004 | Criminal Possession of Weapon Class D | felony | 7500 | 20 | A person who illegally possesses a weapon of Class D is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class D weapons are defined as heavy artillery and explosives, including rocket launchers, C4, grenades, home-made explosives. |

### EF-PC-08-002 - Criminal Sale of Weapons

Source charges being condensed: PC-8005 Criminal Sale of Weapon Class A; PC-8006 Criminal Sale of Weapon Class B; PC-8007 Criminal Sale of Weapon Class C; PC-8008 Criminal Sale of Weapon Class D

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8005 | Criminal Sale of Weapon Class A | felony | 450 | 25 | A person who illegally sells or distributes a weapon of Class A is guilty under this code section. Class A weapons are defined as melee or blunt instruments that are designed to inflict damage, defined to include switchblades, knife, or brass knuckles. |
| Degree | PC-8006 | Criminal Sale of Weapon Class B | felony | 5000 | 10 | A person who illegally sells or distributes a weapon of Class B is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class B weapons are defined as semi-automatic handguns or rifles. |
| Degree | PC-8007 | Criminal Sale of Weapon Class C | felony | 9000 | 15 | A person who illegally sells or distributes a weapon of Class C is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class C weapons are defined as automatic handguns or rifles. |
| Degree | PC-8008 | Criminal Sale of Weapon Class D | felony | 12000 | 60 | A person who illegally sells or distributes a weapon of Class D is guilty under this code section. Illegal possession is defined as someone who is not licensed to or legally able to carry a weapon based on their criminal history. Class D weapons are defined as heavy artillery and explosives, including rocket launchers, C4, grenades, home-made explosives. |

### EF-PC-08-003 - Criminal Use of Weapons and Explosives

Source charges being condensed: PC-8009 Criminal Use of Weapon; PC-8019 Criminal Use of Explosives

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8009 | Criminal Use of Weapon | misdemeanor | 4000 | 15 | A person who uses a weapon or firearm in the process of committing a crime is guilty under this code section. |
| Degree | PC-8019 | Criminal Use of Explosives | felony | 5000 | 30 | A person who uses explosives or incediaries in the act of committing a crime is guilty under this code section. |

### EF-PC-08-004 - Illegal Firearm Configuration

Source charges being condensed: PC-8010 Possession of Illegal Firearm Modifications; PC-8013 Possession of Firearms Without Serial Numbers

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8010 | Possession of Illegal Firearm Modifications | misdemeanor | 4000 | 5 | A person who is in possession of a firearm with modifications that are illegal is guilty under this code section. Examples include Full Auto Switch, extended magazines, suppressors, and serial number removal. |
| Degree | PC-8013 | Possession of Firearms Without Serial Numbers | misdemeanor | 2500 | 5 | A person who possesses a firearm that does not have a registered serial number with the State of San Andreas, regardless of the individual's gun license status, is guilty under this code section. |

### EF-PC-08-005 - Weapon Trafficking

Source charges being condensed: PC-8011 Weapon Trafficking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8011 | Weapon Trafficking | felony | 11000 | 45 | A person who is responsible for the mass transportation (excess of 8) illegal firearms and weapons within or across the state of San Andreas with the intention of sale or distribution is guilty under this code section. |

### EF-PC-08-006 - Illegal Manufacturing of Firearms

Source charges being condensed: PC-8012 Illegal Manufacturing of Firearms

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8012 | Illegal Manufacturing of Firearms | felony | 5000 | 10 | Any individual who manufactures a firearm must be eligible to own a firearm in the State. Any firearm manufactured in the State of San Andreas must be a legal weapon and meet all safety standards including containing an unique serial number that is registered with the State. San Andreas law prohibits individuals from manufacturing or assembling certain classes of firearms, including assault weapons and machine guns. The sale of self-made firearms is illegal. An individual found in violation is guilty of this code section.. |

### EF-PC-08-007 - Brandishing Weapons

Source charges being condensed: PC-8014 Brandishing a Weapon; PC-8015 Brandishing a Firearm

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8014 | Brandishing a Weapon | misdemeanor | 500 | 2 | A person who removes a weapon other than a firearm from concealment or holstering in a public place, either recklessly or threateningly, without obvious threat of harm or other lawful reason to use a weapon, is guilty under this code section. |
| Degree | PC-8015 | Brandishing a Firearm | misdemeanor | 2500 | 5 | A person who removes a firearm from concealment or holstering in a public place, either recklessly or threateningly, without obvious threat of harm or other lawful reason to use a firearm is guilty under this code section. |

### EF-PC-08-008 - Insurrection

Source charges being condensed: PC-8016 Insurrection

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8016 | Insurrection | felony | 20000 | 240 | A person who incites, sets on foot, assists, or engages in any rebellion or insurrection against the authority of the United States is guilty under this code section. |

### EF-PC-08-009 - Flying into Restricted Airspace

Source charges being condensed: PC-8017 Flying into Restricted Airspace

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8017 | Flying into Restricted Airspace | felony | 750 | 10 | A person who, while operating an aircraft, flies over restricted airspace, or flies into controlled airspace without prior authorization from air control, is guilty under this code section. |

### EF-PC-08-010 - Jaywalking

Source charges being condensed: PC-8018 Jaywalking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8018 | Jaywalking | infraction | 100 | 0 | A person who crosses a road not at a valid crossing, within 100 meters of a valid crossing, is guilty under this code section. |

### EF-PC-08-011 - Improper Firearm Storage and Handling

Source charges being condensed: PC-8020 Improper Storage of Firearm; PC-8021 Improper Handling of Firearm

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8020 | Improper Storage of Firearm | misdemeanor | 1500 | 5 | A person who stores, or is in possession of, a firearm in an unsecured container, such as a vehicle glovebox or unlocked vehicle trunk, is guilty under this code section. |
| Degree | PC-8021 | Improper Handling of Firearm | misdemeanor | 1500 | 5 | A licensed person who fails to report a lost or stolen firearm; lends a firearm to another licensed person outside the presence of the registered owner; or provides firearm access to an unlicensed person is guilty under this code section. |

### EF-PC-08-012 - Criminal Possession of Ammunition

Source charges being condensed: PC-8022 Criminal Possession of Ammunition

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-8022 | Criminal Possession of Ammunition | felony | 500 | 5 | A person who possesses ammunition without a firearms license, or who is otherwise legally prohibited from possessing ammunition due to their criminal history, is guilty under this code section. |

## 9. Offenses Involving the Operation of a Vehicle

Source charges: 26. Mapped entries: 26.

### EF-PC-09-001 - Driving While Intoxicated

Source charges being condensed: PC-9001 Driving While Intoxicated

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9001 | Driving While Intoxicated | misdemeanor | 100 | 5 | A person who operates a motor vehicle while under the influence of alcohol with a BAC over 0.08 is guilty under this code section. |

### EF-PC-09-002 - Evading

Source charges being condensed: PC-9002 Evading; PC-9003 Reckless Evading

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9002 | Evading | misdemeanor | 350 | 10 | A person who, while operating a vehicle on land, sea, or in air, or while operating a bicycle, willfully flees or otherwise attempts to elude or avoid a pursuing peace officer who communicates visually or audibly their request to pull over or stop is guilty under this code. |
| Degree | PC-9003 | Reckless Evading | felony | 1500 | 20 | A person who, while operating a vehicle on land, sea, or in air, or while operating a bicycle, willfully flees or otherwise attempts to elude or avoid a pursuing peace officer in a reckless or dangerous manner, defined as failure to maintain correct lanes of travel, excessive variability in rates of speed (ie. brake checking), or shows an imminent threat to the wellbeing of the general public, is guilty under this code section. |

### EF-PC-09-003 - Emergency and Traffic Control Compliance

Source charges being condensed: PC-9004 Failure to Yield to Emergency Vehicle; PC-9005 Failure to Obey Traffic Control Device

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9004 | Failure to Yield to Emergency Vehicle | infraction | 120 | 0 | A person who, while operating a motor vehicle, fails to yeild when signalled to by emergency services lights and sirens is guilty under this code section. |
| Degree | PC-9005 | Failure to Obey Traffic Control Device | infraction | 150 | 0 | A person who fails to obey a traffic control device, such as a stop sign, traffic lights, or yield sign is guilty under this code section. |

### EF-PC-09-004 - Vehicle Roadworthiness and Equipment

Source charges being condensed: PC-9006 Unroadworthy Vehicle; PC-9021 Driving without Headlights or Signals; PC-9024 Illegal Vehicle Modifications; PC-9026 Commercial Vehicle Violation

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9006 | Unroadworthy Vehicle | infraction | 450 | 0 | A person who operates a motor vehicle on a public roadway that is not permitted for legal road use is guilty under this code section. Vehicles such as dirtbikes, tracked vehicles, racecars, golf carts, fall under this section. Additionally, vehicles that are not equipped with indicators, brake lights, or have excessive damage are also guilty under this section. |
| Degree | PC-9021 | Driving without Headlights or Signals | infraction | 100 | 0 | A person who operates a motor vehicle in low light conditions or inclement weather conditions without their headlights switched on is guilty under this code section. |
| Degree | PC-9024 | Illegal Vehicle Modifications | infraction | 650 | 0 | Owners and drivers of vehicles on public streets with upgrades that are not legal for street use, are guilty under this code section. Upgrades that are not legal for street use, but are legal for off-road or track use include: Engines that are Tier 4 or 5, Transmission 3 or 4, NOS, and bulletproof tires. |
| Degree | PC-9026 | Commercial Vehicle Violation | infraction | 1000 | 0 | An owner or driver of a commercial vehicle who fails a San Andreas Department of Transportation inspection is in violation of this code section. |

### EF-PC-09-005 - Unsafe Vehicle Operation

Source charges being condensed: PC-9007 Negligent Driving; PC-9008 Reckless Driving; PC-9022 Motor Vehicle Contest; PC-9025 Public Disturbance by Motor Vehicle

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9007 | Negligent Driving | infraction | 500 | 0 | A person who, while operating a motor vehicle, displays behavior that endangers the safety of other drivers or pedestrians, due to negligence, is guilty under this code section. Negligent driving includes, but is not limited to, using a cellular device while driving on a public road or highway; and failing to move over or slow down for stationary emergency and service vehicles with warning lights flashing. |
| Degree | PC-9008 | Reckless Driving | misdemeanor | 725 | 10 | A person who, while operating a motor vehicle, displays behavior that endangers the safety of other drivers or pedestrians, due to recklessness, defined as failure to maintain correct lanes of travel, excessive variability in rates of speed (ie. brake checking), or shows an imminent threat to the wellbeing of the general public, is guilty under this code section. |
| Degree | PC-9022 | Motor Vehicle Contest | misdemeanor | 1000 | 10 | A person who attempts to or engages in racing or vehicular contest on public roadways is guilty under this code section. |
| Degree | PC-9025 | Public Disturbance by Motor Vehicle | infraction | 350 | 0 | Individuals who use a motor vehicle in a way that causes public disturbance are guilty under this code section. Examples of public disturbance include excessive burnouts, repeated revving of engine, loud music, and improper use of a horn. |

### EF-PC-09-006 - Speeding

Source charges being condensed: PC-9009 Speeding 1-10; PC-9010 Speeding 11-25; PC-9011 Speeding 26-39; PC-9012 Reckless Speeding (40+)

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9009 | Speeding 1-10 | infraction | 100 | 0 | A person who drives up to 10 mph over the posted speed limit is guilty under this code section. |
| Degree | PC-9010 | Speeding 11-25 | infraction | 500 | 0 | A person who drives greater than 11 mph but less than 25 mph over the posted speed limit is guilty under this code section. |
| Degree | PC-9011 | Speeding 26-39 | infraction | 700 | 0 | A person who drives greater than 26 mph but less than 39 mph over the posted speed limit is guilty under this code section. |
| Degree | PC-9012 | Reckless Speeding (40+) | misdemeanor | 1100 | 0 | A person who drives more than 40 mph over the posted speed limit is guilty of reckless speeding under this code section. This crime is a misdemeanor as defined, but does not inherently carry any jail penalty. |

### EF-PC-09-007 - Operator Licensing and Presentation

Source charges being condensed: PC-9013 Unlicensed Operation of Vehicle; PC-9014 Failing to Present a Driver's License; PC-9023 Piloting without Proper Licensing

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9013 | Unlicensed Operation of Vehicle | infraction | 350 | 0 | A person who operates a motor vehicle on a public roadway without the proper licenses for that vehicle class is guilty under this section. |
| Degree | PC-9014 | Failing to Present a Driver's License | infraction | 200 | 0 | A person who operates a motor vehicle on a public roadway who fails to display upon the request of an officer a valid driver's license is guilty under this section. |
| Degree | PC-9023 | Piloting without Proper Licensing | felony | 1500 | 20 | A person who operates an aircraft without the appropriate licenses is guilty under this code section. |

### EF-PC-09-008 - Traffic Movement and Parking Violations

Source charges being condensed: PC-9015 Illegal U-Turn; PC-9016 Illegal Passing; PC-9017 Failure to Maintain Lane; PC-9018 Illegal Turn; PC-9019 Unauthorized Parking

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9015 | Illegal U-Turn | infraction | 100 | 0 | A person who turns around on a roadway where the markings do not permit it is guilty under this code section. |
| Degree | PC-9016 | Illegal Passing | infraction | 100 | 0 | A person who passes traffic illegally, unsafely, or where the markings do not permit it is guilty under this code section. |
| Degree | PC-9017 | Failure to Maintain Lane | infraction | 100 | 0 | A person who crosses over lane markings where they do not permit passing, or when passing in an unsafe manner, is guilty under this code section. |
| Degree | PC-9018 | Illegal Turn | infraction | 100 | 0 | A person who makes a turn from the wrong lane, or where signs disallow it, is guilty under this code section. |
| Degree | PC-9019 | Unauthorized Parking | infraction | 100 | 0 | A person who parks their vehicle while blocking the roadway, on a red curb, on a pedestrian walkway, or in a marked no parking zone is guilty under this code section. |

### EF-PC-09-009 - Hit and Run

Source charges being condensed: PC-9020 Hit and Run

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-9020 | Hit and Run | misdemeanor | 500 | 10 | A person who is involved in a motor vehicle accident, and does not stop to exchange license or insurance information is guilty under this code section. |

## 10. Offenses Involving the Well-Being of Wildlife

Source charges: 13. Mapped entries: 13.

### EF-PC-10-001 - Hunting Violations

Source charges being condensed: PC-10001 Hunting in Restricted Areas; PC-10002 Unlicensed Hunting; PC-10004 Hunting with a Non-Hunting Weapon; PC-10005 Hunting outside of hunting hours; PC-10006 Overhunting; PC-10007 Animal Poaching

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-10001 | Hunting in Restricted Areas | infraction | 450 | 0 | A person who hunts for game outside of allocated hunting areas is guilty under this code section. |
| Degree | PC-10002 | Unlicensed Hunting | infraction | 450 | 0 | A person who hunts for game without the appropriate license is guilty under this code section. |
| Degree | PC-10004 | Hunting with a Non-Hunting Weapon | misdemeanor | 450 | 10 | A person who hunts game with a weapon that is not a legal licensed hunting weapon is guilty under this code section. Legal licensed hunting weapons are defined as weapons that are sold direct-to-consumer by official hunting stores, with weapons being automatically registered to the individual who purchases the weapon. |
| Degree | PC-10005 | Hunting outside of hunting hours | infraction | 450 | 0 | A person who hunts game outside of the legal hours for hunting in that area is guilty under this code section. Legal hunting hours are from dawn to dusk in all legal hunting zones. |
| Degree | PC-10006 | Overhunting | misdemeanor | 110 | 10 | A person who hunts over the amount allowed in a given hunting area is guilty under this code section. The current amount legally allowed by a single individual is defined as 200 kg of combined animal meat and skins, fur, tusks, or other animal by-products. |
| Degree | PC-10007 | Animal Poaching | felony | 1250 | 20 | A person who hunts for an endangered or protected species in the state of San Andreas is guilty under this code section. Current endangered and protected species include the following: Mountain Lions, Bears, Seagulls, and Capybara. |

### EF-PC-10-002 - Animal Cruelty

Source charges being condensed: PC-10003 Animal Cruelty

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-10003 | Animal Cruelty | misdemeanor | 450 | 10 | A person who causes harm to an animal with malicious intent, with no cause for self defence, is guilty under this code section. |

### EF-PC-10-003 - Fishing Violations

Source charges being condensed: PC-10008 Fishing in an Unauthorized Zone; PC-10009 Illegal Fishing; PC-10010 Overfishing

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-10008 | Fishing in an Unauthorized Zone | misdemeanor | 3275 | 5 | Unless otherwise specified, fishing for sport and game may be conducted on public waterways in the State of Los Santos. The following areas are prohibited fishing grounds: Zancudo River, Lago Zancudo Wetlands, Land Act Reservoir, and the Port of Los Santos |
| Degree | PC-10009 | Illegal Fishing | misdemeanor | 6250 | 15 | Illegal fishing is defined as fishing using illegal hooks or possessing, transporting, or selling fish of prohibited lengths or species. Species that are prohibited from possession include: whales, sharks, arapaima, giant snakehead, goliath tigerfish, devil rays, kraken, megalodon, giant coelacanth, and golden fish. These fish, however, may be caught for sport and then immediately released. The minimum and maximum lengths for fish that may be caught, transported and sold are as follows (in inches): Salmon \|30 - 40\|, Trout \|20 - 30\|, Bass \|20 - 30\|, Catfish \|18 - 30\|, Perch \|5 - 10\|, Pike \|22 -38 in\|, Carp \|15 - 30\|, Bluegill \|7 - 14 in\|, Cod \|30 - 45\|, Herring \|7 - 13\|, Walleye \|26 - 38\|, Bream \|12 - 22\|, Zander \|22 - 38\|, Sturgeon \|100 - 130\|, Swordfish \|65 - 95\|, Tuna \|50 - 75\|, Muskellunge \|32 - 48\|, Tarpon \|75 - 110\|, Giant Catfish \|85 - 115\|. Individuals found to be illegally possessing, transporting, or selling these species are subject to confiscation of the fish and subject to the penalties outlined herein.  |
| Degree | PC-10010 | Overfishing | infraction | 600 | 0 | Daily catch limit is 30 fish per person per day. Violations of the catch limit are punishable by up to $600 per fish above the allotted amount. All fishing vessels and subjects who are engaged in fishing are subject to random inspections by Fish & Wildlife Officers for the stated purpose of monitoring fishing equipment, fish length, and all other duties. |

### EF-PC-10-004 - Police Working Dog Murder

Source charges being condensed: PC-10012 Murder of a Police Working Dog; PC-10011 Attempted Murder of a Police Working Dog; PC-10013 Accessory to the Murder of a Police Working Dog

| Role | Source Code | Source Title | Classification | Base Fine | Base Time | Source Description |
|---|---|---|---|---:|---:|---|
| Degree | PC-10012 | Murder of a Police Working Dog | felony | 4000 | 45 | A person who commits the intentional killing of a police working dog, while in the execution of their duties, in a way that is willful, deliberate and premeditated is guilty under this code section. |
| Liability Option | PC-10011 | Attempted Murder of a Police Working Dog | felony | 3000 | 30 | A person who attempts to unlawfully kill or cause great bodily harm to a police working dog, while in the execution of their duties, is guilty under this code section. |
| Liability Option | PC-10013 | Accessory to the Murder of a Police Working Dog | felony | 1750 | 20 | A person who assists another person who attempts to unlawfully kill or cause great bodily harm to a police working dog, while in the execution of their duties, is guilty under this code section. |

Notes: Attempt/accessory variants become liability options.

## Coverage Check

- Source charge count: 189
- Mapped source entries: 189
- Duplicate source mappings: 0
- Missing source mappings: 0
- JSON restructuring performed in this pass: no

