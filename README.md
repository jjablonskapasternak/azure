az login
# Create a resource group.
az group create --name myRG-3 --location westeurope
# Create a virtual network.
az network vnet create --resource-group myRG-3 --name myVnet-3 --subnet-name mySubnet-3
# Create a public IP address.
az network public-ip create --resource-group myRG-3 --name myPublicIP-3
# Create a network security group.
az network nsg create --resource-group myRG-3 --name myNSG-3
# Create a virtual network card and associate with public IP address and NSG.
az network nic create --resource-group myRG-3 --name myNic-3 --vnet-name myVnet-3 --subnet mySubnet-3 --network-securitygroup myNSG-3 --public-ip-address myPublicIP-3
# Create a virtual machine.
az vm create --resource-group myRG-3 --name myVM-3 --location westeurope --nics myNic-3 --image win2016datacenter --adminusername azureuser --admin-password $AdminPassword
# Open port 3389 to allow RDP traffic to host.
az vm open-port --port 3389 --resource-group myRG-3 --name myVM-3
