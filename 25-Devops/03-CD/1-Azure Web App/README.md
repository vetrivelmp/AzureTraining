1. Create Azure Web App -> .Net Core 3.1, Standard App Service Plan
1. Open DevOps Project and create a build pipeline
1. Chose existing ASP.Net Project
1. Remove testing part
1. Add the Publish Task
1. Save and Run
1. Notice the artifact is produced on the Job
1. Open Pipelines\Releases\New Pipeline
1. Chose Azure App Service Deployment
1. Add artifact from build pipeline
1. Configure Stage\Stage Name, Chose Azure Web App
1. Give name to release pipeline and Create Release
1. Open the release details to see the progress
1. Once succeeded look the logs
1. Refresh page to see the deployed app


For Continuous Delivery Trigger:
1. Edit release pipeline
2. Click on Continuous deployment trigger on Artifacts window task
3. Enable
4. Save and Create Release
5. Do changes in the code and commit changes
6. Build pipeline will trigger
7. Release pipeline will also trigger

For Multiple Stages:
1. Edit existing release pipeline
1. Add Stage in Serial for QA then Prod
1. Create new Azure Web App for Prod
1. Configure Prod Web App in release pipeline for Prod App
1. Save and "Create Release"
1. Do changes in Source Code.
1. Build and Release pipelines will trigger
1. Both QA and Prod will be having the release
