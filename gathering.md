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