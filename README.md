# Shift Allowance Ledger - Azure Static Web Apps Deployment

This folder is ready to deploy as an Azure Static Web App.

## Contents

- `index.html` - the Shift Allowance Ledger app
- `staticwebapp.config.json` - Azure Static Web Apps routing/config

## Deploy With Azure Portal + GitHub

1. Push this folder to a GitHub repository.
2. Open Azure Portal: https://portal.azure.com/#browse/Microsoft.Web%2FStaticSites
3. Create a new Static Web App.
4. Select GitHub as the deployment source.
5. Choose the repository and branch.
6. Use these build settings:
   - App location: `/`
   - API location: leave blank
   - Output location: leave blank
7. Create the app.
8. Copy the generated URL, for example `https://your-app.azurestaticapps.net`.

## Required Microsoft Login Setting

After Azure creates the static web app, add the final site URL as a redirect URI in the Microsoft Entra app registration used by this tracker:

1. Go to Microsoft Entra ID > App registrations.
2. Open the tracker app registration.
3. Go to Authentication.
4. Add platform: Single-page application.
5. Add redirect URI: `https://your-app.azurestaticapps.net/`
6. Save.

## SharePoint Data

For all team members to see the same records, configure the app Settings screen with the same:

- Tenant ID
- App/client ID
- SharePoint site URL
- Employees list name
- Rates list name
- Entries list name

If SharePoint is not connected, records are stored only in each user's browser local storage.

## Alternative: Host Directly On SharePoint

You can also host this app from the SharePoint site:

https://bosch.sharepoint.com/sites/msteams_bf9839

Current hosted file:

https://bosch.sharepoint.com/sites/msteams_bf9839/Shared%20Documents/shift-allowance/index.html

Recommended location:

1. Open the site in the browser.
2. Go to Site contents.
3. Open Site Assets, or create a document library/folder for this app.
4. Upload `index.html`.
5. Open the file and copy the direct browser URL.
6. Share that URL with the team.

Important: some SharePoint Online sites block direct rendering of uploaded `.html` files and may download the file instead of running it. If that happens, this app cannot be hosted as plain HTML on that site without SharePoint admin changes or converting it into a SharePoint Framework web part.

If the HTML file opens and runs in the browser, update the Microsoft Entra app registration redirect URI to the exact SharePoint file URL, for example:

https://bosch.sharepoint.com/sites/msteams_bf9839/SiteAssets/shift-allowance/index.html

The exact URL must match where the file is actually hosted.
