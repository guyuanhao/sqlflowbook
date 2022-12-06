# FAQ

## Frequently Asked Questions

This page contains some frenquently asked questions. You can also check the details response under the subpages.

### Q1: How to deal with internal database?

If your database is deployed in an internal network which is not accessable for external connection request, you can:

1. Use [sqlflow-ingester](../../6.-sqlflow-ingester/introduction/README.md) to export the database metadata file.
2. Create sqlflow job by [uploading that metadata file on our SQLFlow UI](../../1.-introduction/ui/job-management/job-sources.md#upload-file).&#x20;
3. Use [SQLFlow on-premise](../../1.-introduction/readme/cloud-and-on-premise-version.md#install-a-sqlflow-on-premise-version-on-your-own-server) version.

Check [deal with internal database](handling-internal-database.md) for more details.

### Q2: Can I delete my account?

Yes, you can delete your account. Check [here](delete-your-account.md) for how to do that.

**Note: your data will be deleted with your account together**

### Q3: How to output only the relationships in a table form without temporary intermediates, just column to column relationships between tables?

You can archive this using one of the following two approaches:

* If you are using SQLFlow UI, change the SQLFlow UI settings and download the data lineage as CSV.
* You can make REST api request to get the desired CSV data.

Check [Table Form Data Without Intermediates](table-form-data-without-intermediates.md) to get more details.