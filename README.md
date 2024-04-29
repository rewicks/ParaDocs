# Quick Use

There are two scripts. One to download and filter from huggingface (`paradocs-hf`) and one to filter from an already downloaded file (`paradocs`) (this may be faster than using huggingface).

They both have the same general usage:

```
usage: paradocs [-h] [--NAME NAME] [OPTIONS]

ParaDocs: Extracts document-level information from RAW ParaCrawl data and filters output for easy bitext extraction.
      Example: paradocs --path en-de-strict.gz

options:
  -h, --help            show this help message and exit
  --path PATH           The path to the data
  --minimum_size MINIMUM_SIZE
                        The minimum consecutive sequence length to include in the output. By default, set to 1 (all sentences included)
  --frequency_cutoff FREQUENCY_CUTOFF
                        Will break documents at any line that occurs above this frequency in the original data. This is an alternative to sentence-level deduping.
  --lid_cutoff LID_CUTOFF
                        Will break documents at any line that occurs below this probability for the assigned language.
  --min_avg_score MIN_AVG_SCORE
                        To print out a document, the whole document must maintain an average score across the whole document.
  --outpath OUTPATH     The output path to write the data. If not set, defaults to sys.stdout
```

Alternatively to use `paradocs-hf`, you can substitute `--path` for `--name` and pass the name of a data split.

