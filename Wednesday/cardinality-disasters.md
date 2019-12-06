# The Great Cardinality Disasters of Our Time:

*Speaker: Bryan Borham, Weaveworks & Chris Marchbanks, Splunk*

* Labels can cause issues if not utilized properly
    * don’t put raw messages in them
    * use relabeling rules
* Buckets used to scale linearly, not anymore now. 
* Browser/Grafana broke b/c it was pulling back every metric name for autocomplete which was too large of a query 
    * again use relabeling rules!

