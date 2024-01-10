# Deploy React App to Azure Webapp. 

## HOW IT WORKS
This workflow does the following:

- Listens for pushes to the main and development branches.
- Checks out the code and sets up Node.js.
- Installs dependencies and builds the React app.
- Determines whether the branch is main or development and sets the appropriate version file and web app name.
- Checks if the version has changed by comparing the current version with the latest version in the commit.
- If the version has changed, it deploys the app to the specified Azure Web App "SLOT" using the Azure `azure/webapps-deploy@v3`.
- Updates the version in the corresponding manifest file if the deployment was successful.

## GITHUB SETUP
In your repository's settings, create two secrets:

### Actions
- `AZURE_WEBJOB_NAME`: The name of the Azure Web Job.
- `AZURE_WEBJOB_PUBLISH_PROFILE_PROD`: The contents of the Azure Web Job's publish profile of the PROD deployment slot.
- `AZURE_WEBJOB_PUBLISH_PROFILE_DEV`: The contents of the Azure Web Job's publish profile of the DEV deployment slot.

    > _The above three parameters are REQUIRED, and the branches_

### Repo
- Create two branches `prod` amd `development`.

## AZURE SETUP
- Create a Webjob setup with two deployment slots named `prod` and `dev`, and download and update the environment variables in the mentioned above.

