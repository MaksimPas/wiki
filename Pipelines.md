# Pipelines

Current application is .NET Core 3.1.


## **Continuous Integration**

Created CI for build of NET 6.0 application
Basic YAML CI script and added the folllowing for artifacts:

```
- powershell: gci env:* | sort-object name | Format-Table -AutoSize | Out-File $env:BUILD_ARTIFACTSTAGINGDIRECTORY/environment-variables.txt

- task: DownloadBuildArtifacts@0
  inputs:
    buildType: 'current'
    downloadType: 'single'
    artifactName: 'drop'
    downloadPath: '$(System.ArtifactsDirectory)'
```


## **Azure web app**

Created a Web App in portal.azure.com at the BESTOS-RG (resource group).

![app_service1.PNG](/.attachments/app_service1-ae54ffa6-5643-457d-afa6-f0719cca8786.PNG)


## **Continuous Deployment**

Created basic CD for release of NET 6.0 application. No changes in script.

Created a new release and published to new Web app.

## **Testing**
When app is released, tested and verified that the release works fine.

![image.png](/.attachments/image-33f14bd3-ad77-43a1-a721-12b0358726bf.png)




![image.png](/.attachments/image-e1907ef7-3dc2-4f54-b266-38109687f196.png)
