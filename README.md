# AzDo-synpaseserverlessdacpac
First extracts the contents of a database in a serverless SQL Pool to a dacpac. It then deploys the contents of the dacpac to a database in a serverless SQL Pool.

Please note that you need the below variables created for this to work
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
