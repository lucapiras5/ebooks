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