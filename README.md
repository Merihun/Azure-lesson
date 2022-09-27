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
    # command
az vm show --resource-group myResourceGroup --name myVMname --query "{name: name, os:storageProfile.imageReference.offer}" --output table

# output
Name    Os
------  ------------
myVMname   UbuntuServer
```
