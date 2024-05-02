# CI/CD pipeline for .Net Application

In this project we will build and deploy CI/CD pipeline for .net Application using Azure DevOps.

## Create a Project in Azure DevOps

First create a project in Azure DevOps.

![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/createproject.png)

## Push source Code into Azure Repo

I pushed .Net Source Code into Azure DevOps Repo
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/Repo.png)

## Build a  Pipeline for the application

Create a new pipeline in Pipelines
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/createpipeline.png)

Select Azure Repo as source Repo
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/selectrepo.png)

select starter pipeline in configure your pipeline
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/starterpipeline.png)

for our pipeline let's add tasks. This tasks will create artifact. task will download required libraries for the application. build the project and create a artifact.
first task is Nuget. Nuget is used to download libraries for >net Application.
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/pipeline1.png)

Second task is we need Visual studio to build the project. I will add Build commands needed for this project below.

```
'/p:DeployOnBuild=true  /p:WebPublishMethod=Package /p:PackageAsSingleFile=true  /p:SkipInvalidConfigurations=true  /p:PackageLocation="$(build.stagingDirectory)" /p:IncludeServerNameInBuildInfo=True /p:GenerateBuildInfoConfigFile=true /p:BuildSymbolStorePath="$(SymbolPath)" /p:ReferencePath="C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Extensions\Microsft\Pex"'
```
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/pipeline2.png)

copy the files to the agent source folder and publish artifact to the staging directory.
![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/pipeline3.png)

Now click on save and run. this will run the build pipeline and create a artifact.

![](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/artifactcreated.png)

## create a release pipeline.
click on release and select new release pipeline.

[](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/createrelease.png)

now just like build pipeline we need to add tasks to the release pipeline.

[](https://github.com/AbiVavilala/CI-CD-Pipeline-for-.Net-application/blob/main/images/addtasks.png)





