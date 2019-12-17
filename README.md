# Workshop Azure & Containers @ ISEP

![workshop-thumbnail](assets/workshop-thumbnail.png)

--- 

## Agenda (Azure Dev Spaces)

1. Create a Kubernetes-based environment in Azure that is optimized for development - a dev space.
    
2. Iteratively develop code in containers using VS Code and the command line.
    
3. Productively develop and test your code in a team environment.

## The Illustrated Children's Guide to Kubernetes
[![The Illustrated Children's Guide to Kubernetes](https://www.cncf.io/wp-content/uploads/2018/12/page1.png)](https://youtu.be/4ht22ReBjno)

---

## Visual Studio Code and .NET Core with Azure Dev Spaces

### Initial CLI Setup
Start by [installing the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) and verify installation.

Login to your Azure account.

`az login`

If you have more than one subscription in your account, you can list them with the following command.

`az account list --output table`

If the subscription you desire has _False_ for _IsDefault_

`az account set --subscription <SUBSCRIPTION_ID>`

### Create a Kubernetes cluster enabled for Azure Dev Spaces

Create a resource group for your cluster in a [supported region](https://docs.microsoft.com/en-us/azure/dev-spaces/about#supported-regions-and-configurations)

`az group create --name "workshop-isep" --location "West Europe"`

Create an Azure Kubernetes Service (AKS) 

`az aks create -g workshop-isep -n aks-workshop-isep --location "West Europe" --disable-rbac --generate-ssh-keys`

### Configure your Cluster to use Azure Dev Spaces

Enter the following command to enable Azure Dev Spaces support in your cluster.

`az aks use-dev-spaces -g workshop-isep -n aks-workshop-isep`

### Get Kubernetes Debugging for Visual Studio Code

1. Install [Visual Studio Code](https://code.visualstudio.com/).

2. Install [Azure Dev Spaces extension](https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds).

### Clone the Sample App 

Clone the repository with the .NET Core sample application to deploy to Azure Dev Spaces.
This repository is forked from the Azure Dev Space samples repository, it has been restructured to ease the deployment process.

`git clone https://github.com/2morales/aks-workshop-isep.git`

### Prepare the deployment

The next step is to containerize it by creating assets that define the app's container and Kubernetes deployment.

1. Launch Visual Studio Code and open the project folder (ignore default prompts to add debug assets or restore the project dependencies).
2. Open the Terminal (View > Integrated Terminal).
3. Run the preparation command (be sure to change directory into the dotnetcore/webfrontend folder).

`azds prep --public`



---

## Azure Dev Spaces
AZDS is an Azure developer service that helps teams develop with speed on Kubernetes. [Click here for more information.](https://aka.ms/signup-azds)

## Purpose of this repository
This source repository primarily hosts *AZDS code samples* to support product guides, as well as provide high-level insight into our product roadmap. Product documentation is hosted here: http://aka.ms/get-azds.

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
