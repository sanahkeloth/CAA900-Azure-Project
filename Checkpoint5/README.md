# Checkpoint4 Submission

- **COURSE INFORMATION: CAA900 - Capstone Project**
- **STUDENT’S NAME: Sanah Hussain Edavalath Vayalil Keloth**
- **STUDENT'S NUMBER: 160683231**
- **GITHUB USER ID: 160683231-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

### Table of Contents

1. [Part A - Creating & Configuring VMs - Using Portal](#part-a---creating--configuring-vms---using-portal)
2. [Part B - Basic Connectivity - VM Configuration](#part-b---basic-connectivity---vm-configuration)
3. [Part C - Enable IP_Forwarding - Using Portal](#part-c---enable-ip_forwarding---using-portal)
4. [Part D - Creating & Configuring VM Images - Using Portal](#part-d---creating--configuring-vm-images---using-portal)
5. [Part E - Azure Cost Analysis Charts](#part-e---azure-cost-analysis-charts)
6. [Part F - Create Customized Azure Dashboard](#part-f---create-customized-azure-dashboard)

## Part A - Creating & Configuring VMs - Using Portal

`az group list -o table`
```
Name                Location    Status
------------------  ----------  ---------
Bastion_RG          canadaeast  Succeeded
NetworkWatcherRG    canadaeast  Succeeded
Student-RG-1202091  canadaeast  Succeeded
```

`RG="Student-RG-1202091"`

`az vm list -g $RG -o table`
```
Name    ResourceGroup       Location    Zones
------  ------------------  ----------  -------
LR-45   Student-RG-1202091  canadaeast
LS-45   Student-RG-1202091  canadaeast
WC-45   Student-RG-1202091  canadaeast
WS-45   Student-RG-1202091  canadaeast
```

`az network nic list -g $RG -o table`
```
AuxiliaryMode    AuxiliarySku    DisableTcpStateTracking    EnableAcceleratedNetworking    EnableIPForwarding    Location    MacAddress         Name      NicType    Primary    ProvisioningState    ResourceGroup       ResourceGuid                          VnetEncryptionSupported
---------------  --------------  -------------------------  -----------------------------  --------------------  ----------  -----------------  --------  ---------  ---------  -------------------  ------------------  ------------------------------------  -------------------------
None             None            False                      False                          False                 canadaeast  00-0D-3A-F4-74-61  lr-45212  Standard   True       Succeeded            Student-RG-1202091  73519d4c-93dc-44d9-805b-6ec55f51418a  False
None             None            False                      False                          False                 canadaeast  00-0D-3A-F4-DF-F4  ls-45582  Standard   True       Succeeded            Student-RG-1202091  8b8bc043-f793-464b-8ceb-74d5ac3fadbc  False
None             None            False                      False                          False                 canadaeast  00-22-48-6E-17-02  wc-45852  Standard   True       Succeeded            Student-RG-1202091  f12f6e56-8f19-4929-ad67-0a85d50c5a14  False
None             None            False                      False                          False                 canadaeast  60-45-BD-F9-AE-91  ws-457    Standard   True       Succeeded            Student-RG-1202091  c5ddb9d4-c64e-4031-8346-a9f6ac802640  False
```

`az network nsg list -g $RG -o table`
```
Location    Name       ProvisioningState    ResourceGroup       ResourceGuid
----------  ---------  -------------------  ------------------  ------------------------------------
canadaeast  LR-45-nsg  Succeeded            Student-RG-1202091  cc778bab-c3ab-4fe8-a0b0-4da834e03dff
canadaeast  LS-45-nsg  Succeeded            Student-RG-1202091  e85b254b-ad6e-4181-b95c-206a47a7c5dc
canadaeast  WC-45-nsg  Succeeded            Student-RG-1202091  95570f1f-f32f-41f0-8ac3-42ebc0c3120c
canadaeast  WS-45-nsg  Succeeded            Student-RG-1202091  dafacb9a-8c49-48f7-9c39-1ae5b64faf96
```

`az disk list -g $RG -o table`
```
Name                                             ResourceGroup       Location    Zones    Sku           OsType    SizeGb    ProvisioningState
-----------------------------------------------  ------------------  ----------  -------  ------------  --------  --------  -------------------
LR-45_OsDisk_1_3ca8d8cd40004bc382545c69f69825a4  Student-RG-1202091  canadaeast           Standard_LRS  Linux     64        Succeeded
LS-45_OsDisk_1_e67eee0cf3894efdbd184681fc85211c  Student-RG-1202091  canadaeast           Standard_LRS  Linux     64        Succeeded
WC-45_disk1_4a02b46b20ab484c9f88e360adecacf3     Student-RG-1202091  canadaeast           Standard_LRS  Windows   127       Succeeded
WS-45_OsDisk_1_339385eca1e14170aee7d2238d7fe83b  Student-RG-1202091  canadaeast           Standard_LRS  Windows   127       Succeeded
```

## Part B - Basic Connectivity - VM Configuration

`az network nic show -g $RG -n lr-45212 --query "enableIPForwarding"`
```
true
```



## Part C - Enable IP_Forwarding - Using Portal

```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)                                                                                                                                            
num   pkts bytes target     prot opt in     out     source               destination                                                                                                      
1     4329   52M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED, ESTABLISHED                                                                   
2        0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                        
3        0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0                                                                                                        
4        0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW tcp dpt:22                                                                        
5       14  1534 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited                                                                                                                                                                                                                                                      

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)                                                                                                                                          
num   pkts bytes target     prot opt in     out     source               destination                                                                                                      
1        0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited                                                                                                                                                                                                                                                      

Chain OUTPUT (policy ACCEPT 4458 packets, 807K bytes)                                                                                                                                     
num   pkts bytes target     prot opt in     out     source               destination     
```

`hostname`
```
LS-45.CAA9002241.com
```

## Part D - Creating & Configuring VM Images - Using Portal

1. Run a command in CLI that lists all your Custom Images. Hint: `az image list ...`. Change the output format to table format and embed the answer in your submission.

`az image list -g STUDENT-RG-1202091 -o table`
```
HyperVGeneration    Location    Name             ProvisioningState    ResourceGroup
------------------  ----------  ---------------  -------------------  ------------------
V2                  canadaeast  LR-45-ver-0.0.1  Succeeded            STUDENT-RG-1202091
V2                  canadaeast  LS-45-ver-0.0.1  Succeeded            STUDENT-RG-1202091
V2                  canadaeast  WC-45-ver-0.0.1  Succeeded            STUDENT-RG-1202091
V2                  canadaeast  WS-45-ver-0.0.1  Succeeded            STUDENT-RG-1202091
```

2. Delete your VMs after your work is completed. Run a command in CLI that lists all your VMs. Hint: `az vm list ...`. Change the output format to table format and embed the answer in your submission.

`az vm list -g STUDENT-RG-1202091 -o table`

There is no output, because all vms were deleted after the images were captured.

3. Recreate all VMs from your images, and establish basic connectivity. How long the entire process took? How can you do this more efficiently?

It took about 20 min for the whole process. Perhaps, it would be better to automate the log in and execution of terminal commands using scripts.

## Part E - Azure Cost Analysis Charts

**Azure Cost Analysis Charts**

| No. | Scope | Chart Type | VIEW Type |  Date Range | Group By | Granularity| Chart |
|-|-|-|-|-|-|-|-|
|1|STUDENT-RG-1202091| Column (Stacked) | DailyCosts | Last 7 Days | Resource | Daily | <img src="./images/daily-cost-barchart.png" alt="Daily Cost Barchart" style="float: left; margin-right: 10px;" /> |
|2|STUDENT-RG-1202091| Column (Stacked) | DailyCosts | Last 7 Days | Service | Daily | <img src="./images/daily-cost-service-barchart.png" alt="Daily Cost Service-Barchart.png" style="float: left; margin-right: 10px;" /> |
|3|STUDENT-RG-1202091| Area| AccumulatedCosts | Last 7 Days | Resource | Accumulated | <img src="./images/accumulated-resource-area.png" alt="Accumulated Resource Barchart" style="float: left; margin-right: 10px;" /> |
|4|STUDENT-RG-1202091| Pie Chart | NA | Last Month | Service Name | NA | <img src="./images/service-name-piechart.png" alt="Service Name Piechart" style="float: left; margin-right: 10px;" /> |
|5|STUDENT-RG-1202091| Pie Chart | NA | Last Month | Service Family | NA | <img src="./images/service-family-piechart.png" alt="Service Family Piechart" style="float: left; margin-right: 10px;" /> |
|6|STUDENT-RG-1202091| Pie Chart | NA | Last Month | Product | NA | <img src="./images/product-piechart.png" alt="Product Piechart" style="float: left; margin-right: 10px;" /> |


## Part F - Create Customized Azure Dashboard

**Azure Cost Analysis Dashboard**

![Cost Analysis Dashboard](./images/cost-analysis-dashboard.png)
