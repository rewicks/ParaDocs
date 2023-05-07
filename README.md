# ParaDocs

ParaDocs is an effort to produce more document-level parallel data for the field of Machine Translation. [ParaCrawl](https://www.paracrawl.eu/) is a large central effort towards extracting bitext from crawled web data for European languages.

The general pipeline for ParaCrawl extraction is:

1) Mining web data (or using publicly mined data)

2) Aligning (language-identified) documents within domains. These domains are typically targeted because they produce parallel documents.

3) Aligning sentences from the aligned documents.

4) From here, much of the data is discarded because of it's bad quality. Further filtering steps on the sentence-level alignments may take the form of:
    
    a.  Deduplication

    b.  Eliminating low-similarity pairs

    c.  Further language identification filterning

During the above, much of the document-level meta data is loss. 

In June 2022, ParaCrawl released a percentage of their [monolingual data](https://www.paracrawl.eu/moredata). We use this data in order to sections of the original documents, by looking for consecutive sentences that have survived previous filtering efforts.

Further, we provide


