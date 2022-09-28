# gcloud snippets

This document contains some nice bit and pieces of `gcloud`, the GCP command line tool

## VMs

View available images from a project.  A project is usually consists of a publisher and product.  In this case SUSE is the publisher and SLES for SAP is the product.

```shell
% gcloud compute images list --project suse-sap-cloud --no-standard-images
NAME                              PROJECT         FAMILY           DEPRECATED  STATUS
sles-12-sp4-sap-v20220714-x86-64  suse-sap-cloud  sles-12-sp4-sap              READY
sles-12-sp5-sap-v20220714-x86-64  suse-sap-cloud  sles-12-sp5-sap              READY
sles-15-sp1-sap-v20220716-x86-64  suse-sap-cloud  sles-15-sp1-sap              READY
sles-15-sp2-sap-v20220718-x86-64  suse-sap-cloud  sles-15-sp2-sap              READY
sles-15-sp3-sap-v20220719-x86-64  suse-sap-cloud  sles-15-sp3-sap              READY
sles-15-sp4-sap-v20220722-x86-64  suse-sap-cloud  sles-15-sp4-sap              READY
```
