CTTV 24 Project
===============

Copyright holder: [EMBL-European Bioinformatics Institute](http://www.ebi.ac.uk) (Apache 2 License)

This script is designed to automatically finemap and highlight the causal variants behind GWAS results by cross-examining GWAS, population genetic, epigenetic and cis-regulatory datasets.

Its original design was based on STOPGAP. 

Installing
----------

Add the ```lib/``` directory to your ```$PYTHONPATH``` environment variable.

Installing dependencies
-----------------------

To install all dependencies run ```sh install_dependencies.sh```

Add the ```bin``` directory to your ```$PATH``` environment variable.

Dataset Preprocessing
---------------------

* Via the FTP site (*recommended*)

  Download all the files on the OpenTargets FTP site (URL TBD)

  Note that the FTP download may mess up your timestamps, so you should run ```make tabix``` to ensure the tabix indices are more recent than the corresponding bed.gz files.

* Manually (*sloooow*)
  1. Type ```make download``` to download public databases.
  2. Type ```make process``` to preprocess the databases. **Warning** this may take days as it needs to split the entire 1000 Genomes files by population.

Running
-------

By default, run from the root directory the command: 

```
python scripts/POSTGAP.py --disease autism  
```

Multiple disease names can be provided.

Testing
-------

```
cat scripts/testing/all_efos.txt | xargs -n1 python scripts/POSTGAP.py --efos > table.tsv
```

