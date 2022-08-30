Data acquisition - Chlorophyta genomes
================

# codingsequences.rda

The object `codingsequences.rda` contains the coding sequences of primary
transcripts for each species, and it was obtained with the following
code:

``` r
#----Get coding sequences--------------------------------------------------
cds_urls <- c(
    Aprotothecoides = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.apr.fasta.gz",
    Helicosporidiumsp = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.hsp.fasta.gz",
    Chlorellasp = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.cnc64a.fasta.gz",
    PicRCC4223 = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.prcc4223.fasta.gz",
    PicSE3 = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.pse3.fasta.gz",
    Asterochlorissp = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.acg.fasta.gz",
    Csubellipsoidea = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.cvu.fasta.gz",
    Creinhardtii = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.cre.fasta.gz",
    Vcarteri = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.vca.fasta.gz",
    Bprasinos = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.bprrcc1105.fasta.gz",
    Otauri = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.ota.fasta.gz",
    Osp = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.orcc809.fasta.gz",
    Olucimarinus = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.olu.fasta.gz",
    Omediterraneus = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.ome.fasta.gz",
    Msp = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.mrcc299.fasta.gz",
    Mpusilla = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.mpu.fasta.gz",
    Ppatens = "ftp://ftp.psb.ugent.be/pub/plaza/plaza_pico_03/Fasta/cds.selected_transcript.ppa.fasta.gz"
)

## Headers in .fa files have protein IDs. Read proteomes and keep only gene IDs
codingsequences <- lapply(cds_urls, function(x) {
    seq <- Biostrings::readDNAStringSet(x)
    names(seq) <- gsub(".* \\| ", "", names(seq))
    return(seq)
})
save(
    codingsequences, 
    file = here::here("data", "codingsequences.rda"),
    compress = "xz"
)
```
