# On digital forensics

*Written by Luca Piras.*

*This document is released under the CC BY-SA 4.0 license.*

- [On digital forensics](#on-digital-forensics)
  - [Introduction](#introduction)
  - [Source code and machine code](#source-code-and-machine-code)
  - [Free software and proprietary software](#free-software-and-proprietary-software)
  - [Software licenses](#software-licenses)
  - [Digital forensics](#digital-forensics)
  - [Scientific research in digital forensics](#scientific-research-in-digital-forensics)
  - [Importance of free software in scientific research](#importance-of-free-software-in-scientific-research)
  - [Digital forensics in legal proceedings](#digital-forensics-in-legal-proceedings)
  - [Acquiring digital evidence](#acquiring-digital-evidence)
  - [Storing and preserving digital evidence](#storing-and-preserving-digital-evidence)
  - [Analyzing digital evidence](#analyzing-digital-evidence)
  - [Evaluating digital evidence](#evaluating-digital-evidence)
  - [Downsides of proprietary software](#downsides-of-proprietary-software)
  - [My personal experience with proprietary software](#my-personal-experience-with-proprietary-software)
  - [Benefits of free and open software](#benefits-of-free-and-open-software)
  - [Factors to assess software quality](#factors-to-assess-software-quality)
  - [Good development practices for free software](#good-development-practices-for-free-software)
  - [Free software for digital forensics](#free-software-for-digital-forensics)
  - [Conclusion](#conclusion)

## Introduction

This document is a translated summary of the final dissertation I wrote for master's degree in law at the University of Bologna, and a retrospective analysis of its merits.

My dissertation was concerned with the **use and advantages** of **free and open source software (FOSS), as opposed to proprietary software,** for the **handling and analysis of digital evidence in legal proceedings**.

My **argument** was that FOSS software is **always preferable to proprietary software** because it results in **publicly-available scientific research** in the field of digital evidence, and its scientific foundations and technical functioning are **fully reviewable** in the context of a legal proceeding. There are other reasons, which will be analyzed further, but these are the most significant ones.

This document is organized as follows. The first section will explain what are the differences between FOSS and proprietary software. It may seem like a digression, but it's necessary to understand the difference between non-free (proprietary) software and FOSS.

The second section will explain what is digital forensics. It will provide a definition of the subject, elaborate on its ties to the scientific method and legal proceedings, and why the FOSS model is a better fit for the subject.

The last section will provide examples of FOSS in digital forensics.

## Source code and machine code

**Digital evidence** is evidence in the form of **digital data**. **Software** is what allows users to **create, read, update and delete digital data**. Likewise, in order to **handle and analyze digital data for the purposes of a legal proceeding, one must also use software**.

When people talk about software, they're usually referring to **machine code**, a long list of very simple, low-level instructions that a computer can execute. Humans find it hard to read and write machine code, because they prefer to write short lists of very abstract, high-level instructions called **source code**. The difference between source code and machine code is comparable to the difference between saying "go to the store to buy milk" and "check the weather, put on appropriate clothes, get the car keys, lock the front door, turn on the car, check that there's enough fuel in the car" (and so on).

Computers can't execute source code as-is. A **compiler** is a piece of software that takes care of translating the abstract instructions found in source code into low-level machine code, so that they can be executed. This is a process known as *compilation*, and it's not reversible. Given machine code, it's impossible to go back to the original source code. All one has is a long list of simple steps, but there's no names to explain what the intent between these steps is.

Therefore, compilation is **necessary** to execute source code, but it also **strips away the original structure** in the resulting machine code. Having **access to the source code is necessary** only if one wants to **make changes** to the software, or **study how it works**. If all one wishes to do is **execute software**, then they can simply use the **machine code**.

## Free software and proprietary software

The "free" in free software does not refer to its price[^fsf-selling], but rather, to the **four freedoms**[^fsf-freedoms] which are granted to end-users.

[^fsf-selling]: See Free Software Foundation, *What is Free Software?* (2024). <https://www.gnu.org/philosophy/free-sw.html>.
[^fsf-selling]: See Free Software Foundation, *Selling Free Software* (2021). <https://www.gnu.org/philosophy/selling.html>.

The first freedom is to **run software for any purpose**. If someone has a copy of the software, they can simply use it. They don't have to ask the developers for prior authorization, and there can be no technological measures in place to restrict its execution.

The second freedom is to **study how the software works and modify its source code**. This means that free software **must always provide a copy of the source code**, and can **never be released only in the form of machine code**. Free licenses instead encourage users to gain an understanding of the source code so that they can **understand what the software is doing**, and also so that they can **extend it** to suit their needs, and **improve it** to fix bugs. If the source code is available, but it can't be modified or redistributed[^tarsnap-license] then the program is said to be **proprietary, but source-available**.

[^tarsnap-license]: *Tarsnap* is a notable example of software that is source-available, since if the source code is modified, then the modified version can no longer be redistributed. See Tarsnap Backup Inc., *COPYING* (2025). <https://github.com/Tarsnap/tarsnap/blob/master/COPYING>.

The third and fourth freedoms are to **redistribute copies of the software**, and to **redistribute modified copies** respectively. This means that free software can also be **redistributed by anyone who has a copy**, without asking the original developers for permission.

If any of these freedoms are missing, then the software is **proprietary**.

**Proprietary software** often **limits the user's ability to execute it**, by means of a hardware dongle or other measures to that effect. These limitations may affect how many users can use the software, or what features they are allowed to use. It usually **doesn't distribute its source code**, because if it exposed how it works, it'd be **tantamount to revealing trade secrets**, and it would lose its advantage over the competitors. It often features measures intended to **prevent people from studying how it works** (there's measures to prevent reverse-engineering), and as a consequence **it can't be modified** either (there's measures to block the software's execution if it's been tampered with). Finally, proprietary software often forbids users from redistributing it by creating new copies, in order to not lose on sales.

## Software licenses

In practice, the freedoms of free software and the limitations of proprietary software are defined in a **software license**, a **contract** between the developer of the software and the end-user which determines what rights are granted to the users of the software, to what extent, and under which conditions.

Art. 10 of the *TRIPS Agreement* establishes that **software is protected by copyright law as a literary work**, as defined in art. 2 of the *Berne Convention*. This means that **the developers reserve all rights** on the **creation of copies and derivative works** on the software they create, unless stated otherwise.

For example, as far as copyright law is concerned even simply executing software is considered creating a copy of the work, since the software has to be copied from the disk to memory in order to be executed. This means that "executing the program" is a right which must be granted explicitly.

**Proprietary software licenses** follows the **traditional model of copyright law**, where **end-users are strictly consumers of the copyrighted work**, and are not allowed to create derivative works or further redistribute the work. The author's rights, and the limitations on the end-user that stem from them can be **enforced at the software level** and **circumvention or removal** of these measures is **unlawful**, as per art. 11 and 12 of the *WIPO Copyright Treaty*.

On the other hand, **free software licenses** use **copyright law to enforce the freedoms that define free software**. In particular, **copyleft licenses** like the *GNU GPL* allow the use, **modification** and redistribution of code on the condition that **the resulting code adopts the same license**. The practical effect of the self-propagation of the license is that **source code remains always available**.

## Digital forensics

**Digital forensics** is the **forensic science** that studies **how digital systems and digital data work**.

The catalyst for the development of digital forensics were **harmful actions that could be only committed by means of a computer, or against another one**. There were attempts to interpret traditional criminal statutes broadly (for example, using a computer system and then charging the cost on someone else could be prosecuted as larceny, unauthorized access to a computer system could be prosecuted as trespass), but these interpretations were deemed too vague and imprecise to be constitutional under the *vagueness doctrine*[^vagueness-doctrine]. As such, lawmakers enacted **criminal statutes that specifically punished computer crimes** [^nugent1991].

[^nugent1991]: See H. Nugent, *State Computer Crime Statutes* (1991). <https://www.ojp.gov/pdffiles1/Digitization/128780NCJRS.pdf>.
[^vagueness-doctrine]: See Constitution Annotated, *Amdt5.8.1 Overview of Void for Vagueness Doctrine*. <https://constitution.congress.gov/browse/essay/amdt5-8-1/ALDE_00013739/>.

The **only way to prove** these new crimes was to gather **digital evidence from the systems involved in the incident**. The study of **how to best acquire, preserve, analyze and interpret digital evidence** was initially called *computer forensics*. It later became known more generically as *digital forensics*, since its scope had expanded to all the digital technologies that had developed over time, such as computer networks, mobile devices, cloud storage, cryptocurrencies, and so on.

The purpose of digital forensics is to **study how hardware and software works**, in order to assist **law-makers and judges** with the necessary technical knowledge to **make informed decisions** while writing **substantive and procedural law**, and when **evaluating digital evidence** during legal proceedings.

For a **practical example** of the kind of domain-specific knowledge that digital forensics can provide, let's assume that one wants to prove that someone visited an internet website.

The **most intuitive** way to do it would be to turn on the suspect's device, open the browser, and search for traces of that website. However, this is also the **most harmful**, since it's akin to a coroner handling a corpse without wearing gloves and using tools that haven't been sanitized. Booting a computer and opening programs is extremely invasive, and directly alters the evidence. After a computer is booted and during its operation, there are many services running in the background, manipulating files, and possibly changing or overwriting useful traces.

The **proper approach** to handling evidence is much more involved, and requires using specialized software to create multiple copies of the device's internal drive called *forensic images*, calculating their *cryptographic hash digest* so that their integrity can be verified, using specialized software to process the images and extract the browsing history, and where feasible, using multiple approaches to make sure that they all come to the same conclusions.

Furthermore, these steps should be carried out by an expert who is **knowledgeable** about the current best practices, **aware** of the legal significance of what they are doing, and capable of **arguing in defense** of their approach in front of the judge.

Digital forensics was originally developed in the context of crimes against digital systems, but it's also relevant when a **traditional crime is committed by means of a computer** (e.g., wire fraud or libel on social media), or even when **computers contain useful evidence** that another crime has been committed (e.g., a sale of illicit goods that was conducted in person, but the parties talked organized the sale online prior to meeting).

## Scientific research in digital forensics

I believe that digital forensics is a science, and that **digital systems** can be studied using the **scientific method**. There are two reasons for doing so.

The first is the ever-increasing **complexity of digital systems**. Hardware and software are complex, continuously evolving, and their functioning and mutual interaction between systems become ever more **intricate and unpredictable**. This means that making **ahead-of-time, deductive predictions** about how a system is going to behave based only on its publicly available documentation is **not good enough**. The documentation may be incomplete, inaccurate, or lacking for the purposes of digital forensics.

Rather, the **only reliable knowledge and predictions** about how systems work are the ones obtained through **empirical observations and inductive reasoning**. In other words, digital forensics **builds a theoretical model** of how digital systems work, and then **validates and improves that model** through experiments, just like scientists do. The scientific knowledge accumulated in this way can then be used to inform decisions in a legal proceeding.

The second reason is that **digital devices are programmable** and **digital data be duplicated infinitely**, with **every copy being identical** down to the last bit. This makes digital systems the **ideal subject for scientific experiments**.

Scientists must **repeat** experiments over and over to ensure that their results are consistent, and then an independent group of scientist will attempt to **reproduce** the experiment, to validate or disprove the results. Every repetition must have the same starting conditions, precautions must be taken so that the the external environment doesn't affect the experiment, and resetting the test environment between repetitions may take a significant time and resources. These are issues in natural sciences, because scientists don't perfectly control the environment.

On the other hand, digital forensics researchers can **program a computer so that it automatically** to **resets itself to the starting conditions**, then **runs the experiment**, **validates the results** and **produces a report**. They have **full control over the environment** the experiment is run in, and they can **create a copy** of this environment and **share it** with other researchers, who can then run it on their own machines and try to **falsify the results**.

If different researchers obtain different results, then **the model is improved**, until it produces **consistent results**. For example, let's suppose that a researcher is trying to learn how an undocumented file format is structured. Through a process of trial and error, they manipulate parts of the file, observe the effects of these changes, and **document how the file is structured**. Finally, they will **write a program that can extract information** out of the file, according to their research.

The documentation and the program is shared with other scientists, who then proceed to run the program on their own samples of this file type. If the program produces reasonable outputs, it can be believed that it's working correctly. If it fails to analyze the data, this means that the file type is more complex than what was believed. The scientific method cycle starts over, until it produces a theoretical model and analysis software that's more capable, and can handle inputs that the previous model couldn't.

Scientific research produced by digital forensics researchers consists of two parts, the **documentation** of how a certain system (some feature of an operating system, a program, a file format, a network protocol, and so on) **has been observed to work**, and **software** that is based on their findings and can **extract useful data**.

## Importance of free software in scientific research

The importance of **freely and openly sharing the results of scientific research** cannot be stressed enough. The free flow of information allows science to thrive and **benefits everyone**, since everyone can join the **falsification process**, and stimulate the improvement of better and more accurate theoretical models that will be made available to the public.

On the opposite end of openness and transparency is **proprietary research**, which is **kept secret from the public**. This results in an immediate **loss of rigor and efficiency**, since there is no public oversight to falsify the theories and test the tools that have been produced. Furthermore, this research **exclusively benefits the private entities** that use it to develop and sell products and services at (often) **high price points**, given the small (or non-existent) pool of competitors.

This **distinction between public and proprietary research** is reminiscent of the **distinction that exists between FOSS and proprietary software**. Free and open source software was not developed specifically in the context of scientific research, but it's undeniable that public scientific research and FOSS are in synergy with each other and **share similar values**.

The software developed **during scientific research** (the software that runs experiments on data) or that **implements scientific findings** (the software that is based on the scientific model that was created and analyzes data) should be released as **free software** and the **source code** should always remain available. This ensures that other researchers can always **study** this software, **verify** its correctness, **improve** it if there are issues or new discoveries, and freely **redistribute** it to other researchers or end-users.

Ideally, the **software used to study the systems** (the software that scientists use to modify and study data) should **also be free software** itself. This would ensure that **all software that is used or produced** in the context of scientific research is free software and benefits from its advantages.

## Digital forensics in legal proceedings

The **practical purpose of the scientific research produced by digital forensics** is twofold. It provides **anyone who handles digital evidence in any capacity** the necessary knowledge to do so safely, and to the best of their abilities, and it serves as the **foundation upon which the software to handle digital evidence with** is produced.

These two purposes are **closely related**, because **digital evidence consists entirely of digital data**, and so it **must be acquired, preserved, analyzed and presented for evaluation by means of software**.

Any **non-digital representation** of digital evidence, such as printing out an email or a log file, should be used for **illustrative purposes only**, but it should never replace the actual piece of evidence. In other words, it should be treated as if it were a photo of an object, rather than the object itself. The **original digital version** must always be **preserved**, so that it can be used if **evidence is to be re-examined** for any reason.

## Acquiring digital evidence

The first step of handling digital evidence is **acquiring digital data**. In criminal proceedings, this step mainly involves and concerns **law enforcement officers** (as they will likely be the first to handle the evidence) and **prosecutors** (as they direct the investigations), who may perform these activities on their own, or appoint an expert. In civil proceedings, these steps will be performed by **court-appointed or party-appointed experts**.

The software that **acquires digital data** will produce a **forensic image** of the data, that is, a **copy that is identical to the original, bit-by-bit**. This software should also take care **not to alter the original data**, and it should **create a log file** containing identifying information about the operation (such as a timestamp for the beginning and end of the operation, an identifier for the acquired evidence, the examiner(s), the version of the software, the settings being used, any warnings and diagnostic messages, and so on).

The most important element in the log file is the acquired data's **cryptographic hash digest**. A *hash digest* is the product of a **hash function**, an algorithm that can take an **arbitrary amount of data** as input, "hashes" it into smaller chunks, and then combines these chunks together to return a **fixed-length value**.

The most fundamental property of hash functions is that the **same input data will always result in the same output data**. Hash digests can be thought of a **fingerprint** of the original data, and can be used to **verify the integrity of copies** compared to the original data **at any point in the future**.

It's important to use **cryptographic hashing functions**, because they provide various security guarantees, such as the **avalanche effect** (changing **even a single bit** in the input will produce a **completely different digest**, which is useful to catch **accidental bit-flips**) and **second preimage resistance** (if one knows the input data and its digest, it's nearly impossible to alter the input in such a way that it still produces the same digest, which is useful to catch **intentional tampering** of the data).

Software that acquires data should provide **abundant and accurate diagnostic information**. It **must report any issues** during the acquisition phase, **no matter how insignificant** they may appear to be. These issues can always be dismissed as not significant after the fact, but if they go unreported, the examiner won't be aware of them.

In the case of **volatile data**, where acquiring it again is **impossible** (such as network connections, since they are ephemeral and only exist for the duration of the transfer) or **leads to different results** (such as acquiring the contents of the RAM on a live system, since the contents of the RAM are constantly changing) or **could alter the original data** (such as acquiring the contents of a faulty device, since every attempt increases the likelihood that the device may become unreadable) the software should be able to **capture a partial amount of data**, and provide a **detailed explanation** of what data has been acquired and what other data the program was aware of (but decided not to acquire, and why).

The final step of the acquisition phrase is **digitally signing the log file with a timestamp**. The goal is to prove the **existence and contents** of the document that details of the operation, ideally **as soon as the acquisition ends**. The timestamp should be provided and recorded by a **time-stamping authority**.

## Storing and preserving digital evidence

After data has been acquired, it must be **stored and preserved**. This step has an **extremely wide scope**, as it begins as soon as data has been acquired, and lasts until data is no longer relevant to a proceeding and can be disposed of, and it doesn't concern only **evidence custodians** proper but also **whomever handles the evidence at any point**.

The reason is that digital data is **fragile**. The physical media it's stored on can **deteriorate** and **become unreadable** or produce **faulty values** if handled improperly. If **digital data is tampered with**, whether **intentionally** or **by accident**, it may be possible to detect modifications, but it's **impossible to undo** them, and any attempt to reconstruct the previous state is based on guesswork.

Software used in this step must be able to **verify the data integrity** by recalculating its cryptographic hash. Ideally it should also be able to **encrypt** the data to ensure that it remains confidential, even if the device it's on is stolen. It should also be able to manage **multiple backups** of the same data, so that **if any copies get damaged, they can be repaired** by comparing them with the other copies.

Software can also be used to maintain a **digital chain of custody**, with handwritten signatures being replaced by **digital signatures** (which can't be forged, and have stronger non-repudiation guarantees).

## Analyzing digital evidence

**Analyzing data** concerns the **judge, the parties** (the prosecutor in criminal proceedings, the plaintiff in civil ones, and the defendant), and the **court-appointed and party-appointed experts**.

The first step is **defining the scope of the expert's analysis**, and **what questions the expert should answer** once they are called to testify. The parties will ask questions that support their legal arguments, while the judge may ask a question to resolve a disputed fact. The expert will then choose the **most appropriate tool and method of analysis**.

Any software used in this phase should be **based on scientific research, that ideally has been published and peer-reviewed**. It should also be **robust and able to handle invalid data gracefully**. It should warn the examiner of its presence, instead of crashing, or processing it but producing invalid or meaningless results.

Besides **interpreting data correctly**, the software should make sure that its output can be **clearly understood by human examiners**. For example, dates are usually stored as how much time has passed since a reference date called the *epoch date*. *Epoch dates* are different on every operating system[^epoch-dates] and can also be picked arbitrarily[^cobol-date]. Once the software correctly interprets the date, it should clearly tell the user whether the date it's displaying is in UTC, or whether it's been converted to the user's time zone, or whether the date already had time zone information embedded in it[^utc-date].

[^epoch-dates]: See D. Lakshmanan, *What Is Epoch Time All About?* (2020). <https://www.maketecheasier.com/what-is-epoch-time/>.
[^cobol-date]: See Raffzahn's answer in *Did missing/corrupt dates in COBOL default to 1875-05-20?* (2025). <https://retrocomputing.stackexchange.com/a/31290>.
[^utc-date]: See Stack Overflow, *Daylight saving time and time zone best practices* (2016). <https://stackoverflow.com/questions/2532729/daylight-saving-time-and-time-zone-best-practices>.

## Evaluating digital evidence

The final step is **presenting the findings** obtained in the previous step to the judge, who has to **evaluate them**. This step mainly concerns the **judge**, who has the delicate role of assessing whether the scientific evidence is admissible and reliable, and then determining how it correlates with the rest of the evidence.

This last point is fundamental. The **judge must not accept scientific evidence as-is** and disregard the rest of the evidence as less trustworthy, because they would be essentially delegating their decision-making power to someone else. At the same time, the judge **can't dismiss scientific evidence outright** on the grounds that they lack the necessary knowledge, skills or experience to properly evaluate it.

There are two standards regarding the **admissibility** of scientific evidence, which are *Frye* (where scientific methodologies must be **generally accepted by the scientific community**) and *Daubert* (where general acceptance is one of several factors, and judges must also evaluate the **underlying scientific principles**).

Under the more lenient **Frye standard** there are no issues with tools for the analysis of digital evidence developed as a consequence of proprietary research, as long as they're widely used by professionals. The soundness of its foundation, the **scientific research it was built upon is never put into question**.

The **Daubert standard** is more thorough, since in addition to general acceptance judges also have to evaluate whether the theory is **falsifiable** (and whether it has been), whether it has been **published and subjected to peer review**, its known or potential **error rate**, the **existence and maintenance of standards** that control its operation.

**Free and open-source tools for the analysis of digital evidence developed in accordance with free and open scientific research** are more in line with the **Daubert standard**, since it's possible to accurately answer all the questions it poses. There has been much discussion on whether the use of **proprietary algorithms** such as *COMPAS*[^proprietary-predictive-algorithms] (and more recently, **AI models**) for **sentencing** is harmful to the **principle of due process**, and the same arguments can be applied to algorithms that analyze evidence.

[^proprietary-predictive-algorithms]: See M. Brenner *et al.*, *Constitutional Dimensions of Predictive Algorithms in Criminal Justice* (2020). <https://journals.law.harvard.edu/crcl/wp-content/uploads/sites/80/2020/09/Brenner-et-al.pdf>.

More generally, the **legal system favors openness** in trials. Judges must provide an explanation for their decisions, because their decisions would be arbitrary otherwise. Trials are open to the public, because secret trials are fertile ground for all kinds of injustices. Criminal trials can involve a jury, because it ensures that the decision taken by a single authority figure also takes into account the opinion of the public. Defendants have the right to know the charges and the evidence being brought against them, or else they wouldn't know be able to mount a thorough defense.

In this context using proprietary research and tools, which are characterized by their secretiveness and inscrutability, feels like a step backwards. If open, peer-reviewed alternatives are available, they should be favored instead. Having **many elements to evaluate in the context of scientific evidence** is a good problem to have, because it means that the final decision is rooted in a **logical and thorough assessment** of the evidence and the scientific theories underpinning it, **rather than a deferential faith** in a method whose only claim to reliability is its generally acceptance by the scientific community.

## Downsides of proprietary software

**Proprietary software** is usually **developed for profit** by organizations or individuals. Funding is mainly obtained by **selling the right to use the software** to consumers, though consulting and formation may also play a significant role.

It is developed in an **autocratic manner**. There may be public roadmaps and customers may submit feature requests, but the developers don't have to honor them if they feel that it would be **unprofitable, or not profitable enough** to do so.

The main focus is on **form and marketability**, rather than **function and user experience**. The perception of the software as authoritative is more important than how efficiently or accurately it actually functions. Developers have an incentive to **not mention or downplay any defects** the software may have, and at any rate, the **users can't tell how it functions** anyway, since the **source code is not available** for inspection.

It's quite likely that products and new features are implemented as quickly as possible, because the developer's time is expensive. As a result, the code base will likely accumulate **technical debt**, making it harder to maintain and increasing the amount of bugs, and **features aren't tested in depth**.

The **high cost** of licenses and the fact that software isn't freely redistributable also means that it's hard to have a **wide, distributed public oversight** on its correct functioning.

An argument can be made that **it is possible to test the correct functioning of proprietary software** by creating a hand-crafted dataset with known features, and then checking if the software detects them and produces the expected answers.

However, there are some **issues with this methodology**. Setting aside the fact that the scientific basis on which these features are being detected can't be inspected (since the source code isn't available, and the software's documentation may be vague or unclear on how the analysis is actually implemented), this method only proves that the software works correctly in a controlled environment, on a specific dataset with known features.

Normally one is **working outside of a controlled environment**, with digital data of unknown origin, which may have all sorts of unusual characteristics. In this scenario, one has to trust that the proprietary research is sound and that the software has correctly implemented the publicly available research.

In either case there's a certain **margin of uncertainty** regarding the trustworthiness of the software, which is compounded by the profit motive, which disincentivizes testing and debugging it.

Finally, proprietary software's **highly centralized** nature means that it suffers from the so-called *maintainer hit by a bus* problem. If **anything happens to the organization** (e.g. they get acquired by another company and the product is discontinued, or they have to cease their operations for any reason) or **individuals** (e.g. illness, burnout) who develop the software, then **updates will stop**, and the software will become **outdated** over time, until it becomes **incompatible with newer software**.

In other words, **proprietary research is always at risk of extinction**, of becoming a fossilized relic. Worse yet, the extinction of a piece of proprietary software also means that all the **research efforts** that went into creating the software will be **lost along with it**, and that they can't be salvaged.

These traits may not be an issue, but they're **critical flaws** when it comes to a subject that **requires scientific rigor** as much as digital forensics does.

## My personal experience with proprietary software

During my internship, I had the chance to use various proprietary industry-standard tools. I'd made various predictions regarding proprietary software in my dissertation. At the time were based on speculation and informed guesses, but as my internship progressed, I learned that they turned out to be accurate.

The first issue with proprietary software is that it's **prohibitively expensive** to use. The company I worked with spent tens of thousands of euros in licenses alone each year. The high cost meant that we could only work with a **limited number of licenses** at the same time, which **reduced productivity** (we had to take turns while using software) and **increased stress** (we constantly had to plan around the limited amount of licenses, especially in the case of large workloads).

Software was **extremely inefficient** (despite us running it on top-of-the-line hardware), and **lacked the most basic quality-of-life features**. In particular, software that performed long-running operations would go on without reporting any progress to the user for long stretches of time. Due to this lack of feedback, the user was never quite sure whether the program was still working or had hung up. This uncertainty resulted in lost productivity, since one had to wait until the program was stuck for an "unreasonable" amount of time, and further stress, because terminating the process when it wasn't actually stuck meant having to start over.

Software was **inflexible and unforgiving**. Many pieces of software asked the user to specify the analysis methods and their options used upfront, with no option to run additional methods later, or re-run individual methods with different options. If the user made a mistake, or realized that the results weren't what they needed or expected, they couldn't simply re-run a part of the analysis, they had to redo everything from scratch. Even if the user made no mistakes, but the software had any sort of issues during the analysis process, the only solution was to delete everything and start over.

Software was **poorly documented**. The manuals and built-in help didn't provide useful advice, so they **always left the user with a lingering doubt** as to whether they were missing something and whether the results were actually what they expected them to be. This not only compounded the previous problem, but also meant that asking coworkers for advice often led to conflicting answers. This is probably the **most significant** issue, because if **users are not sure of what the software has done**, then **any decision that is based on these results is potentially faulty**, since the **results may be uncertain, incomplete or erroneous, if not all three**.

Software **did not provide useful error messages**. Operations would often fail silently, without warnings or explanations. Error messages were generic, with no indication regarding what went wrong, or any possible causes or solutions. Again, this lack of useful or actionable feedback **makes the user question whether the software is actually behaving correctly** when no errors are reported.

Software sometimes presented **arbitrary limitations**. They weren't limitations imposed as part of the license that we were using, these were limitations inherent to the software itself. Having some experience in programming, I know that arbitrary limitations are often a symptom of issues that haven't been addressed in the underlying code, and the easier fix is simply to introduce a limitation instead of reworking the software to be more flexible or efficient. A real-world analogy is having a bridge that needs to be repaired. Telling people to simply avoid the bridge (and take a much longer route) is easier than actually investing the resources needed to fix the bridge.

Software was **unstable and unreliable**. Every employee would experience a tools crashing for no clear reason or getting stuck while processing data at least once every day. An hour wouldn't go by in the office without someone complaining about software not working properly. If "turning it off and on again" didn't work, one had to rely on support. Support tickets were routinely closed without solving the problem. Solutions didn't last long before another issue would grind work to a halt. Employees probably wasted as much time troubleshooting issues and working around software limitations as they did doing productive work.

Software was **too streamlined**. Perhaps the intention was to make it as intuitive as possible, but in practice this meant that software was inflexible in what options it offered. Even when it allowed users to write extensions to augment its capabilities, doing so was so difficult and poorly documented that it may as well not have been a feature at all.

Software was **resilient to automation**. Everything had to be done interactively, and there was often no way to batch operations in advance, meaning that users often had to access their workstations remotely (after leaving work and returning home) to check on software, and ensure that work would get done in a timely manner.

Software was **limited in its output formats**. There was rarely an option to produce output in a structured data format that was easy to process further, most options were intended for creating generic reports for non-technical users that rarely matched our needs, and customization was either limited or absent.

On several occasions **I wrote purpose-built tools to automate work** as much as possible, since the alternative was mind-numbing and error-prone manual labor.

On a few occasion, my knowledge about **FOSS alternatives** proved useful to help colleagues **work around arbitrary limitations** found in proprietary tools. Finally, there were situations with faulty devices where proprietary software refused to produce any output, while FOSS alternatives managed to generate a **more detailed report** that could be used to demonstrate that the device was faulty.

I've also seen colleagues use FOSS tools simply because there were no proprietary tools that could perform the same task.

The rest of this document will explain why that's the case.

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

The second issue is that **free software can't make use of proprietary code**. Companies may be willing to share code with each other to enable interoperability between their formats or their systems, but free software has to **reverse-engineer** how these elements work, and then **write a custom implementation**. Having to reinvent the wheel is actually an advantage here, since this knowledge can then circulate in the form of code. The main limitation is **technical measures** intended to prevent reverse-engineering, since legally speaking **reverse-engineering can fall under the fair use** doctrine.

Finally, the use of free software can be **counterproductive when circumventing security measures is necessary to acquire data**. This is because publishing the source code directly informs the device's manufacturer about which vulnerability in their system has been exploited, and so an update that removes this vulnerability can be published quickly.

This makes **state-sponsored spyware** particularly insidious, since it has to remain proprietary in order to be installed covertly on a suspect's device. However, this **secrecy also leaves ample room for abuse**, such as planting evidence. If the spyware was actually used to harm their case, but defendant isn't allowed to know how said spyware works, how can they possibly defend themselves and have elements to argue that there's been a serious misconduct? They can only make tenuous allegations.

The type of **software which requires secrecy to work** amounts to a **near-complete erasure of the constitutional right to effective legal counsel**.

Conversely, **software that embraces openness** strengthens this right. If a **trial results in a conviction**, then the defendant can **appeal both the judge's legal reasoning and the software's technical assessment**.

## Factors to assess software quality

If the software's **source code is available**, then it's possible to **assess its quality**, and in turn determine the **software's reliableness**.

The most important factor is the **choice of programming language**. It's important to use **modern**, **memory-safe** programming languages with that have both **strong and static typing**. These features **drastically reduce the likelihood of bugs** at the outset.

Memory-related bugs are extremely common and can be hard to track down[^gaynor2019], while using strong and static typing[^hurd2021] ensures that data structures in the program are consistent, and avoids bugs where the program is expecting one kind of data structure, but receives another.

[^gaynor2019]: See A. Gaynor, *Introduction to Memory Unsafety for VPs of Engineering* (2019). <https://web.archive.org/web/20190812151808/https://alexgaynor.net/2019/aug/12/introduction-to-memory-unsafety-for-vps-of-engineering/>.
[^hurd2021]: See T. Hurd, *Introduction to Static, Dynamic, Strong and Weak Data Types* (2021). <https://web.archive.org/web/20210603180908/https://www.sitepoint.com/typing-versus-dynamic-typing/>.

It is preferable to use **simple, consistent, opinionated languages** that prioritize **convention** and standardization over complex, expressive or unopinionated languages where there are multiple approaches to achieve the same goal[^winestock2021].

It is possible to deviate from these recommendations, but care must be taken to minimize the impact of drawbacks. This is possible when a memory-unsafe, type-unsafe or complex language is **well-established** and has a **large and knowledgeable community** of developers, so that there's **documentation and tooling** to ease the development process, and ensure that software is reliable in spite of the hurdles.

[^winestock2021]: See R. Winestock, *The Lisp Curse* (2011). <https://web.archive.org/web/20110416211304/http://winestockwebdesign.com/Essays/Lisp_Curse.html>.

**Documentation** is also essential. It can be broadly divided into **documentation for end-users**, which is concerned with installing, configuring and using the software, and **documentation for maintainers**, which is concerned with detailing the design choices and implementation details, and serves as a guide to introduce new developers to the code base.

The latter becomes useful when it's necessary to prove the **trustworthiness** of the software. It's the equivalent of producing the project of a building to show that it's structurally sound. One of the best-documented pieces of free and open source software is *SQLite*[^sqlite-docs].

[^sqlite-docs]: See <https://sqlite.org/docs.html>.

It's important that **documentation too is distributed with a free license**, and that it's **kept up-to-date with software**. If the software and documentation diverge, it can be challenging to tell where the mistake lies.

Developers almost always rely on **third-party code**, which is code that was written by other developers. Such code is often called a **software library**. **Code reuse is a good practice**, since it leads to **specialization**.

Maintainers can focus all of their efforts into improving their library, and **improvements to one library** immediately translate to **improvements to all the software that depends on that library**. If everyone wrote all of their code from scratch and never reused any, this wouldn't be possible.

As such, **it's perfectly acceptable to rely on widely-used libraries**, since this also implies a degree of **public scrutiny** regarding their correctness. Depending on obscure or outdated libraries should be treated as a negative, unless it's demonstrated that these libraries are mature, stable, or otherwise trustworthy.

If **libraries are distributed with an open license**, but they're not up to standard for the needs of software used for scientific evidence (they don't have enough documentation, they're not robust enough, and so on), it's possible to **improve them** until they are. Being able to build on software saves the effort of creating an implementation from scratch.

When distributing software it's useful to distribute its source code along with the source code of any third-party libraries it depends on, a technique which is called **vendoring**[^macwright2021].

[^macwright2021]: See T. MacWright, *Vendor by default* (2021). <https://web.archive.org/web/20230929010221/https://macwright.com/2021/03/11/vendor-by-default>.

This avoids many issues that are related to third-party code, such as **supply-chain attacks** (an attack on the third-party code won't affect the existing copies that are being shipped together with software) or **dependency hell** (a situation that arises when there's conflicts between dependencies). If a developer distributes the code as it exists on their machine, it **ensures that the behavior of the code is also reproducible**.

It's important to evaluate the **quality assurance process** for software. Developers should perform both **static analysis** of their software to identify and correct potential issues in the source code, and **dynamic analysis** to determine that the software works correctly, and handles unexpected situations gracefully.

**Unit tests** can be written to verify that each component of the software works correctly in isolation. **Integration tests** verify that the components work together correctly. These tests can be **run automatically**, so that developers can get immediate feedback as to whether changes to the code don't produce the expected results.

Tests are also useful to **avoid regressions**, a situation where a bug that had been fixed presents itself again, and in general serve as a **form of documentation** for developers, since they demonstrate how to use the source code.

Finally, it's important to assess **whether the software is distributed in a reproducible manner**. It doesn't matter how technically excellent software is, if it's distributed improperly to the public. Techniques like *vendoring*, *reproducible builds* (making the build process as deterministic as possible), and *containerization* (creating isolated, clean-room virtual environments for the software to run in) ensure that the behavior of software is **reproducible**, and that software works the same way across different systems.

## Good development practices for free software

This section is closely related to the previous one. It introduces more factors to assess software quality which are related to the development process.

The first factor is **determining the scope of software**. It's generally better to have **many small tools** that do one thing, do it well, and are designed to work together, rather than a large, all-encompassing one. The main reason is that smaller programs are also easier to reason about, but having specialized programs and reducing duplicate effort is just as important.

In accordance with that logic, it's also useful to structure the program in two parts. The **back-end** handles all the data-processing logic, and the **front-end** handles presenting data to the user. Cleanly separating them makes it much **easier to extend either**, and also makes it possible to extract the back-end into a stand-alone library.

It's always advisable to use **free software licenses**. A non-copyleft license can be used for very simple programs, where the source code would be shorter than the text of the license. But for anything else, it's advisable to use the copyleft **GPL license**, ideally in its **GPLv...-or-later** version, since GPL versions aren't backwards-compatible[^gpl-or-later].

[^gpl-or-later]: See R. Stallman, *For Clarity's Sake, Please Don't Say “Licensed under GNU GPL 2”!* (2022). <https://www.gnu.org/licenses/identify-licenses-clearly.html>.

**Distributed version control systems** are the cornerstone of modern software development. They keep a **historical record** of software, and **simplify collaboration** by providing tools to merge changes made by different people to the same file. Learning them involves a learning curve, but the benefits are more than worth it.

In particular, they can be used to **distribute code** along with its history, verify a copy's **integrity**, retrieve a **specific version** of the code, **add contributions** back into the code base, find out **which versions of software are affected by a bug**.

If a project decides to accept **third-party contributions**, it should define and publish a **procedure** regarding how to handle them. In particular, contributions should be **reviewed** to make sure they're pertinent, useful and in good faith, contributors should be asked to sign a **licensing agreement** to avoid legal ambiguity, and only a group of **select people** should be responsible for **including contributions** into the main code base.

In general, the **whole development process** should be **transparent to the public from beginning to end**. All discussions regarding development, bugs and support should be archived and remain available to the public, both to maintain a historical record and to ensure a distributed oversight.

There have been several cases of **bad-faith or harmful contributions** to open source projects, but these cases only stress the **importance of having a rigorous and transparent procedure** in place. **Trust** comes from knowing the risks, not being kept in the dark about them, as is the case with proprietary software.

Finally, the development process should also be **automated** where possible. This reduces the potential for **human error** and ensures **consistent results**. For example, developers can set up a **continuous integration** system. When they distribute a new version of the software, this system will automatically the tests included with software, and if any tests fail it'll prevent the new version from being published. This reduces the chance of releasing a broken update.

## Free software for digital forensics

The **operating system** is the **most foundational piece of software**, since it provides all the features that are necessary to execute software, and interact with hardware. There are **free and open source** operating systems, which have all the same advantages as free and open source software. In short, it's possible to know how they work, and since they can be duplicated freely so that all the elements necessary to analyze software are reproducible.

*GNU/Linux* is the most widely used free and open source operating system. There are many versions of GNU/Linux, called **Linux distributions**, each tailored for a specific purpose. There are several distributions for digital forensics, such as *CAINE*, *DEFT*, *SIFT Workstation*, *Kali Linux*, *BackBox Linux*.

They all have several traits in common. They don't have to be installed before use, but they can be booted in **live mode**, so that they can be executed directly on the hardware that's being acquired (this is useful if it's not possible to extract a device's internal storage, and acquire it on its own). They **block all write operations** by default and make devices available in **read-only** mode in order to preserve evidence. They often come with **pre-installed software** for convenience and for reproducibility (using the same version of the operating system also implies using the same version of the pre-installed software). Finally, they often feature **graphical interfaces** to speed up typical workflows.

Regarding **software for data acquisition**, *ddrescue* is a piece of software that's specialized in recovering data from potentially faulty devices. Data acquisition can be interrupted and resumed at any point, and it'll produce a log file with details about partial acquisitions and unrecoverable data. If *ddrescue* isn't available, the ubiquitous *dd* can be used instead. It isn't specifically tailored for data recovery, but it can still be useful with the correct options. *ddrescue* and *dd* will produce a raw, uncompressed forensic image. The user is also responsible for manually computing the hash digest of this image.

*Guymager* is another popular choice. It features a graphical user interface, and can save forensic images in standard formats that are supported by most forensic tools.

*Wireshark* can acquire network data, and is widely used in network forensics. It can be paired with other software that's specialized in data acquisition from network sources (such as *rclone* for cloud storage, *yt-dlp* for video streaming websites, *Instaloader* for Instagram, *DiscordChatExporter* for Discord, and so on) to create a forensic acquisition of that data.

*FIT* is an all-in-one tool that follows this logic, combining various libraries to download data from popular sources with a library to capture network traffic. The **advantage of combining various widely-used libraries** like this is the small amount of original code that needs to be scrutinized.

There is free and open source software for memory forensics as well. *WinPmem* and *LinPmem* can be used to acquire memory from Windows and Linux respectively.

Regarding **software for data preservation**, programs such as *BorgBackup* and *Restic* allow users to create encrypted and compressed backups of data, and easily verify their integrity. These backup archives can then be stored on *OpenZFS*, a filesystem that can create redundant copies of data, regularly monitors their integrity, and can correct damaged data.

Data should be copied using robust utilities that can resume transfers on errors, verify the integrity of transferred data, and are designed to handle large amounts of data, such as *Rsync*.

The chain of custody can be stored in a version control system like *Git*, which enables users to apply digital signatures to commits.

Regarding **software for data analysis**, there are two approaches. *Autopsy* is the most well-known example of a **monolithic** software that offers many features under a single graphical interface.

The advantage is the ease of use by end users. They're more intuitive, are optimized for typical workflows, can automatically generate reports. *Autopsy* in particular is not far behind proprietary software. The disadvantage is that the user's choices are limited to what's available in the program, and it can be tricky to extend it.

The second approach is to use **many small utilities**, designed to be interoperable with each other. This requires more effort on the user's part, but it pays off in absolute flexibility.

For example, many of *Autopsy*'s functionalities can be reproduced using separate programs, such as *md5sum* and *sha1sum* to calculate the cryptographic hash digest of files, *PhotoRec* to find and extract deleted files, *file* to determine the file format of files, *grep*, *ripgrep* and *ripgrep-all* to search for keywords inside files, *imagemagick* and *ffmpeg* to manipulate images and videos, *stat* to extract the creation, modification and access time.

*Wireshark* can also analyze the network data it captured, and *Volatility* can be used to examine memory acquisitions.

Running these programs manually would be tedious and error-prone. It's possible to automate their execution using **scripts**, which can then be shared with other users. In the case of one-off scripts devised for a specific case, there's still value in preserving them, since they represent a form of documentation on how the expert witness arrived at their conclusions.

*VirtualBox* and *QEMU* can be used to create **virtual machines**. These are virtual environments that are isolated from the *host* operating system, and can be used to run a *guest* operating system. They have various uses, such as analyzing malware in a safe environment, performing destructive operations in a reproducible manner (virtual machines support *snapshots*, which allow users to restore a previously saved state), simulate processes that involve various systems, and so on.

## Conclusion

Digital forensics is a delicate forensic science. Its man-made origin arguably makes it harder to study compared to natural sciences. Natural phenomena don't change, only our understanding does. Digital phenomena on the other hand are constantly changing, they're often secretive in ways that make it hard for them to be studied, and our full understanding is always lagging behind.

Digital forensics is a science that's necessary to prove computer crimes, and useful to investigate all other crimes, given our reliance on digital devices. Its complexity and potential usefulness is what demands an approach that's rigorous and transparent.

Scientists and judges have to justify their decisions, their credibility depends on the fact that their claims can be scrutinized, verified, appealed, proven wrong. This isn't the case with proprietary software, which keeps its inner workings a secret. Proprietary research and software are at odds with the core values that inspire scientific and legal procedures.

On the other hand, these core values resonate with the values of free and open source software. Free software is inherently more trustworthy, even when it's less capable than proprietary software. The fact that anyone can study it and suggest improvement is not a weakness or a mark of amateurishness, it's its biggest strength. There are many publicly-available resources on good development practices. If anything, free and open source software can only get better over time.

Proprietary research and proprietary software are always on the verge of becoming forgotten, irrelevant, it's a short-term investment. Free and open software, especially when released under a copyleft license, will keep on circulating and can always remain relevant as long as someone maintains it. It's a long-term investment that will never go to waste, even if it becomes obsolete it will remain useful as a historical record. In short, it benefits everyone with more knowledge, more transparency, more trust in the legal process, more fairness, instead of benefitting a small group of people with mere profits.