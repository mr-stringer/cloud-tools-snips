# az snippets

This document contains some nice bit and pieces of `az`, the Azure command line tool

## VMs

View all VMs available in a regions that and filter on CPU and memory requirements.  Here we set various filters and decide what we want to see in the output.

```shell
% az vm list-sizes --location uksouth --query "[?numberOfCores ==\`2\` && memoryInMb <=\`8192\`  && memoryInMb >=\`4096\`].{Name:name,  Cores:numberOfCores, MemoryMiB:memoryInMb}" --output table
Name                   Cores    MemoryMiB
---------------------  -------  -----------
Standard_B2ms          2        8192
Standard_B2s           2        4096
...
```

View available images from a publisher.  -p specifies the publisher and -l specifies the azure region.  It produces a long list.  All of the data in the Urn column is required in terraform for the image selection.

```shell
% az vm image list -p SUSE -l uksouth --all --output table 
Offer                     Publisher    Sku          Urn                                            Version
------------------------  -----------  -----------  ---------------------------------------------  ----------
cap-deploy-byos           SUSE         gen2         SUSE:cap-deploy-byos:gen2:2020.06.26           2020.06.26
cap-deploy-byos           SUSE         gen2         SUSE:cap-deploy-byos:gen2:2020.12.04           2020.12.04
manager-proxy-4-1-byos    SUSE         gen1         SUSE:manager-proxy-4-1-byos:gen1:2021.12.09    2021.12.09
manager-proxy-4-1-byos    SUSE         gen1         SUSE:manager-proxy-4-1-byos:gen1:2022.01.27    2022.01.27
manager-proxy-4-1-byos    SUSE         gen1         SUSE:manager-proxy-4-1-byos:gen1:2022.03.08    2022.03.08
manager-proxy-4-1-byos    SUSE         gen1         SUSE:manager-proxy-4-1-byos:gen1:2022.04.08    2022.04.08
manager-proxy-4-1-byos    SUSE         gen2         SUSE:manager-proxy-4-1-byos:gen2:2021.12.09    2021.12.09
...
```

View available VMs sizes in a region. -l specifies the region

```shell
% az vm list-sizes -l francecentral -o table
MaxDataDiskCount    MemoryInMb    Name                      NumberOfCores    OsDiskSizeInMb    ResourceDiskSizeInMb
------------------  ------------  ------------------------  ---------------  ----------------  ----------------------
4                   8192          Standard_D2a_v4           2                1047552           51200
8                   16384         Standard_D4a_v4           4                1047552           102400
16                  32768         Standard_D8a_v4           8                1047552           204800
32                  65536         Standard_D16a_v4          16               1047552           409600
32                  131072        Standard_D32a_v4          32               1047552           819200
32                  196608        Standard_D48a_v4          48               1047552           1228800
32                  262144        Standard_D64a_v4          64               1047552           1638400
...
```

