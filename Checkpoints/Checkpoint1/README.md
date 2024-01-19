
# CAA900-Azure-Project: Checkpoint1 Submission

- **COURSE INFORMATION: CAA900 - Capstone Project**
- **STUDENT’S NAME: Sanah Hussain Edavalath Vayalil Keloth**
- **STUDENT'S NUMBER: 160683231**
- **GITHUB USER_ID: 160683231-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

## Table of Contents
- [My Collaborators Image](#my-collaborators-image)
- [Sample Single Line Code Embedding](#sample-single-line-code-embedding)
- [Sample Multi-Line Code Snippet](#sample-multi-line-code-snippet)
- [Sample JSON Object](#sample-json-object)
- [Sample Table](#sample-table)
- [Collaboration in GitHub - Suggestions](#collaboration-in-github---suggestions)
- [Useful Links](#useful-links)

## My Collaborators Image
![Collaborators Screenshot](collaborator.png)

## Sample Single Line Code Embedding
To retrieve the username email of the Azure account, you can use the following Azure CLI command:
`az account show --query user.name -o tsv`

## Sample Multi-Line Code Snippet
```bash
# Azure CLI Script to Check and Create a Resource Group if it Doesn't Exist
if [ $(az group exists --name myResourceGroup) = false ]; then 
   az group create --name myResourceGroup --location eastus
else
   echo "myResourceGroup already exists"
fi
```

## Sample JSON Object

## Sample Table

## Collaboration in GitHub - Suggestions

## Useful Links
