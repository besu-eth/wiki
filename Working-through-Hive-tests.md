

* Where is the dashboard? https://hive.ethpandaops.io/ - note dashboards are being actively improved so things may move around
* How to run the tests locally - [here](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22156302/Using+Hive+Test+Suite)
* If you have questions on the tests themselves? You can post in `el-testing` channel in Eth R&D discord
* Analysis of current failures - Currently using this [spreadsheet](https://docs.google.com/spreadsheets/d/1UkIJ9Sgj_Bd4AfjSUOmIIq-t2rfzHUbBDSQR_3glEuw/edit?gid=0#gid=0) (public) for the `rpc-compat` failures
* Often there will be several tests failing with the same root cause
* For `rpc-compat` there's a handful of causes of the failing tests - I colour-coded the spreadsheet :rainbow:
* Also can be useful to look at the dashboard to see if other clients are passing or failing the specific tests. Sometimes the tests are wrong!
* If there are a number of root causes, you could create issues in github so that the work can be broken up. Maybe there's some `good first issues`
