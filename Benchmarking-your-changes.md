When working on issues related to performance, it is important to provide a performance benchmark for your changes to assess whether or not your change has a performance impact. PDF.js provides tools to do this easily.

Run the following command to create a 'baseline' measurement (before you make your changes):

    cd test
    node test.js --browserManifestFile=resources/browser_manifests/browser_manifest.json --statsFile=stats/results/baseline.json

Then apply your changes and create a 'current' measurement:

    node test.js --browserManifestFile=resources/browser_manifests/browser_manifest.json --statsFile=stats/results/current.json

Now you can compare the measurements and see any performance differences:

    node stats/statcmp.js stats/results/baseline.json stats/results/current.json

As a sanity check, you should do this twice with the same code and compare the results.