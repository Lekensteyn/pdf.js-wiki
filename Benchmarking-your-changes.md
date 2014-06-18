When working on issues related to performance, it is important to provide a performance benchmark for your changes to assess whether or not your change has a performance impact. PDF.js provides tools to do this easily. Normally you would create a simple manifest file has couple of pdfs you trying to optimize and run it multiple times, e.g. `my_pdfs.json`:

```
[
    {  "id": "tracemonkey-eq",
       "file": "pdfs/tracemonkey.pdf",
       "md5": "9a192d8b1a7dc652a19835f6f08098bd",
       "rounds": 20,
       "lastPage": 5,
       "type": "load"
    }
]
```

Run the following command to create a 'baseline' measurement (before you make your changes):

    $ cd test
    $ node test.js --browserManifestFile=resources/browser_manifests/browser_manifest.json \
        --statsFile=stats/results/baseline.json --statsDelay=5000 \
        --manifestFile=my_pdfs.json

Then apply your changes and create a 'current' measurement:

    $ node test.js --browserManifestFile=resources/browser_manifests/browser_manifest.json \
        --statsFile=stats/results/current.json --statsDelay=5000 \
        --manifestFile=my_pdfs.json

Now you can compare the measurements and see any performance differences:

    node stats/statcmp.js stats/results/baseline.json stats/results/current.json

As a sanity check, you should do this twice with the same code and compare the results.