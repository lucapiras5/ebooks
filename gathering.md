## Gathering devices and acquiring evidence

The first step of handling digital evidence is **gathering digital devices** and **acquiring digital data**. In criminal proceedings, it mainly concerns **law enforcement officers** (as they will likely be the first to handle the evidence) and **prosecutors** (as they direct the investigations), who may perform these activities on their own, or appoint an expert. In civil proceedings, these steps will be performed by **party-appointed experts**. 

Digital forensics prescribes how devices should be gathered in order to **preserve as much data as possible**. The software that **acquires digital data** will produce a **forensic image** of the data, that is, a **copy that is identical to the original, bit-by-bit**. This software should also take care **not to alter the original data**, and it should **create a log file** containing identifying information about the operation (such as a timestamp for the beginning and end of the operation, an identifier for the acquired evidence, the examiner(s), the version of the software, the settings being used, any warnings and diagnostic messages, the forensic image's *cryptographic hash digest*, and so on).

As the software is acquiring data, it should simultaneously calculate its **cryptographic hash digest**.

---

A *hash function* takes an arbitrary amount of digital data as input, and returns a **fixed-length** amount of digital data as output, called the *digest*, with the guarantee that identical inputs will always produce identical digests. This characteristic is called **determinism**. A common analogy is to think of a digest as the **fingerprint of a piece of data**.

The adjective *cryptographic* refers to certain security guarantees about the function.

The first is the **avalanche effect**, whereby flipping a single bit in the input flips half of the bits in the digest, meaning that even the **smallest possible alteration** in the input will result in a **very noticeable difference** in the digest, which can be caught at a glance.

The second is **collision resistance**, whereby two different inputs should not produce the same output. Since the digest has a fixed length, but the input data can have an arbitrary length, by the *pigeonhole principle* it's certain that different inputs may map to the same digest. The design of cryptographic hash functions tries to minimize the likelihood of this happening in a predictable fashion.

The last one is **second preimage resistance**, whereby if one knows the input data and its digest, it's unfeasible to find a different input that produces the same output.

The first characteristic is useful to find **accidental bit-flips** in the data, usually caused by natural decay or errors while copying the data. The latter two are useful to catch **intentional tampering** of the data.

The digest should be calculated **after copying the data for the first time**, and then **whenever a copy of the data is used**, to ensure that it's **still identical** to the original.

Cryptographic hash functions are the **cornerstone** of digital forensics, because they represent one element of **stability**. They demonstrate that in spite of all its drawbacks digital data can be **reliably duplicated and preserved over time**, which can't be said for conventional evidence.

It's important that the software can **capture as much data as possible**, and **report any issues** during the acquisition phase, no matter how insignificant they may be. Depending on **how volatile** the data being acquired is (the contents of RAM and network connections are the most volatile types of data), it may be **impossible or risky to retry acquiring it**. Having **partial data** is better than having no data, but a **detailed explanation** of what data has been acquired is necessary.

The final step of the acquisition phrase is **digitally signing the log file with a timestamp**. The goal is to prove the **existence and contents** of the document that details of the operation, ideally **as soon as the acquisition ends**. The timestamp should be provided and recorded by a **time-stamping authority**.



For all of digital data's faults there is a silver lining. Digital data can be **copied an infinite amount of times**, **each copy is indistinguishable from the original**, and that it's **easy to demonstrate the integrity of copies**.

Conventional (non-digital) evidence can't be copied, since it's impossible to perfectly reproduce the material arrangement of an object down to the atomic level. Even with things like photocopies, it's always possible to distinguish between the original and its copy.

At best one may create many **representations** of that evidence, such as taking pictures of the crime scene, but the pictures are not a substitute for the actual crime scene. Besides, once **non-digital evidence decays** due to natural causes, or it's **irreversibly damaged** due to the use of an invasive analysis technique, it's **impossible to return to a prior state**. 

On the other hand, **digital evidence can be easily copied**. It essentially consists of a sequence of digits, so as long as those digits are reproduced in an identical fashion, one has obtained an **exact copy of the original**, and **the original and the copy are perfectly interchangeable**.

Digital evidence too is susceptible to decay or damages, and as such it's always advisable to create multiple copies, as to always preserve a **backup of the original**.

It's possible to create a **representation of digital evidence** as well. For example, by printing an email message. However, the printed representation (a sheet of paper) is **not interchangeable** with the original email (digital data), it can't be analyzed or copied in the same way, they're entirely different things.

This point can't be stressed enough. Digital evidence **must remain preserved in its digital form**, and may be **degraded into a representation** for **illustrative purposes only**. Representations of digital evidence are never a substitute for the original, and if **evidence is to be re-examined** for any reason, then one should look at the **digital evidence, not its representation**.

Finally, it's possible to **determine whether a copy is still intact** or not, by using **cryptographic hash functions**. 

----

This includes **law enforcement officers** (as they seize devices or acquire digital evidence by other means), **evidence custodians** (as they're in charge of safely storing devices containing digital data), **prosecutors** (as they investigate a case), the defendant or the parties' **legal counsel** (as they define their legal strategy), **expert witnesses** (as they will analyze the digital data, and will be called upon to explain their findings before the judge), and the **judge** (as they evaluate the evidence that has been presented in preparation for their decision).

That **list should not be considered exhaustive**, since it only mentions the figures involved in civil and criminal proceedings. Different jurisdictions and legal systems may have different figures, but the underlying principle is always the same. **Digital evidence has special requirements**, and the rules and guidelines for its special treatment are prescribed by digital forensics.

Judges in particular have a very delicate role. Given that digital forensics is a science, this means that **digital evidence can be considered a form of scientific evidence**. There are two standards regarding the admissibility of scientific evidence, which are *Frye* (where scientific methodologies must be **generally accepted by the scientific community**) and *Daubert* (where general acceptance is one of several factors, and judges must also evaluate the **underlying scientific principles**).

Under the more lenient **Frye standard** there are no issues with tools for the analysis of digital evidence developed as a consequence of proprietary research, as long as they're widely used by professionals. The soundness of its foundation, the **scientific research it was built upon is never put into question**.

The **Daubert standard** is more thorough, since in addition to general acceptance judges also have to evaluate whether the theory is **falsifiable** (and whether it has been), whether it has been **published and subjected to peer review**, its known or potential **error rate**, the **existence and maintenance of standards** that control its operation.

**Tools for the analysis of digital evidence developed in accordance with free and open scientific research** are more in line with the **Daubert standard**, since they can address all of these questions. The fact that the claims they make can be scrutinized even in the context of a legal proceeding makes them **inherently more trustworthy**.

More generally, the **legal system favors openness** in trials. Judges must provide an explanation for their decisions, because their decisions would be arbitrary otherwise. Trials are open to the public, because secret trials are fertile ground for all kinds of injustices. Criminal trials can involve a jury, because it ensures that the decision taken by a single authority figure also takes into account the opinion of the public. Defendants have the right to know the charges and the evidence being brought against them, or else they wouldn't know be able to mount a thorough defense.

In this context using proprietary research and tools, which are characterized by their secretiveness and inscrutability, feels like a step backwards. If open, peer-reviewed alternatives are available, they should be favored instead. Having **many elements to evaluate in the context of scientific evidence** is a good problem to have, because it means that the final decision is rooted in a **logical and thorough assessment** of the evidence and the scientific theories underpinning it, **rather than a deferential faith** in a method whose only claim to reliability is its generally acceptance by the scientific community.

<!-- TODO judgements involving algorithms in sentencing -->

## Software for handling digital evidence

The previous section established the importance of free and open scientific research, and how it's beneficial to legal proceedings, especially under the Daubert standard. It also hinted that the tools to handle digital evidence should be developed on top of scientific research.

These tools that **handle digital evidence** are **pieces of specialized software**. Their **specialization lies in how they function**, rather than any particular qualifications of their developers.

The **storage** step starts after data has been acquired, and lasts until data doesn't have to be retained anymore and can be disposed of. Software used in this step should be able to **verify the data integrity** by calculating its cryptographic hash and **encrypt** the data to ensure that it remains confidential. Software can also be used to maintain a **digital chain of custody**, with handwritten signatures being replaced by **digital signatures** (which can't be forged, and have stronger non-repudiation guarantees).

The **analysis** step is chiefly **technical**, and involves **finding elements of interest** in the digital data that has been acquired. This is the step where **scientific research is actualized into software**, and so the developers should take care to implement the published, ideally peer-reviewed scientific findings as closely as possible. They should also make sure that software can **handle invalid data gracefully** (signaling its presence instead of crashing with no explanation or producing invalid results) and that it's **easily extensible** (so that other developers can build on top of it instead of having to start from scratch).

<!-- ## The silver lining of digital data

The challenges outlined in the previous sections paint the subject in a rather **unflattering light**. Digital data is generally useful as **circumstantial evidence**, and in the case of computer crimes it's the only kind of **direct evidence** that's available. And yet, it's **volatile and hard to make sense of**. However, that doesn't mean that digital forensics is an exercise in futility, a doomed attempt at trying to create order out of chaos.

 -->