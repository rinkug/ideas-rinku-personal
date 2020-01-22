Introducing the PSIP Software Improvement Process

**Hero Image:**

 - <img src='https://github.com/betterscientificsoftware/images/raw/master/Blog_0819_Dataviz.png' />[Do we have a hero image?]
 
#### Contributed by [Rinku Gupta](https://github.com/rinkug)

#### Publication date: Jan 10, 2020


Software has become important. Software practices are becoming more important. Scientists don’t have background and resources to it (brief para)
Many SPIs do not work for many reasons, mention a few reasons. We understand and  hence psips (brief para)
Advantages of psip
What is a psip framework (explain with figure)
Success stories of psip (brief para)
How to get more information on psips
References to other posts on psips


In the last two decades, software design and development has become an integral part of the daily research life of almost every scientist in any domain of scientific computing. Most popular research software, in all likelihood, started as a research project, gained traction and acceptance, and over time have become invaluable to the community. Product-oriented  software developed by the industry, on inception, do have focussed product specifications, software lifecycle, software longevity estimates, revenue estimates, trained teams and support plans charted out. Contrast this to research-developed software which follow a more ad-hoc style heavily dependent on vagaries of project funding, skilled personnel resource constraints, along with a forward-looking but ambiguously changing technological landscape. In such indeterministic environments, where the focus of scientists is to get the proposed software project up and going, devoting resources to software practices, eventual product sustainability, superior product quality or team productivity are often rendered to the second-class citizen bucket. 

Many domain scientists, especially on the application side, are experts in their chosen domain but may have modest formal software engineering training. They understand formal software engineering terminology but may have limited experience on how to apply it. While all scientists and researchers appreciate software improvement methodologies, they worry about significant delay to their current scientific activities or need of large investments before seeing benefits. Scientific software teams are typically focused on obtaining scientific results from the software they write. Funding is typically for generating results, not software. This is a competitive process and teams cannot usually expend much time or effort outside of writing the software features that support generating new results. Therefore, any productivity or sustainability improvements *must be incremental, iterative and integrated into the primary feature development process*. With this focus in mind, the *Productivity and Sustainability Improvement Planning (PSIP)* software process impovement (SPI) method was envisoned for scientific software teams.



### PSIP overview

### PSIP and FLASH

Rewrite...

While working on this effort, we were introduced to the [Productivity and Sustainability Improvement Planning](LINK) (PSIP) process, which is developed and promoted by the [IDEAS-ECP](https://ideas-productivity.org/) project.   PSIP is itself a work in progress that is becoming a useful methodology for improving productivity and software sustainability.  We now recognize that the fundamental philosophy of our process aligns well with that of PSIP – take stock of where the project is and make changes in small, well-planned, and manageable steps.  Because of this similarity, we are able to map retroactively our process for improving two development processes onto PSIP and discuss how we may have used PSIP to improve our productivity and the quality of our work.

### Refactoring and testing

The first improvement addressed the need to grow our test suite and to improve techniques for documenting how the test suite evolves in response to changes in the software.  This work has been retroactively represented by a PSIP [progress tracking card](https://github.com/betterscientificsoftware/PSIP-Tools/tree/master/PTCs) (PTC) for verification coverage and test-suite management, shown in Figure 1.  This work was linked to the effort to refactor the mesh management component of FLASH to work with AMReX, so that we could address perceived barriers to correctly and productively achieving this goal.  The need for this process improvement is best understood through explaining our plan of attack for the refactoring.

<br>

<img src='https://github.com/betterscientificsoftware/images/raw/master/Blog_082719_PSIPTestingCard.png' class='page lightbox'/>[Figure 1. A PSIP progress tracking card that represents the incremental steps used to improve our verification process.]

<br>

Our refactoring strategy relied on two team members carrying out simultaneous, incremental refactoring efforts with similar goals.  One person added in AMReX from the bottom up, while the other person undertook a top-down refactoring.  In the latter approach, the data structures for storing solution data were constructed with AMReX; but the original library, Paramesh, was used to drive the mesh refinement.  The first task in the PTC resulted in our understanding that the FLASH test suite had enough tests in place to verify the top-down modifications through simulation-level regression testing but was inadequate for the bottom-up part.  While some unit tests  already existed, they  did not provide sufficient coverage for our desired incremental modification approach. The reason was that the internal AMR features of AMReX are quite different from those of Paramesh, which was used to design the original tests.
We therefore used test-driven development to design and implement integration-level regression testing, where each new test covered a single aspect of the internal AMR functionality.

In addition to these changes to the test suite, we identified the need to improve our documentation of the setup of each execution environment used to run our test suite.  For example, we decided to maintain a history of which third-party libraries were installed, when, and why.  Also, we wanted to be able to trace the provenance of each baseline we establish for regression testing and needed to create a procedure for documenting how a baseline was verified both when created and when updated.

Since this refactoring was large and complicated, we appreciated the incremental nature of making improvements, which is in accord with the PSIP methodology.  For instance, as we were working on items 1 and 2, we could use the experience of writing more tests and adding these to the test suite to try out potential protocols for documenting the history of changes to baselines.  However, we did not feel pressured to work on item 5 until the refactoring effort was nearly finished and we had learned enough from these experiments.  While this approach meant that we might not record the full history of the test suite, the process allowed us to manage carefully the amount of work we were undertaking, as well as the complexity of the work, at any point in time.

### Git workflow

Because we decided to transition the management of our code to git, the second improvement related to designing and evolving a test-driven git workflow so that we could improve the collaboration that occurs when team members integrate work developed in parallel through a revision control system.  Rather than adopt a full-featured and possibly excessive workflow, we started simple and added capabilities as needed.  This incremental process has been retroactively represented by the PSIP progress tracking card (PTC) for git workflow shown in Figure 2.

<br>

<img src='https://github.com/betterscientificsoftware/images/raw/master/Blog_082719_PSIPGitCard.png' class='page lightbox' />[Figure 2. A PSIP progress tracking card that represents the process of designing, implementing, and improving our git workflow.]

<br>

To date, the code in the git repository is a small subset of the production version of FLASH. Although this relatively simple workflow has worked well so far, we have already identified an area where we would like improvement and where we can explicitly apply PSIP. This area is to *smoke test* changes made to the software in the repository with a continuous integration test server such as Travis CI. (*Smoke testing* is preliminary testing to reveal simple failures.) As more code components from the production version are transitioned to git and more users and contributors switch to the git version, we will be faced with many more challenges and the need for process improvements. While our development philosophy has always mirrored PSIP, the formalization brought by PSIP makes the philosophy explicit to new team members and external contributors. We foresee many instances of PSIP being used before the new version of FLASH is ready for production.
 
<!-- Replace using hyperlinked ref format
#### Citations
* Jared O'Neal, Anshu Dubey, & Klaus Weide. [Experience report: refactoring the mesh interface in FLASH, a multiphysics software](https://doi.org/10.1109/eScience.2018.00141). 2018 IEEE 14th International Conference on e-Science (e-Science). IEEE.
-->

### Author bios


<br>

[1]: #ref1 "Experience report: Refactoring the mesh interface in FLASH, a multiphysics software"

References | &nbsp;
:--- | :---
<a name="ref1"></a>1 | [Jared O'Neal, Anshu Dubey, and Klaus Weide. Experience report: Refactoring the mesh interface in FLASH, a multiphysics software. 2018 IEEE 14th International Conference on e-Science ](https://doi.org/10.1109/eScience.2018.00141)

<!---
Publish: yes
RSS update: 2019-08-27
Categories: planning, development, reliability
Topics: software process improvement, refactoring, testing
Tags: bssw-blog-article
Level: 2
Prerequisites: default
Aggregate: none
--->

