---
title: Lab Protocol for 515Y/926R universal primers
featured: true
authors:
- admin
date: 2019-07-29
---

We use a "DIY" protocol for preparing amplicons that produces high-quality, quantitative data. We use long primers with Illumina adapters already as part of the primer, meaning that there is no additional adapter ligation step. This ligation step might have some negative effect on the quantitative nature of the PCR assay but it also complicates sample preparation. The only downside of our way of doing things is you have to be really careful to note which forward and reverse primers correspond to which sample. After your PCR is completed, all you need to do is to cleanup with Ampure XP beads, quantify, and pool at equimolar concentrations.

The latest and greatest version of the protocol can be found here:

https://www.protocols.io/view/fuhrman-lab-515f-926r-16s-and-18s-rrna-gene-sequen-vb7e2rn

**Important Notes on Calculating Sequencing Depth**

Thank you to Liv for sharing her experience in this matter!

We normally sequence our cleaned amplicons on a 2x250 HiSeq RapidRun which gives us ~180 million reads. To provide the requisite "random" DNA that the sequencer needs, we pool our amplicons with metagenomes. The calculation for this pooling is somewhat counterintuitive, but this is how it has worked in the past:

1. Create pool that contains 75% amplicons by molarity; the remainder is metagenomes.
2. Put on sequencer, which yields 180 million reads on average.
3. For whatever reason, there is an approximate 3x bias against the amplicons, which means you get approximately 25% of the total 180 million reads back as amplicons, and 75% is the metagenome you added (why? Bob only knows...).
4. If you add approximately 280 amplicon samples, you will get on the order of 100,000 reads/sample (though there is considerable stochasticity in this number).
5. For our large size fraction (1.2 - 80uM), you can expect to get approximately 10,000 18S reads, 17,000 Chloroplast 16S and 73,000 other 16S (mostly Bacteria/Archaea but also including Mitochondria).