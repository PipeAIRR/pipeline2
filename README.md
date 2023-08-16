A pipeline for BCR repertoire libraries from the form of - Illumina MiSeq 2x250 BCR mRNA. that were produced in the same fashion as those in [Greiff et al. 2014](https://bmcimmunol.biomedcentral.com/articles/10.1186/s12865-014-0040-5)

Library preperation and sequencing method:

The sequences were amplified using specific primers of the C-region and non coding V region of the IGH chain. The generated libraries were then sequenced with Illumins MiSeq 2x250. 

Each 250 base-pair read was sequenced from one end of the target cDNA, so that the two reads together cover the entire variable region of the Ig heavy chain. The V(D)J reading frame proceeds from the start of read 2 to the start of read 1. Read 1 is in the opposite orientation (reverse complement), and contains the C-region primer sequence. Both reads begin with a random sequences of 4 nucleotides.


Input files:

1. Two fastq file of paird sequencing
2. primer files

To test the pipeline:

We recommend to test the pipeline using a small example from the original reads that can download using the fastq-dump command.

```bash
fastq-dump --split-files -X 25000 ERR346600
```

And upload directly to dolphinnext. 


Output files:

1. {sampleName}_collapse-unique.fastq
2. {sampleName}_atleast-2.fastq
3. log tab file for each steps
4. report for some of the steps


Pipeline container:

* Docker: immcantation/suite:4.3.0

Sequence processing steps:

* Paired-end assembly

	1. AssemblePairs

* Quality control and primer annotation

	2. FilterSeq
	3. MaskPrimer


* Deduplication and filtering

	4. CollapseSeq
	5. SplitSeq



Primers used:

* [Greiff2014_CPrimers (R1)](https://bitbucket.org/kleinstein/presto/src/master/examples/Greiff2014/Greiff2014_CPrimers.fasta)


* [Greiff2014_VPrimers (R2)](https://bitbucket.org/kleinstein/presto/src/master/examples/Greiff2014/Greiff2014_VPrimers.fasta)

