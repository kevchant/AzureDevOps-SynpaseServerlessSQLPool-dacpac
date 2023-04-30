# AzureDevOps-SynpaseServerlessSQLPool-dacpac
Example of a state-Based deployment that can create a dacpac file based on an existing serverless SQL Pool and deploy it to another Azure Synapse serverless SQL Pool using Azure DevOps. Based on a blog post I wrote called '[Deploying a dacpac to a serverless SQL pool](https://www.kevinrchant.com/2023/02/15/deploying-a-dacpac-to-a-serverless-sql-pool/)'.

You can find the YAML files which you can use as templates for Azure Pipelines in the AzureDevOpsTemplates folder.

The '[serverlessSQLPool-sqlpackage.yml pipeline](https://github.com/kevchant/AzureDevOps-SynpaseServerlessSQLPool-dacpac/blob/main/AzureDevOpsTemplates/serverlessSQLPool-sqlpackage.yml)' extracts the contents of a database in a serverless SQL Pool to a dacpac. It then deploys the contents of the dacpac to a database in the same  serverless SQL Pool.

Whereas the '[serverlessSQLPool-sqlpackage-install-first.yml pipeline](https://github.com/kevchant/AzureDevOps-SynpaseServerlessSQLPool-dacpac/blob/main/AzureDevOpsTemplates/serverlessSQLPool-sqlpackage-install-first.yml)' first installs SqlPackage on the agent specified. 

From there, it extracts the contents of a database in a serverless SQL Pool to a dacpac. It then deploys the contents of the dacpac to a database in the same  serverless SQL Pool.

Please note that you need the below variables created for either of the pipelines to work:
I recommend doing this by creating at least one variable group
*   agentpool - The name of the agent pool you want to use (ideally a self-hosted one with latest sqlpackage installed).
     Otherwise you must put additional logic in this pipeline to deploy latest version of sqlpackage onto the agent
*   TargetFile - The name of the dacpac that you want to be created
*   SQLPoolEndPoint - The name of your serverless SQL Pool endpoint (which you can get in the Azure Synapse overview)
*   SourceDB - The name of database in the serverless SQL Pool you want to extract the schema from
*   SQLPooluser - A SQL login that can access the serverless SQL Pool
*   SQLPoolpw - The p/w for the above SQL login
*   SQLPoolartifactname - A name for the created artifact
*   AzureSubscription - The Azure subscription that contains the serverless SQL Pool where you want to deploy the dacpac
*   DestinationDB - The name of the target/destination database where you to deploy the dacpac

Note that you can extend this however you see fit. For example, you can add a variable for a second serverless SQL Pool endpoint which belongs to another workspace.
