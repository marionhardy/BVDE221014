library(biomaRt)

## Annotations

listDatasets(useMart("ensembl"))

# Load mus musculus ensembl dataset

mart <- useDataset("hsapiens_gene_ensembl", useMart("ensembl"))

listAttributes(mart)

ensembl_to_geneName <- getBM(attributes = c("ensembl_gene_id",
                                            "ensembl_gene_id_version",
                                            "uniprot_gn_id",
                                            "uniprot_gn_symbol",
                                            "external_gene_name",
                                            "entrezgene_id","description"),
                             mart = mart)
names(ensembl_to_geneName) <- c("ensembl","ensembl_version", "protID" ,
                                "prot_name","gene", "ENTREZID", "description")
head(ensembl_to_geneName)
ensembl_to_geneName$gene = sub("^$", NA, ensembl_to_geneName$gene) 

## Run this script every six months to get updated gene annotations

saveRDS(ensembl_to_geneName,"./data/hsapiens_annotations_230510.rds")




