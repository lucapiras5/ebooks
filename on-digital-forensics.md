# On digital forensics

## Introduction

<!-- executive summary -->

This document is a summary, a translation and a re-examination of my master's thesis.

It's a summary, because it's much shorter: the original document consists of more than a hundred pages, and has tens of thousands of words.

It's a translation, because the original was written in Italian, since I graduated at the University of Bologna.

It's a re-examination, because after writing my thesis I've had the chance to see how my predictions and recommendations hold up in practice.

## Digital forensics

**Digital forensics** is the forensic science that deals with digital devices and digital data.

This definition is kept **as generic as possible** on purpose, given the immensely pervasive and deeply entrenched reliance on digital devices and digital data for nearly any human endeavor, and the **particular characteristics of digital data**.

The catalyst for the development of digital forensics were **harmful actions that could be (only) committed by means of a computer, or against another one**. In many cases it was impossible to apply existing criminal statutes by interpreting them broadly. There were attempts to do so, but they bordered on unconstitutionality by being too arbitrary.

For example, could using a computer system and then charging the cost on someone else be considered larceny? In *Lund v. Commonwealth*, the courts found that a computer's services could not be considered personal property, a necessary element for larceny. Or should be unauthorized access to a computer system be considered trespass? Could a computer virus that damages data fall under the definition of damage to property?

As per the *vagueness doctrine*[vagueness-doctrine] criminal law can't afford to be vague or imprecise, so lawmakers enacted **criminal statutes punishing these novel computer crimes** [nugent1991]. These statues are of interest to digital forensics because they provide the foundation of the entire subject.

[nugent1991]: See H. Nugent, *State Computer Crime Statutes* (1991). <https://www.ojp.gov/pdffiles1/Digitization/128780NCJRS.pdf>.
[vagueness-doctrine]: See Constitution Annotated, *Amdt5.8.1 Overview of Void for Vagueness Doctrine*. <https://constitution.congress.gov/browse/essay/amdt5-8-1/ALDE_00013739/>.

The only way to prove these computer crimes is to **gather evidence from the systems that were used to commit the crime and the affected systems**, but this evidence is digital in nature. Again, the matters of gathering, handling and making sense of this kind of evidence were uncharted waters, and so the field of "computer forensics" was born.

Later technological innovations such as the ubiquity of computer networks, the introduction of mobile telephones, new software technologies like cloud storage or computing and Bitcoin created new sub-fields, such as network forensics, mobile forensics, cloud forensics, blockchain forensics, and so on. *Digital forensics* is the umbrella term that encompasses all these fields.

Throughout its history, digital forensics has been concerned with the study of these technologies, much like how biology is concerned with the study of all living things. Biology studies the components of living things, what substances they produce during their lifecycle, how external substances affect them.

Likewise, digital forensics studies how digital systems are structured, what traces of their functioning they produce, how users or software can affect the system's functioning or the traces it produced.

For a **practical example** of the kind of domain-specific knowledge that digital forensics can provide, let's assume that one wants to prove that someone visited an internet website, and that the suspect's device has already been seized by the police, and it is turned off.

The **most intuitive** way to do it would be to turn on the suspect's device, open the browser, and search for traces of that website. However, this is also the **most harmful**, since it's akin to a coroner handling a corpse without wearing gloves and using dirty tools. Booting a computer and opening programs is extremely invasive, and alters the evidence.

After a computer is booted and during its operation, there are many services running in the background, manipulating files, and possibly changing or overwriting useful traces. The safe approach to handling evidence is much more involved, and requires using specialized software to create multiple copies of the device's internal drive called *forensic images*, calculating their *cryptographic hash digest* so that their integrity can be verified, using specialized software to process the images and extract the browsing history, and where feasible, using multiple approaches to make sure that they all come to the same conclusions.

This is just a **high-level overview**. In practice, one needs to be aware of possible side-effects, trade-offs and caveats of the approach they're taking, both in order to use the least invasive techniques on the original evidence, and to be able to defend their approach if it's called into question, or provide a honest assessment of how reliable the conclusions are.

Therefore, the purpose of digital forensics as a science is to research the lifecycle of digital data and digital systems, bearing in mind that the purpose of this research is not to accumulate knowledge for knowledge's sake (which would be the purpose of a pure science), but to use this knowledge to solve legal problems (this is what the adjective "forensics" is about).

As such, **procedural law** is of extreme interest for digital forensics. Much like how substantive law had to be amended in order to create new crimes that didn't exist before, procedural law should also contain **provisions for handling digital evidence**, and digital forensics is the subject that can define the **fundamental guiding principles** that should be mentioned in these provisions.

While digital forensics was originally developed to deal with computer crimes, it can still be **used in the context of "traditional" crimes**, when they're committed by means of a computer (e.g., wire fraud or libel on social media), or even when computers are involved only insofar they contain evidence that a crime has been committed, or even just leads (e.g., a sale of illicit goods that was conducted in person, but the parties talked organized the sale online prior to meeting).

## Challenges in digital forensics

The previous section introduced the purpose and usefulness of digital forensics. This paragraph outlines the most pressing challenges in the subject, and how to deal with them.

The first issue is the **exponential rate of growth in technological evolution**. Hardware and software is continuously evolving. It's challenging enough to learn about new technologies, let alone publish and peer-review scientific studies on how to analyze them.

This is compounded by the fact that **scientific research in how digital systems work is often hampered by various hurdles**. They may be **economic** (the high cost of acquiring these systems in the first place), **technical** (these systems may have anti-tampering measures in place that make it challenging to inspect their functioning), due to a **lack of documentation** (documentation may be completely absent, or limited to only a high-level overview), or due to **legal limitations** (licenses, NDAs and trade secrets can prevent researchers from learning more about these systems, or publishing their findings).

Furthermore, **digital data is fragile**. The essence of digital data is that it's just a long list of discrete values, in other words, a **sequence of digits**, which are **stored on a physical medium**, such as hard disks.

Physical media is subject to **deterioration**, which means that data stored within them can become unreadable, or subject to **random bit flips**, where the value of a single bit changes. If someone has physical access to the storage medium, they can also **tamper with its contents**, by wholly erasing it, or carefully changing certain elements, such as the timestamp on a file, or deleting all traces of a file.

Users to know how to **interpret binary data** in order to make sense of it. These rules that convert human-readable information into binary data are called "**encodings**", and the process of turning binary data back into human-readable information is called **decoding**.

Using the **incorrect decoding rules**, or **the correct decoding rules on data that's been damaged** (either through natural deterioration or willful intervention) will result in data that's completely **meaningless** at best, or **inaccurate** in subtle, hard-to-detect ways in the worst case.

Even if this tampering can be detected, it's **usually impossible to reconstruct the original data** was, since the data stored on a device can be **changed without leaving traces**. At best, one can only provide various explanations of what may have happened.

## The silver lining of digital data

The challenges outlined in the previous sections paint the subject in a rather **unflattering light**. Digital data is generally useful as circumstantial evidence, and in the case of computer crimes it's the only kind of direct evidence that's available, and yet, it's volatile and hard to make sense of. However, that doesn't mean that the digital forensics is an exercise in futility, a doomed attempt at trying to create order out of chaos.

For all of digital data's faults, there is one silver lining, the fact that digital data can be **copied an infinite amount of times**, that **each copy is indistinguishable from the original**, and that it's **easy to demonstrate the integrity of copies**.

Conventional (non-digital) evidence can't be copied, since it's impossible to perfectly reproduce the material arrangement of an object, down to the atomic level. Even with things like photocopies, it's always possible to distinguish between the original and its copy.

At best one may create many **representations** of that evidence, such as taking pictures of the crime scene, but the pictures are not a substitute for the actual crime scene. Besides, once non-digital evidence decays due to natural causes, or it's irreversibly damaged due to the use of an invasive analysis technique, it's **impossible to return to a prior state**. 

On the other hand, **digital evidence can be easily copied**. It essentially consists of a sequence of digits, so as long as those digits are reproduced in an identical fashion, one has obtained an **exact copy of the original**, and **the original and the copy are perfectly interchangeable**.

Digital evidence too is susceptible to decay or damages, and as such it's always advisable to create multiple copies, as to always preserve a **backup of the original**.

It's possible to create a **representation of digital evidence** as well, by printing an email message for example. However, the printed representation (a sheet of paper) is **not interchangeable** with the original email (digital data), it can't be analyzed or copied in the same way, they're entirely different things.

This point can't be stressed enough. Digital evidence **must remain preserved in its digital form**, and may be **degraded into a representation** for **illustrative purposes only**. Representations of digital evidence are never a substitute for the original, and if **evidence is to be re-examined** for any reason, then one should look at the **digital evidence, not its representation**.

Finally, it's possible to **determine whether a copy is still intact** or not, by using **cryptographic hash functions**. A *hash function* takes an arbitrary amount of digital data as input, and returns a **fixed-length** amount of digital data as output, called the *digest*, with the guarantee that identical inputs will always produce identical digests. This characteristic is called **determinism**. A common analogy is to think of a digest as the **fingerprint of a piece of data**.

The adjective *cryptographic* refers to certain security guarantees about the function.

The first is the **avalanche effect**, whereby flipping a single bit in the input flips half of the bits in the digest, meaning that even the **smallest possible alteration** in the input will result in a **very noticeable difference** in the digest, which can be caught at a glance.

The second is **collision resistance**, whereby two different inputs should not produce the same output. Since the digest has a fixed length, but the input data can have an arbitrary length, by the *pigeonhole principle* it's certain that different inputs may map to the same digest. The design of cryptographic hash functions tries to minimize the likelihood of this happening in a predictable fashion.

The last one is **second preimage resistance**, whereby if one knows the input data, and its digest, it's unfeasible to find a different input that produces the same output.

The first characteristic is useful to find **accidental bit-flips** in the data, usually caused by natural decay or errors while copying the data. The latter two are useful to catch **intentional tampering** of the data.

The digest should be calculated **after copying the data for the first time**, and then **whenever a copy of the data is used**, to ensure that it's **still identical** to the original.

Cryptographic hash functions are the **cornerstone** of digital forensics, because they represent one element of **stability**, they demonstrate that despite all the other issues, digital data can be **reliably duplicated and preserved over time**, which can't be said for conventional evidence.

## Scientific rigor in digital forensics

The fact that digital data can be duplicated and preserved reliably is significant, because it makes it the perfect candidate for study by the **scientific method**. In fact, its other shortcomings necessitate the use of the **most rigorous** method of study that is available, in order to produce a body of the **most reliable** knowledge possible.

Computers are **programmable**, meaning that they can be instructed to follow a **specific procedure on a specific starting condition**, which consists of the digital data or system that is being studied. This means that they can be used to mechanically **perform experiments, verify the results, and produce a report**.

The data and software that comprise the experiment then be **shared**, so that other researchers can **re-run the experiment** for themselves, and **attempt to falsify** the results.

If the **results hold true**, then it means that the **theory is valid**. If the **experiment fails**, then it means that **adjustments have to be made**.

For example, let's suppose that a researcher is trying to learn how an undocumented file format is structured. They can manipulate parts of the file, and see what effects these manipulations have. Through a process of trial and error, they begin to document the various parts of the file, and then they write a program that can read this file type, and extract  information out of it.

The documentation and the software is shared with other scientists, who then proceed to run the program on their own samples of this file type. If the program produces reasonable outputs, it can be believed that it's working correctly. If it fails to analyze the data, this means that the file type is more complex than what was believed. The cycle of the scientific method begins anew, and ideally it'll end when a new version of the software, capable of analyzing the file that the previous version couldn't, is released, along with the revised documentation of the format.

The importance of **freely and openly sharing the results of scientific research** cannot be stressed enough. The free flow of information allows science to thrive and benefits everyone, since everyone can join in on the **falsification process**, and stimulate the improvement of better, more accurate knowledge.

On the opposite end of openness and transparency is **proprietary research**, which is **kept secret** from the public. This results in an immediate **loss of rigor and efficiency**, since there is no public oversight to falsify the theories and test the tools that have been produced. Furthermore, it exclusively benefits the private entities that use it to develop and sell products and services at (often) **high price points**, given the small (or non-existent) pool of competitors.

## Digital forensics in legal proceedings

The purpose of digital forensics is to **support anyone who has to interact with digital evidence in any capacity in the context of legal proceedings** with the **necessary domain-specific knowledge** to carry out their duties to the best of their abilities.

This includes **law enforcement officers** (as they seize devices, or acquire digital evidence by other means, such as wiretapping), **evidence custodians** (as they're in charge of safely storing devices containing digital data), **prosecutors** (as they investigate a case), the defendant or the parties' **legal counsel** (as they define their legal strategy), **expert witnesses** (as they will analyze the digital data, and will be called upon to explain their findings before the judge), and the **judge** (as they evaluate the evidence that has been presented in preparation for their decision).

That **list should not be taken as exhaustive**, since it only mentions the figures involved in civil and criminal proceedings. Different jurisdictions and legal systems may have different procedures, but the underlying principle is always the same. Digital evidence has special requirements, and the rules and guidelines for its special treatment are prescribed by digital forensics.

Judges in particular have a very delicate role. Given that digital forensics is a science, this means that **digital evidence can be considered a form of scientific evidence**. There are two standards regarding the admissibility of scientific evidence, which are *Frye* (where scientific methodologies must be **generally accepted by the scientific community**) and *Daubert* (where general acceptance is one of several factors, and judges must also evaluate the **underlying scientific principles**).

Under the more lenient **Frye standard** there are no issues with tools for the analysis of digital evidence developed as a consequence of proprietary research, as long as they're widely used by professionals. The soundness of its foundation, the **scientific research it was built upon is never put into question**.

The **Daubert standard** is more thorough, since in addition to general acceptance judges also have to evaluate whether the theory is **falsifiable** (and whether it has been), whether it has been **published and subjected to peer review**, its known or potential **error rate**, the **existence and maintenance of standards** that control its operation.

**Tools for the analysis of digital evidence developed in accordance with free and open scientific research** are more in line with the **Daubert standard**, since they can address all of these questions. The fact that the claims they make can be scrutinized even in the context of a legal proceeding makes them **inherently more trustworthy**.

More generally, the **legal system favors openness** in trials. Judges must provide an explanation for their decisions, because their decisions would be arbitrary otherwise. Trials are open to the public, because secret trials aren't trustworthy. Criminal trials can involve a jury, because it ensures that the decision taken by a single authority figure also takes into account the opinion of the public. Defendants have the right to know the charges and the evidence being brought against them, or else they wouldn't know be able to mount a thorough defense.

In this context using proprietary research and tools, which are characterized by their secretiveness and inscrutability feels like a step backwards. If open, peer-reviewed alternatives are available, they should be favored instead. Having **many elements to evaluate in the context of scientific evidence** is a good problem to have, because it means that the final decision is rooted in a **logical and thorough assessment** of the evidence and the scientific theories underpinning it, rather than a deferential faith in a method whose only claim to fame is its generally acceptance by the scientific community.

---

<!--
- 1978 Florida Computer Crimes Act, potential for harm
- lifecycle of digital evidence
-->

## Software for handling digital evidence

The previous section established the importance of free and open scientific research, and how it's beneficial to legal proceedings, especially under the Daubert standard. It also hinted at tools to handle digital evidence with being developed on top of scientific research.

These tools that **handle digital evidence** are **pieces of specialized software**. Their **specialization lies in how they function**, rather than any particular qualifications of their developers.

One can identify several steps in the handling of digital evidence. The most crucial one is **acquisition**, where the software acquires the first forensic image of the original data. At minimum, the software must ensure that the **forensic image is identical to the original data**, that **it's not altering the original data**, that it **it creates a log file** containing identifying information about the operation (such as a timestamp for the beginning and end of the operation, an identifier for the piece of evidence, the examiner(s), the version of the software, the settings being used, any warnings and diagnostic messages, the forensic image's **cryptographic hash digest**, and so on).

It's important that the software can **capture as much data as possible**, and **report any issues** during the acquisition phase, no matter how insignificant they may be. Depending on how volatile the data being acquired is (the contents of RAM and network connections are the most volatile types of data), it may be impossible or risky to retry acquiring it. Having partial data is better than having no data, but a **detailed explanation** of what data has been acquired is necessary.

The final element of acquisition is **digitally signing the log file with a timestamp**. The goal is to prove the **existence and contents** of the document that details of the operation, ideally **as soon as the acquisition ends**. The timestamp should be provided and recorded by a **time-stamping authority**.

The **storage** step starts after data has been acquired, and lasts until data doesn't have to be retained anymore because it's no longer relevant to any proceeding. Software used in this step should be able to **verify the data integrity** by calculating its cryptographic hash and **encrypt** the data to ensure that it remains confidential. Software can also be used to maintain a **digital chain of custody**, with handwritten signatures being replaced by **digital signatures** (which can't be forged, and have stronger non-repudiation guarantees).

The **analysis** step is chiefly **technical**, and involves **finding elements of interest** in the digital data that has been acquired. This is the step where **scientific research is actualized into software**, and so the developers should take care to implement the published, ideally peer-reviewed scientific findings as closely as possible, to make sure that software can **handle invalid data gracefully**, and that it's **easily extensible**, so that other developers can build on top of it instead of having to start from scratch.

## Software licenses and free software

The software used in the previous section has a direct bearing on the results that will be presented in court. Just like how **scientific research should be published and peer-review, so should the software** that implements it in practice.

From a legal viewpoint, **software is protected by copyright law** as a literary work. This means that **unless stated otherwise, all rights are reserved by the author**. Software is usually distributed with a **license** that regulates what rights are granted to the users of the software.

Software developed on the basis of **proprietary research** is often distributed with **restrictive licenses**, that place restrictions on **how the program is executed** (usually a hardware dongle is required, but there may be also limitations on how many users can use the program simultaneously in an organization, licenses may expire after a period, some functionalities could be disabled in cheaper licenses), on **being able to study how the program works** (proprietary research is valuable only as long as it's secret, so there's both legal and technical measures in place to prevent reverse-engineering efforts), on **modifications** (if it's not possible to understand how the program works then it's not possible to modify it either, and there's measures to verify whether the software has been tampered with), and so on.

The opposite of proprietary licenses are **free software licenses**, as defined by the *Free Software Foundation*, which are designed to **grant freedoms** to end users.

It should be noted that the adjective **"free" refers to freedom, not price**. While it is true that free software is usually distributed free of charge, it can also be sold. For that reason, the expressions "**free and open source software**" or "**libre software**" are often used to clear any ambiguity.

The first freedom is to **run software for any purpose**. If someone has a copy of the software, they can simply use it. They do not have to obtain the authorization to do so from the developers or a reseller in the form of a hardware dongles, or other measures to that effect. There can't be any artificial limitations of how the user can run the software, or what they can do with it.

The second freedom is to **study how the software works and modify its source code**. Proprietary software usually doesn't distribute its source code, because it contains a human-readable description of the algorithms it uses (which are trade secrets), and this would be tantamount to distributing the proprietary research that it's based on. Free licenses instead encourage users to gain an understanding of the source code so that they can **understand what the software is doing**, and also so that they can **extend it** to suit their needs, and **improve it** to fix bugs.

It should be noted that if source code is released, but the license forbids modifying it, redistributing it, or any other use, then the program is said to be **proprietary, but source-available**. The only advantage over ordinary proprietary software is that one can inspect how the program functions, but they can't participate in its improvement.

The third and fourth freedoms are to **redistribute copies of the software**, and to **redistribute modified copies** respectively. This effectively means that software released under free licenses grants everyone the **right to create copies and derivative works** of the original software.

The **free software model** is particularly fitting for the software developed during **scientific research** in the field of digital forensics. It enables everyone to download the software, test it, study it, and make and share improvements. Just like how **scientific research and legal proceedings are open rather than secretive**, so should be the **software that acts as a link between the two**.

Free software licenses can be grouped in two groups. **Permissive licenses** place minimal restrictions on code reuse, and **proprietary software** can **freely use, modify and redistribute** code released under these licenses. The main requirement is simply to **preserve the copyright notice**, so that the usage of the software and the authors who worked on it can be acknowledged.

On the other hand, **copyleft licenses** allow the use, modification and redistribution of code on the condition that **the resulting new code adopts the same license**. In other words, any changes to copylefted code must be released under the same copyleft license.

This **automatic self-propagation** of the license ensures and enforces that **source code remains always available**, so that it can be **studied** to know how it works, but also **modified** to improve it, or to **ensure it remains up-to-date** with new scientific research, and with new versions of other software and operating systems.

## Downsides of proprietary software

**Proprietary software** is usually **developed for profit** by organizations or individuals. Funding is mainly obtained by **selling the right to use the software** to consumers, though consulting and formation may also play a significant role.

It is developed in an **autocratic manner**. There may be public roadmaps and customers may submit feature requests, but the developers don't have to honor them if they feel that it would be **unprofitable, or not profitable enough** to do so.

The main focus is on **form and marketability**, rather than **function and user experience**. The perception of the software as "authoritative" is more important than how efficiently or accurately it actually functions. Developers have an incentive to **not mention or downplay any defects** the software may have, and at any rate, the **users can't tell how it functions** anyway, since the **source code is not available** for inspection.

It's quite likely that products and new features are implemented as quickly as possible, because time spent on developing them is expensive. As a result, the code base will likely accumulate **technical debt**, making it harder to maintain and increasing the amount of bugs, and **features aren't tested in depth**.

The **high cost** of licenses and the fact that software isn't freely redistributable also means that it's hard to have a **wide, distributed public oversight** on its correct functioning.

An argument can be made that **it is possible to test the correct functioning of proprietary software** by creating a hand-crafted dataset with known features, and then checking if the software detects them and produces the expected answers.

However, there are some **issues with this methodology**. Setting aside the fact that the scientific basis on which these features are being detected can't be inspected, since the source code isn't available, and the software's documentation may be vague or unclear on how the analysis is actually implemented, this method only proves that the software works correctly in a controlled environment, on a specific dataset with known features.

Normally one is **working outside of a controlled environment**, with digital data of unknown origin, which may have all sorts of unusual characteristics. In this scenario, one has to trust that the proprietary research is sound, and/or that the software has correctly implemented the publicly available research.

In either case there's a certain **margin of uncertainty** regarding the trustworthiness of the software, which is compounded by the profit motive, which disincentivizes testing and debugging it.

Finally, proprietary software's **highly centralized** nature means that it suffers from the so-called *maintainer hit by a bus* problem. If **anything happens to the organization** (e.g. they get acquired by another company and the product is discontinued, or they have to cease their operations for any reason) or **individuals** (e.g. illness, burnout) who develop the software, then **updates will stop**, and the software will become **outdated** over time, until it becomes **incompatible with newer software**.

In other words, **proprietary research is always at risk of extinction**, of becoming a fossilized relic. Worse yet, the extinction of a piece of proprietary software also means that all the **research efforts** that went into creating the software will be **lost along with it**, and that they can't be salvaged.

These traits may not be an issue, but they're **critical flaws** when it comes to a subject that **requires scientific rigor** as much as digital forensics does.

## Benefits of free and open software

**Free software** is **not developed for profit**. Funding comes from recurring donations, corporate sponsors, offering complementary services like consulting, bounties requested for the implementation of features.

Sometimes for-profit corporations will release software they developed using free licenses. Researchers may release the code they've worked on together with their research. It's also common that developers receive no compensation at all for their work, and act as unpaid volunteers.

Free software is also commonly **developed in a more open and communal way**, but this doesn't mean that the **development process is uncontrolled**. While everyone is welcome to submit improvements to the source code, **not all submissions** will be included.

The **discussions** surrounding the contributions and their vetting are **publicly available**. This is invaluable, because users of free software get access to the **source code**, but also get to see the **decision-making process** that led to that code. The functioning of the software is fully explained. The analogue of this is the **explanation a judge provides for their decisions**, and the **explanation of methodologies** that scientists provide in their research.

In the case of **severe disagreements** on the direction the project should take developers can *fork* the software. This is no different than how **in science** there can be **several competing theories**, each with its own merits.

Given that there is no pressure to maximize profits, it is possible to **maximize the quality of the software instead**. **Feature requests** and **simple quality-of-life improvements** can be implemented by anyone who is capable and wiling of doing so, and there's a high chance that among the users there are people who have the necessary technical skills.

Developers aren't under strict schedules, so they can work on **finding and fixing** bugs. The **community** at large doesn't just use the software, it actively **contributes to and oversees** its development. Most importantly, since free software is not intended to appeal to a potential buyer it can be **honest about its shortcomings**, about **known bugs** and **incomplete or experimental** features.

It could be said that **free software enables peer review** in software development, and the participation of the public in the development process **increases the software's trustworthiness and reliability**.

Most importantly, **source code** becomes a **living record** of the achievements of scientific research, and a form of **documentation** of how digital systems work. For example, a program that can find deleted files must know how files are stored on the disk, a program that can decode and extract information from a proprietary file format also serves as documentation for that format, and so on.

Copyleft licenses also **perpetuate the distribution of source code**, meaning that the **research and effort put into creating tools will never disappear** or be in vain, and the community can always **keep the software up-to-date**, never allowing it to become a relic of the past.

That said, **free software is not perfect**. There are several shortcomings with it, which can be addressed.

The main one is a **(misguided) lack of trust** in free software. According to the maxim *you get what you pay for*, free software is worthless. This perception is worsened by the fact that it's not developed by a corporate entity with large funding, so it may come across as hard to use, unintuitive, unpolished and amateurish. Worse yet, since the public can contribute to its development, and source code is distributed freely, then that means that it's code that may have been tainted by the unwashed masses, or that it's impossible to find a trustworthy version of the software since anyone who has a copy could modify it prior to distribution.

These are **prejudices** that stem from unfamiliarity with how free software is actually developed and distributed.

It's entirely possible (and not uncommon) for free software to be **developed or backed by corporations**, which often embrace this development model to offset the burden of software maintenance, or to foster goodwill and trust with the public. However, **even when this isn't the case**, and software is developed and maintained by researchers who aren't software engineers by trade, or programmers who aren't researchers, or even amateurs who have the requisite knowledge, what matters is **whether software works as intended, not who developed it**. Whether software works correctly can be **measured in an objective manner**, by running tests to evaluate its capabilities and inspecting the quality of the code.

Secondly, **not all contributions will find their way into the main code base**. Developers can choose to not integrate them. Everyone is free to publish their modified version anyway, of course, but most people will only be interested in the **official release**, maintained by the core team. If one trusts proprietary software, which doesn't even publish source code, it follows that they should also trust the official release of free software, especially since they can study its behavior before using it.

The second issue is that **free software can't make use of proprietary code**. Companies may be willing to share code with each other to enable interoperability between their formats or their systems, but free software has to **reverse-engineer** how these elements work, and then **write a custom implementation**. Having to reinvent the wheel is actually an advantage here, since this knowledge can then circulate in the form of code. The main limitation is **technical measures** intended to prevent reverse-engineering, since legally speaking reverse-engineering can fall under the **fair use** doctrine.

Finally, the use of free software can be **counterproductive when circumventing security measures is necessary to acquire data**. This is because publishing the source code directly informs the device's manufacturer about which vulnerability in their system has been exploited, and so an update that removes this vulnerability can be published quickly.

This makes **state-sponsored spyware** particularly insidious, since it has to remain proprietary in order to be installed covertly on a suspect's device. However, this **secrecy also leaves ample room for abuse**, such as planting evidence. If the spyware was actually used to harm their case, but defendant isn't allowed to know how said spyware works, how can they possibly defend themselves and have elements to argue that there's been a serious misconduct? They can only make tenuous allegations.

The type of **software which requires secrecy to work** amounts to a **near-complete erasure of the constitutional right to effective legal counsel**.

Conversely, **software that embraces openness** strengthens this right. If a **trial results in a conviction**, then the defendant can **appeal both the judge's legal reasoning and the software's technical assessment**.

## Factors to assess software quality

If the software's **source code is available**, then it's possible to **assess its quality**, and in turn determine the **software's reliableness**.

The most important factor is the **choice of programming language**. It's important to use **modern**, **memory-safe** programming languages with that have both **strong and static typing**. These features **drastically reduce the likelihood of bugs** at the outset.

Memory-related bugs are extremely common and can be hard to track down[gaynor2019], while using strong and static typing[hurd2021] ensures that data structures in the program are consistent, and avoids bugs where the program is expecting one kind of data structure, but receives another.

[gaynor2019]: See A. Gaynor, *Introduction to Memory Unsafety for VPs of Engineering* (2019). <https://web.archive.org/web/20190812151808/https://alexgaynor.net/2019/aug/12/introduction-to-memory-unsafety-for-vps-of-engineering/>.
[hurd2021]: See T. Hurd, *Introduction to Static, Dynamic, Strong and Weak Data Types* (2021). <https://web.archive.org/web/20210603180908/https://www.sitepoint.com/typing-versus-dynamic-typing/>.

It is preferable to use **simple, consistent, opinionated languages** that prioritize **convention** and standardization over complex, expressive or unopinionated languages where there are multiple approaches to achieve the same goal[winestock2021].

It is possible to deviate from these recommendations, but care must be taken to minimize the impact of drawbacks. This is possible when a memory-unsafe, type-unsafe or complex language is **well-established** and has a **large and knowledgeable community** of developers, so that there's **documentation and tooling** to ease the development process, and ensure that software is reliable in spite of the hurdles.

[winestock2021]: See R. Winestock, *The Lisp Curse* (2011). <https://web.archive.org/web/20110416211304/http://winestockwebdesign.com/Essays/Lisp_Curse.html>.

**Documentation** is also essential. It can be broadly divided into **documentation for end-users**, which is concerned with installing, configuring and using the software, and **documentation for maintainers**, which is concerned with detailing the design choices and implementation details, and serves as a guide to introduce new developers to the code base.

The latter becomes useful when it's necessary to prove the **trustworthiness** of the software. It's the equivalent of producing the project of a building to show that it's structurally sound. One of the best-documented pieces of free and open source software is *SQLite*[sqlite-docs].

[sqlite-docs]: See <https://sqlite.org/docs.html>.

It's important that **documentation too is distributed with a free license**, and that it's **kept up-to-date with software**. If the software and documentation diverge, it can be challenging to tell where the mistake lies.

Developers almost always rely on **third-party code**, which is code that was written by other developers. Such code is often called a **software library**. **Code reuse is a good practice**, since it leads to **specialization**.

Maintainers can focus all of their efforts into improving their library, and **improvements to one library** immediately translate to **improvements to all the software that depends on that library**. If everyone wrote all of their code from scratch and never reused any, this wouldn't be possible.

As such, **it's perfectly acceptable to rely on widely-used libraries**, since this also implies a degree of **public scrutiny** regarding their correctness. Depending on obscure or outdated libraries should be treated as a negative, unless it's demonstrated that these libraries are mature, stable, or otherwise trustworthy.

If **libraries are distributed with an open license**, but they're not up to standard for the needs of software used for scientific evidence (they don't have enough documentation, they're not robust enough, and so on), it's possible to **improve them** until they are. Being able to build on software saves the effort of creating an implementation from scratch.

When distributing software it's useful to distribute its source code along with the source code of any third-party libraries it depends on, a technique which is called **vendoring**[macwright2021].

[macwright2021]: See T. MacWright, *Vendor by default* (2021). <https://web.archive.org/web/20230929010221/https://macwright.com/2021/03/11/vendor-by-default>.

This avoids many issues that are related to third-party code, such as **supply-chain attacks** (an attack on the third-party code won't affect existing distributions) or **dependency hell** (a situation that arises when there's conflicts between dependencies). If a developer distributes the code as it exists on their machine, it **ensures that the behavior of the code is also reproducible**.

It's important to evaluate the **quality assurance process** for software. Developers should perform both **static analysis** of their software to identify and correct potential issues in the source code, and **dynamic analysis** to determine that the software works correctly, and handles unexpected situations gracefully.

**Unit tests** can be written to verify that each component of the software works correctly in isolation. **Integration tests** verify that the components work together correctly. These tests can be **run automatically**, so that developers can get immediate feedback as to whether changes to the code don't produce the expected results.

Tests are also useful to **avoid regressions**, a situation where a bug that had been fixed presents itself again, and in general serve as a **form of documentation** for developers, since they demonstrate how to use the source code.

Finally, it's important to assess **whether the software is distributed in a reproducible manner**. It doesn't matter how technically excellent software is, if it's distributed improperly to the public. Techniques like *vendoring*, *reproducible builds* (making the build process as deterministic as possible), and *containerization* (creating isolated, clean-room virtual environments for the software to run in) ensure that the behavior of software is **reproducible**, and that software works the same way across different systems.

## Good development practices for free software

This section is closely related to the previous one. It introduces more factors to assess software quality which are related to the development process.

The first factor is **determining the scope of software**. It's generally better to have **many small tools** that do one thing, do it well, and are designed to work together, rather than a large, all-encompassing one. The main reason is that smaller programs are also easier to reason about, but having specialized programs and reducing duplicate effort is just as important.

In accordance with that logic, it's also useful to structure the program in two parts. The **back-end** handles all the data-processing logic, and the **front-end** handles presenting data to the user. Cleanly separating them makes it much **easier to extend either**, and also makes it possible to extract the back-end into a stand-alone library.

It's always advisable to use **free software licenses**. A non-copyleft license can be used for very simple programs, where the source code would be shorter than the text of the license. But for anything else, it's advisable to use the copyleft **GPL license**, ideally in its **GPLv...-or-later** version, since GPL versions aren't backwards-compatible[gpl-or-later].

[gpl-or-later]: See R. Stallman, *For Clarity's Sake, Please Don't Say “Licensed under GNU GPL 2”!* (2022). <https://www.gnu.org/licenses/identify-licenses-clearly.html>.

**Distributed version control systems** are the cornerstone of modern software development. They keep a **historical record** of software, and **simplify collaboration** by providing tools to merge changes made by different people to the same file. Learning them involves a learning curve, but the benefits are more than worth it.

In particular, they can be used to **distribute code** along with its history, verify a copy's **integrity**, retrieve a **specific version** of the code, **add contributions** back into the code base, find out **which versions of software are affected by a bug**.

If a project decides to accept **third-party contributions**, it should define and publish a **procedure** regarding how to handle them. In particular, contributions should be **reviewed** to make sure they're pertinent, useful and in good faith, contributors should be asked to sign a **licensing agreement** to avoid legal ambiguity, and only a group of **select people** should be responsible for **including contributions** into the main code base.

In general, the **whole development process** should be **transparent to the public from beginning to end**. All discussions regarding development, bugs and support should be archived and remain available to the public, both to maintain a historical record and to ensure a distributed oversight.

There have been several cases of **bad-faith or harmful contributions** to open source projects, but these cases only stress the **importance of having a rigorous and transparent procedure** in place. **Trust** comes from knowing the risks, not being kept in the dark about them, as is the case with proprietary software.

Finally, the development process should also be **automated** where possible. This reduces the potential for **human error** and ensures **consistent results**. For example, developers can set up a **continuous integration** system. When they distribute a new version of the software, this system will automatically the tests included with software, and if any tests fail it'll prevent the new version from being published. This reduces the chance of releasing a broken update.

## Free software for digital forensics

The **operating system** is the **most foundational piece of software**, since it provides all the features that are necessary to execute software, and interact with hardware. There are **free and open source** operating systems, which have all the same advantages as free and open source software. In short, it's possible to know how they work, and since they can be duplicated freely so that all the elements necessary to analyze software are reproducible.

*GNU/Linux* is the most widely used free and open source operating system. There are many versions of GNU/Linux, called **Linux distributions**, each tailored for a specific purpose. There are several distributions for digital forensics, such as *CAINE*, *DEFT*, *SIFT Workstation*, *Kali Linux*, *BackBox Linux*.

They all have several traits in common. They don't have to be installed before use, but they can be booted in **live mode**, so that they can be executed directly on the hardware that's being acquired. They **block all write operations** by default and make devices available in **read-only** mode in order to preserve evidence. They often come with **pre-installed software** for convenience and for reproducibility (using the same version of the operating system also implies using the same version of the pre-installed software). Finally, they often feature **graphical interfaces** to speed up typical workflows.

Regarding **software for data acquisition**, *ddrescue* is a piece of software that's specialized in recovering data from potentially faulty devices. Data acquisition can be interrupted and resumed at any point, and it'll produce a log file with details about partial acquisitions and unrecoverable data. If *ddrescue* isn't available, the ubiquitous *dd* can be used instead. It isn't specifically tailored for data recovery, but it can still be useful with the correct options. *ddrescue* and *dd* will produce a raw, uncompressed forensic image. The user is also responsible for manually computing the hash digest of this image.

*Guymager* is another popular choice. It features a graphical user interface, and can save images in various formats that already feature a hash digest.

*Wireshark* can acquire network data, and is widely used in network forensics. It can be paired with other software that's specialized in data acquisition from network sources (such as *rclone* for cloud storage, *yt-dlp* for video streaming websites, *Instaloader* for Instagram, *DiscordChatExporter* for Discord, and so on) to create a forensic acquisition of that data.

*FIT* is an all-in-one tool that follows this logic, combining various libraries to download data from popular sources with a library to capture network traffic. The **advantage of combining various widely-used libraries** like this is the small amount of original code that needs to be scrutinized.

There is free and open source software for memory forensics as well. *WinPmem* and *LinPmem* can be used to acquire memory from Windows and Linux respectively.

Regarding **software for data preservation**, programs such as *BorgBackup* and *Restic* allow users to create encrypted and compressed backups of data, and easily verify their integrity. These archives can then be stored on *OpenZFS*, a filesystem that can create redundant copies of data, regularly monitors their integrity, and can correct damaged data.

Data should be copied using robust utilities that can resume transfers on errors, verify the integrity of transferred data, and are designed to handle large amounts of data, such as *Rsync*.

The chain of custody can be stored in a version control system like *Git*, which enables users to apply digital signatures to commits.

Regarding **software for data analysis**, there are two approaches. *Autopsy* is the most well-known example of a **monolithic** software that offers many features under a single graphical interface.

The advantage is the ease of use by end users. They're more intuitive, are optimized for typical workflows, can automatically generate reports. *Autopsy* in particular is not far behind proprietary software. The disadvantage is that the user's choices are limited to what's available in the program, and it can be tricky to extend it.

The second approach is to use **many small utilities**, designed to be interoperable with each other. This requires more effort on the user's part, but it pays off in absolute flexibility.

For example, many of *Autopsy*'s functionalities can be reproduced using separate programs, such as *md5sum* and *sha1sum* to calculate the cryptographic hash digest of files, *PhotoRec* to find and extract deleted files, *file* to determine the file format of files, *grep*, *ripgrep* and *ripgrep-all* to search for keywords inside files, *imagemagick* and *ffmpeg* to manipulate images and videos, *stat* to extract the creation, modification and access time.

*Wireshark* can also analyze the network data it captured, and *Volatility* can be used to examine memory acquisitions.

Running these programs manually would be tedious and error-prone. It's possible to automate their execution using **scripts**, which can then be shared with other users. In the case of one-off scripts devised for a specific case, there's still value in preserving them, since they represent a form of documentation on how the expert witness arrived at their conclusions.

*VirtualBox* and *QEMU* can be used to create **virtual machines**. These are virtual environments that are isolated from the "host" operating system, and can be used to run a "guest" operating system. They have various uses, such as analyzing malware in a safe environment, performing destructive operations in a reproducible manner (virtual machines support "snapshots", which allow users to restore a previously saved state), simulate processes that involve various systems, and so on.

## Conclusion

Digital forensics is a delicate forensic science. Its man-made origin arguably makes it harder to study compared to natural sciences. Natural phenomena don't change, only our understanding does. Digital phenomena on the other hand are constantly changing, they're often secretive in ways that make it hard for them to be studied, and our full understanding is always lagging behind.

It's a science that's necessary to prove computer crimes, and useful to investigate all other crimes, given our reliance on digital devices. Its complexity and potential usefulness is what demands an approach that's rigorous and transparent.

Scientists and judges have to justify their decisions, their credibility depends on the fact that their claims can be scrutinized, verified, appealed, proven wrong. This isn't the case with proprietary software, which keeps its inner workings a secret. Proprietary research and software are at odds with the core values that inspire scientific and legal procedures.

On the other hand, these core values resonate with the values of free and open source software. Free software is inherently more trustworthy, even if it's less capable than proprietary software. The fact that anyone can study it and suggest improvement is not a weakness or a mark of amateurishness, it's its biggest strength. There are many publicly-available resources on good development practices. If anything, free and open source software can only get better over time.

Proprietary research and proprietary software are always on the verge of becoming forgotten, irrelevant, it's a short-term investment. Free and open software, especially when released under a copyleft license, will keep on circulating and can always remain relevant as long as someone maintains it. It's a long-term investment that will never go to waste, even if it becomes obsolete it will remain useful as a historical record. In short, it benefits everyone with more knowledge, more transparency, more trust in the legal process, more fairness, instead of benefitting a small group of people with mere profits.