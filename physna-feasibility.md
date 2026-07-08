# Physna Feasibility Note

Technical note on Physna, geometric search, and why 3D-printer firearm-blocking technology is unlikely to work as broadly as supporters suggest.

This is not a claim that Physna's core geometric-search technology is fake. The narrower claim is that **3D geometric search may be useful for enterprise search, triage, or flagging known models, but that is different from a legally mandated, reliable, low-false-positive, hard-to-bypass firearm blocker for all consumer 3D printers.**

Last updated: 2026-07-08.

## What Physna Is Claiming Publicly

Physna describes its core business as geometric search and "physical AI" for 3D models. Public materials describe the technology as codifying 3D models into software-readable data, comparing geometric relationships, and finding exact, similar, alternative, or partial matches.

In coverage of New York's printer-blocking law, AP quoted a Physna technical account manager saying: "Geometric search is mature, it's deployed, it is ready to be applied to this problem."

Physna's own LinkedIn post about New York's law says the company was featured in the AP/PBS discussion and says the technology needed to enforce this regulation is "actually already available." A related post by Physna CEO Paul Powers says modern physical AI can distinguish firearm components from ordinary industrial parts with very high precision, and that Physna testing showed ordinary industrial parts were not incorrectly identified as prohibited firearm components.

Those are strong claims. They deserve equally strong proof.

## What The Technology Might Be Good At

A geometry-search system can plausibly help with:

- finding exact or near-exact copies of known 3D models;
- identifying similar shapes inside a controlled enterprise CAD database;
- comparing part revisions;
- flagging uploaded files for human review;
- finding duplicate or substitute parts;
- triaging known firearm files in a cloud platform, school lab, or managed enterprise print fleet.

That is useful. It is also much narrower than "3D printers can reliably refuse gun parts."

## The Core Problem

The policy goal is not simply "find known files in a database." The policy goal is closer to:

> Before a printer runs, correctly decide whether an arbitrary model, from any source, in any supported file format, possibly modified, segmented, transformed, renamed, remixed, embedded, or combined with unrelated geometry, is a prohibited firearm or firearm component.

That is an open-world adversarial classification problem. It is not the same thing as enterprise similarity search.

## Why It Will Not Work As Stated

### 1. Geometry Is Not Legal Intent

A shape does not carry legal intent. A tube, grip-like contour, bracket, hook, spring guide, jig, mold, toy part, prop, or repair part can resemble a firearm-related geometry without being a firearm component.

The legal category may depend on context:

- intended use;
- material;
- scale;
- assembly with other parts;
- post-processing;
- whether the object is functional;
- whether it is a prop, toy, fixture, repair part, or actual component.

Geometry alone cannot reliably resolve those facts.

### 2. Known-Geometry Matching Is Not The Same As Novel-Design Detection

If the system compares a submitted model to a database of known firearm and conversion-kit geometries, it can only be strongest against known or near-known designs.

It gets harder when a design is:

- novel;
- parametric;
- remixed;
- split into subparts;
- combined with unrelated geometry;
- scaled or modified;
- altered to avoid similarity thresholds;
- represented differently across file formats.

Physna may be better than simple file hashing, but geometric similarity still requires thresholds. Thresholds always create a tradeoff: too strict and modified weapons pass; too broad and lawful objects get blocked.

### 3. False Positives Are Built Into The Tradeoff

AP reported concerns that harmless pipes or an S-shaped wall hanger could be flagged as firearm-adjacent. EFF similarly argues that broad shape scanning risks blocking lawful repair parts, hobby parts, and ordinary mechanical designs.

This is not a side issue. For a mandatory printer gatekeeper, false positives are product failures:

- a school lab cannot print a lawful engineering part;
- a repair shop cannot print a replacement bracket;
- a maker cannot print an unrelated object;
- a user has no meaningful appeal path if the algorithm is embedded in firmware.

The more aggressively the system tries to stop modified designs, the more lawful objects it is likely to block.

### 4. False Negatives Are Also Built Into The Tradeoff

The opposite problem is also unavoidable. If the system avoids false positives by only blocking close matches to a known prohibited database, users who actually intend to break the law can modify, split, or route around the detection system.

The Engineering.com article on 3D-printed firearms quotes a 3DPrinterOS executive working with Physna as saying that if someone runs a 3D printer completely offline, it becomes very difficult to control what they print, and that no solution will be 100 percent effective.

That is the practical center of gravity: the tech may add friction in managed environments, but it cannot be relied on as a universal blocker.

### 5. Consumer Printers Are Not Managed Enterprise Platforms

Physna-style search makes more sense in a cloud or enterprise environment where files pass through a managed service before printing.

Consumer printers are different:

- many run offline;
- many accept files from local storage;
- many support open-source slicers or firmware;
- many can be modified, repaired, or rebuilt;
- many are kits or partially user-built machines;
- older printers will remain in circulation.

To make blocking mandatory on consumer hardware, lawmakers would need to push printers toward locked firmware, approved software stacks, remote checks, or state-approved model lists. That is exactly where the right-to-repair and open-source problems begin.

### 6. On-Device Analysis Has Cost And Performance Limits

Running meaningful geometric analysis locally on low-cost printer hardware is not the same as running a cloud search against an indexed enterprise database.

If the analysis is local, manufacturers have to add compute, storage, update mechanisms, and model maintenance to inexpensive machines. If the analysis is cloud-based, then private designs may be uploaded or checked against third-party systems, adding privacy, reliability, latency, and security risks.

Either path changes what a 3D printer is: from a tool controlled by the owner into a tool that requires permission from a software gatekeeper.

### 7. Adversarial 3D Classification Is A Known Research Problem

The broader 3D machine-learning literature recognizes adversarial attacks against 3D point-cloud and shape classifiers. Researchers have shown that 3D models can be intentionally perturbed to cause misclassification.

That does not prove a specific Physna model fails. It does show that "AI can classify 3D shape" is not enough. A mandatory firearm blocker has to be robust against people who are actively trying to evade it, not just random users uploading ordinary files.

### 8. The Currency-Printer Analogy Breaks Down

Supporters compare firearm blocking to anti-counterfeiting detection in paper printers. The analogy is weak.

Currency detection looks for known anti-counterfeiting patterns in a narrow set of standardized objects that are intentionally designed to be detectable. Firearm components are not standardized in that way. They are a broad and evolving family of shapes, many of which overlap with ordinary mechanical forms.

A dollar bill is meant to be recognized. A prohibited 3D model can be intentionally changed.

### 9. "Very High Precision" Needs Public Benchmarking

Physna says ordinary industrial parts were not incorrectly identified in its testing. That is not enough for public law.

A credible claim would need independent, public, reproducible testing across:

- large lawful-model corpora;
- repair parts;
- cosplay and prop models;
- toys and hobby models;
- functional mechanical parts;
- known firearm components;
- novel firearm-like designs;
- transformed and remixed files;
- segmented designs;
- adversarial examples;
- multiple file formats and slicer outputs;
- offline and low-cost printer conditions.

The key metrics are not just accuracy. They are false positive rate, false negative rate, adversarial robustness, latency, privacy impact, appeal process, update control, and auditability.

## Better Framing

Physna-style technology may be useful as:

- a voluntary moderation tool for model-hosting platforms;
- a school or enterprise policy tool where users agree to managed printing;
- a forensic or investigative search tool;
- a triage tool for human review;
- a way to search known prohibited models across large repositories.

It is not proven as:

- a universal consumer-printer safety interlock;
- a reliable legal classifier;
- a low-risk firmware mandate;
- a tool that cannot be easily circumvented;
- a system that avoids chilling lawful repair, research, open-source, or hobby use.

## What To Ask Physna Or Lawmakers

Before any state relies on this technology, ask:

1. What exact models were tested?
2. How many lawful industrial, repair, toy, prop, and hobby models were in the test set?
3. What was the false positive rate?
4. What was the false negative rate?
5. Were adversarially modified models tested?
6. Were split or partial components tested?
7. Were open-source slicers and offline printers tested?
8. Does the system run locally or in the cloud?
9. What data leaves the user's machine?
10. Who controls the prohibited-geometry database?
11. Can users appeal a blocked print?
12. Can independent researchers audit the model?
13. Does lawful repair or firmware replacement trigger liability?
14. What happens when a printer company goes out of business or stops updating the blocker?
15. Can the blacklist expand to non-firearm designs, including copyrighted objects, patented parts, or politically sensitive items?

## Working Conclusion

Physna's geometric search may be real and useful. But the legal mandate being built around this category of technology overpromises.

The most accurate conclusion is:

> Geometry search can flag some known or similar files in controlled environments. It cannot, by itself, reliably determine legal intent or stop all firearm-related printing across open consumer hardware without creating false positives, false negatives, privacy risks, repair restrictions, and incentives for locked printer ecosystems.

That makes it a poor foundation for broad printer-level mandates unless the law includes independent testing, narrow definitions, repair carve-outs, offline protections, auditability, user appeals, and strict limits on database expansion.

## Sources

- AP, New law seeks to block 3D printers from making guns: https://apnews.com/article/3d-printers-firearms-ghost-guns-737b48cd483da5394076bc99d94619ca
- The Verge, Are you ready for what it takes to stop ghost guns?: https://www.theverge.com/tech/960802/3d-printed-gun-laws-ghost-guns
- Physna LinkedIn post, New York Blocks 3D Printed Guns with AI Tech: https://www.linkedin.com/posts/physna_first-of-its-kind-law-in-new-york-could-block-activity-7472294387985788928-JrwF
- Paul Powers LinkedIn post, Narrowly Targeted Safety Feature for 3D Printers: https://www.linkedin.com/posts/techlab_this-isnt-about-banning-3d-printing-its-activity-7478087549693980672-H7tZ
- CIMdata, Physna Promotes 3D Model Search and Discovery: https://cdn2.hubspot.net/hubfs/5241855/CIMdata_Whitepaper_Physna.pdf
- Engineering.com, What can we do about 3D printed guns?: https://www.engineering.com/what-can-we-do-about-3d-printed-guns/
- EFF, Print Blocking is Anti-Consumer: https://www.eff.org/deeplinks/2026/04/print-blocking-anti-consumer-permission-print-part-1
- EFF, Print Blocking Won't Work: https://www.eff.org/deeplinks/2026/04/print-blocking-wont-work-permission-print-part-2
- Tangelder and Veltkamp, A survey of content based 3D shape retrieval methods: https://webspace.science.uu.nl/~veltk101/publications/art/mtap08.pdf
- Su et al., A Deeper Look at 3D Shape Classifiers: https://jongchyisu.github.io/papers/shape_recog/shape_recog.pdf
- Xiang et al., Adversarial Attacks and Defenses on 3D Point Cloud Classification: https://arxiv.org/html/2307.00309v2
- Williams et al., Data Management Challenges for Internet-scale 3D Search Engines: https://arxiv.org/abs/2209.03913

