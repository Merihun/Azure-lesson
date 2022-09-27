# Azure-lesson

### If you have a repository and want to push from local
```
echo "# Azure-lesson" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:Merihun/Azure-lesson.git
git push -u origin main
```
### Tips for using the Azure CLI successfully

### Output formatting

Three common output formats are used with Azure CLI commands:

1. The json format shows information as a JSON string.
    This format is the default but you can use the --output parameter to specify a different option.
    Change the global default format to one of your personal preference by using az config such as 
    ```
    az config set core.output=table.
    ```
2. The table format presents output as a readable table. 
```
az vm show --resource-group myResourceGroup --name myVMname --query "{name: name, os:storageProfile.imageReference.offer}" --output table

output
Name    Os
------  ------------
myVMname   UbuntuServer

```
3. The tsv format returns tab-separated and newline-separated values without extra formatting, keys, or other symbols.
    - The TSV format is useful for concise output and scripting purposes.
    - The TSV will strip double quotes that the JSON format preserves.
    - To specify the format you want for TSV, use the --query parameter.
```
export vm_ids=$(az vm list --show-details --resource-group myResourceGroup --query "[?powerState=='VM running'].id" --output tsv)
az vm stop --ids $vm_ids
```

### Pass values to another command
If the value will be used more than once, assign it to a variable. Variables allow you to use values more than once or to create more general scripts. This example assigns an ID found by the az vm list command to a variable.
```
# assign the list of running VMs to a variable
running_vm_ids=$(az vm list --resource-group MyResourceGroup --show-details \
    --query "[?powerState=='VM running'].id" --output tsv)

# verify the value of the variable
echo $running_vm_ids
```
