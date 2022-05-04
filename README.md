# MyKotaApp
Existing Kotakota App enhanced with Authentication via Approuter and CDS Authorization

AppRouter Authentication
1. Add App Router and UI5 as dependencies in package.json

MyKotaSrv and MyKotaApp Connection
1. Set MyKotaSrv URI as destination in manifest.yaml
2. Set XSUAA as services in manifest.yaml (See deployment prerequisites)
3. Add MyKotaSrv destination in xs-app.json with basic authentication. Approuter will handle forwarding of AuthToken to MyKotaSrv
4. Add localDir webapp with XSUAA authentication
5. Update webapp/manifest.json DataSources with relative path of MyKotaSrv destination configured in xs-app.json.
6. Update BaseController.js ajax call with relative path of MyKotaSrv destination configured in xs-app.json

Basic UI Config to reflect CDS Authorization in MyKotaSrv
1. Update UnitAvailSea.controller.js/_onPatternMatched method with try-catch block for handling of CDS Authorization messages.
2. On error, display message pop up with error status code and text.
3. Redirect to new target "Others" containing basic Message Page to block section if user is unauthorized to READ/GET

New view "Others" for basic UI handling
1. Create Others.view.xml containing basic MessagePage
2. Update webapp/manifest.json targets with the new view

Deployment Prerequisites (XSUAA must be the same as MyKotaSrv)
1. Create XSUAA instance using xs-security.json found in MyKotaApp in BTP