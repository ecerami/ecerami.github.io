--- 
layout: post 
title: IntOGen - Interview with Nuria Lopez-Bigas
---

This week marks a slightly different direction for biobits.org.  For some time, I have been thinking of interviewing practitioners in the world of cancer genomics, and getting their perspectives.


<div class="sidebar-left">
	<p><b>Recommended Reading:</b>
	<p>
		<ul>
			<li>David Tamborero, et al., <a href="http://www.nature.com/srep/2013/131002/srep02650/full/srep02650.html">Comprehensive identification of mutational cancer driver genes across 12 tumor types.</a> Scientific Reports, 2013.</li>
			<li>Gonzalez-Perez A, et al., <a href="http://www.nature.com/nmeth/journal/vaop/ncurrent/full/nmeth.2642.html">IntOGen-mutations identifies cancer drivers across tumor types</a>.  Nature Methods, 2013.</li>
			<li>Tamborero D, et al., <a href="http://bioinformatics.oxfordjournals.org/content/29/18/2238.long">OncodriveCLUST: exploiting the positional clustering of somatic mutations to identify cancer genes</a>.  Bioinformatics. 2013.</li>
			<li>Abel Gonzalez-Perez, et al., <a href="http://nar.oxfordjournals.org/content/40/21/e169.full?keytype=ref&ijkey=jWx48Ab6s74fm7I">Functional impact bias reveals cancer drivers</a>.  Nucleic Acids Research, 2012.</li>
		</ul>
</div>

The first installment is an interview with <a href="http://bg.upf.edu/group/people/people.nuria.php">Nuria Lopez-Bigas</a>, from the <a href="http://bg.upf.edu/group/index.php">Biomedical Genomics group</a> at the <a href="http://www.upf.edu/">University Pompeu Fabra</a> in Barcelona (her group also maintains a nice <a href="http://bg.upf.edu/blog/">Blog</a>).

I talked with Nuria about her recent work in building <a href="http://www.intogen.org/">IntOGen</a> (Integrative OncoGenenomics), which was recently published in <a href="http://www.nature.com/nmeth/journal/vaop/ncurrent/full/nmeth.2642.html">Nature Methods</a>.

**What motivated you to build IntOGen in the first place?  What specific problem were you trying to solve?**

**NLB**:  Numerous independent projects are re-sequencing cohorts of tumor genomes and identifying the mutations found on them, including projects from the TCGA, ICGC, as well as independent initiatives not linked to any of these consortia. Each of the projects report their list of cancer drivers identified with differing criteria and methodologies, which makes difficult to have a complete view of which genes are drivers in each cancer type. Thus, we decided to develop a system dedicated to analyze in a systematic manner all tumor cohort genome/exome sequencing project. With this we are now able to have a comprehensive view of cancer vulnerabilities across cancer types, which was not possible before.

We designed the IntOGen-mutations to be updated regularly and to be scalable to the analysis of much larger number of tumors, so that we can keep up with the expected increase in sequenced tumor genomes/exomes. Thus in each update we will obtain a more complete view of cancer drivers across tumor types.

**Most methods identify "driver" genes based on mutation recurrence (above background).  What do you think is potentially missed by such methods, and how are the methods integrated into IntOGen different?**

**NLB:**  Driver genes by definition bear certain mutations that provide a selective advantage to tumor cells. Thus, we can find them by searching signals of positive selection in a cohort of tumors. Mutation recurrence is the most intuitive signal that we can think of and has been the most used approach to identify drivers (eg. MutSigCV, MuSiC). The biggest challenge of any of these approaches is to correctly estimate the background mutation rate, which we now know that is variable across the genome and in different cells.

Instead of using mutation recurrence measurements, our methods detect other signals of positive selection. For instance, OncodriveFM detect genes in which observed mutations in tumors are biased towards high functionally impacting mutations. One important advantage of this method is that it does not depend on the background mutation rate. OncodriveCLUST, on the other hand, detects genes in which mutations are clustered in certain protein regions. An important feature of our methods is that they only require the list of somatic mutations as input and they are computationally unexpensive, both of which are important features when analyzing large cohorts of tumors like we do in IntOGen-mutations.

As part of the IntOGen-mutations paper we did a comparison of the genes reported as drivers in the original publications describing the dataset (which used MutSig or MuSic) and those identified by the methods included in IntOGen-mutations pipeline. We find that in general there is a very high overlap, with some known cancer driver genes identified exclusively by IntOGen-mutations (described in Supplementary Note 1 of the manuscript).

When possible though, I would recommend to use several methods and consider the results of each of those in the final decision of which genes are drivers.

**Can you give us an example of a gene that you identified via OncodriveFM or OncodriveCLUST that was missed by other methods?  What is the significance of the finding?**

One interesting example is ASXL1 (additional sex combs like 1) that belongs to the Enhancer of trithorax and Polycomb gene family. This gene is mutated in only 5 AML samples out of 196 samples analyzed by TCGA (<a href="http://www.ncbi.nlm.nih.gov/pubmed/23634996">TCGA Network N Engl J Med. 2013</a>) and was missed by MuSiC, however OncodriveFM detects it as a driver as it has a clear FMbias: the 5 mutations are severely affecting the function of the protein. GATA2 and NF1 are other genes missed by MuSiC and detected by OncodriveFM in the AML dataset, both are mutated in only 2 AML samples, but those are mutations with a high functional impact.

One interesting example for OncodriveCLUST is PRKCZ (Protein kinase C zeta), which is a member of the PKC family of serine/threonine kinases involved in cell proliferation, NF-kappa-B activation and mitogenic signaling. This gene is mutated in 3 out of 103 breast cancer samples from (<a href="http://www.ncbi.nlm.nih.gov/pubmed/22722202">Banerji et al Nature 2012</a>) and was not detected by MutSig. OncodriveCLUST, on the other hand, identifies it as a driver because the three samples have mutations in exactly the same protein position.

**What are your future plans for IntOGen?**

The most immediate plan is to keep regular updates of the data in IntOGen-mutations. Currently, we are getting ready for the next release, which includes 6346 tumors covering 46 projects and 15 cancer sites.  Future plans also include implementing other analytical methods in IntOGen-mutations pipeline (in addition to OncodriveFM and OncodriveCLUST) and enriching the database with Drug-Gene Interaction information.

**What is the most interesting cancer genomics paper you have read this year and why?**

I enjoyed reading the set of pan-cancer papers published this year, and I found particularly interesting the manuscript by <a href="http://www.nature.com/nature/journal/vaop/ncurrent/full/nature12477.html">Alexandrov et al., Nature 2013</a>, in which they analyse the mutations observed in about 7000 tumors and identify 20 mutational signatures, some present across cancer types and others more specific of particular cancer types.

**Is your lab really on the beach?**

Yes it is, if you visit Barcelona, let me know and I will show you.