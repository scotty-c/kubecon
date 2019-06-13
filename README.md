# KubeCon China 2019 Demo

In this demo we are going to run a [Kubernetes](https://kubernetes.io/) cluster on [Azure](https://cda.ms/XK) with [virtual node](https://cda.ms/XL) enabled.  
Virtual node is based of the open source project [Virtual Kubelet](https://cda.ms/XM)

## Prerequisites

For the environment to build you will need the following software installed
- [Azure cli](https://cda.ms/XN)
- [Helm](https://helm.sh/)
- [Porter](https://porter.sh/)
- [Docker](https://www.docker.com/)
- [Kubectx](https://github.com/ahmetb/kubectx)
- [Jq](https://stedolan.github.io/jq/)

# Set up your cluster
To set up your cluster just run the script `setup.sh`       
The script will as you two questions 
```
Enter the subscription to use:
Enter region to deploy the cluster:
```
The subscription to use to connect to Azure with

If you are not sure regions are available you can find the out with the following 
```
$ az account list-locations -o table
DisplayName          Latitude    Longitude    Name
-------------------  ----------  -----------  ------------------
East Asia            22.267      114.188      eastasia
Southeast Asia       1.283       103.833      southeastasia
Central US           41.5908     -93.6208     centralus
East US              37.3719     -79.8164     eastus
East US 2            36.6681     -78.3889     eastus2
West US              37.783      -122.417     westus
North Central US     41.8819     -87.6278     northcentralus
South Central US     29.4167     -98.5        southcentralus
North Europe         53.3478     -6.2597      northeurope
West Europe          52.3667     4.9          westeurope
Japan West           34.6939     135.5022     japanwest
Japan East           35.68       139.77       japaneast
Brazil South         -23.55      -46.633      brazilsouth
Australia East       -33.86      151.2094     australiaeast
Australia Southeast  -37.8136    144.9631     australiasoutheast
South India          12.9822     80.1636      southindia
Central India        18.5822     73.9197      centralindia
West India           19.088      72.868       westindia
Canada Central       43.653      -79.383      canadacentral
Canada East          46.817      -71.217      canadaeast
UK South             50.941      -0.799       uksouth
UK West              53.427      -3.084       ukwest
West Central US      40.890      -110.234     westcentralus
West US 2            47.233      -119.852     westus2
Korea Central        37.5665     126.9780     koreacentral
Korea South          35.1796     129.0756     koreasouth
France Central       46.3772     2.3730       francecentral
France South         43.8345     2.1972       francesouth
Australia Central    -35.3075    149.1244     australiacentral
Australia Central 2  -35.3075    149.1244     australiacentral2
South Africa North   -25.731340  28.218370    southafricanorth
South Africa West    -34.075691  18.843266    southafricawest
```

There are a whole heap of params at the top of the script that you can change if you like,  
or just keep the defaults.