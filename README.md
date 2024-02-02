# ParaDocs

ParaDocs is an effort to produce more document-level parallel data for the field of Machine Translation. [ParaCrawl](https://www.paracrawl.eu/) is a large central effort towards extracting bitext from crawled web data for European languages.

The general pipeline for ParaCrawl extraction is:

1) Mining web data (or using publicly mined data)

2) Aligning (language-identified) documents within domains. These domains are typically targeted because they produce parallel documents.

3) Aligning sentences from the aligned documents.

4) From here, much of the data is discarded because of its bad quality. Further filtering steps on the sentence-level alignments may take the form of:
    
    a.  Deduplication

    b.  Eliminating low-similarity pairs

    c.  Further language identification filtering

During the above, much of the document-level meta data is loss. 

In June 2022, ParaCrawl released a percentage of their [monolingual data](https://www.paracrawl.eu/moredata). We use this data in order to sections of the original documents, by looking for consecutive sentences that have survived previous filtering efforts.

Further, we provide some suggestions towards _document-level filtering_ which leverages larger contexts in order to determine whether an entire document is high enough quality for downstream use.


## Script Use ##

The script requires that you have two files.

1. The ParaCrawl RAW file for your language pair. This is available on the ParaCrawl homepage by selecting the down arrow next to the TXT version and selecting RAW. These are significantly larger than the TXT files and have `classified` in the file name.
2. The ParaDocs META file for your language pair. Released later.

To extract data, you can point the paradocs scripts to these files.

### Quick start

```
paradocs --raw_path en-de.classified.gz \
            --metadata_path en-de.meta.gz 
```

will extract a reasonable starting place for bitext.

### Extended Use

```
ParaDocs: Extracts document-level information from RAW ParaCrawl data and filters output for easy bitext extraction.
      Example: paradocs --raw_path en-de.gz --metadata_path en-de.meta.gz --echo src,tgt,docid+sub

options:
  -h, --help            show this help message and exit
  --raw_path RAW_PATH   The path to the original paracrawl .gz file (from the RAW version)
  --metadata_path METADATA_PATH
                        The path to the metadata .gz file provided by ParaDocs
  --minimum_size MINIMUM_SIZE
                        The minimum consecutive sequence length to include in the output. By default, set to 1 (all sentences included)
  --frequency_cutoff FREQUENCY_CUTOFF
                        Will break documents at any line that occurs above this frequency in the original data. This is an alternative to sentence-level deduping.
  --outpath OUTPATH     The output path to write the data. If not set, defaults to sys.stdout
  --echo ECHO           What to print. Available keys are:
                            - src : original source sentence
                            - tgt : original target sentence
                            - srcurl : source urls
                            - tgturl : target urls
                            - docid : numerical id for documents
                            - subdocid : subdocument id (keeps track of breaking documents)
                            - docid+sub: the document id and subdocument id concatenated with a '+' in a single column
                            - collection : original source of data (based on paracrawl divisions)
                            - src_p : source paragraph ids
                            - tgt_p : target paragraph ids
                            - src_s : source sentence ids
                            - tgt_s : target sentence ids
                            - src_idx : the start and stop index for source character strings
                            - tgt_idx : the start and stop index for target character strings

```

