HITdb - Human Intestinal 16S rRNA gene reference taxonomy 
=========================================================

Ritari J, Salojärvi J, Lahti L & de Vos WM. Improved taxonomic assignment of human intestinal 16S rRNA sequences by a dedicated reference database. Submitted Manuscript.


## Files 

HITdb v1.00 contains HITdb 16S rRNA gene sequences in fasta format (HITdb_sequences.fna) and associated taxonomy text files in Qiime (HITdb_taxonomy_qiime.txt) and Mothur (HITdb_taxonomy_mothur.txt) formats.


## Notes

RDP or Mothur naïve Bayesian classifiers are recommended to be used with HITdb.

The HITdb taxonomy has six levels (Phylum, Class, Order, Family, Genus, Species) in order to make it compatible with Qiime analysis pipeline, in particular the summarize_taxa_through_plots.py script which outputs 6 levels of taxonomy.

Each OTU in HITdb has its nearest cultivable species determined based global sequence similarity. The "NN=" in OTU name indicates the nearest cultivable neighbour, and "D=" indicates the sequence similarity. 

In Qiime, the following scripts can be employed to assign taxonomy to OTUs using HITdb with RDP as the assigner algorithm:

``` python
# taxonomy assignment
assign_taxonomy.py -i $PWD/otus/rep_set/seqs_rep_set.fasta -t $PWD/HITdb_taxonomy_qiime.txt -r $PWD/HITdb_sequences.fna -m rdp -o hitdb_taxonomy

# generating OTU table
make_otu_table.py -i $PWD/otus/uclust_picked_otus/seqs_otus.txt -t $PWD/hitdb_taxonomy/seqs_rep_set_tax_assignments.txt -o hitdb_otutable.biom

# output in tab and biom formats
summarize_taxa_through_plots.py -i hitdb_otutable.biom -m mapping.txt -o hitdb_taxa_summary
```

## Version history

v. 1.00, 5 March 2015

First released version
