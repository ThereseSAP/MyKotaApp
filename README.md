# MyKotaApp
Existing Kotakota App enhanced with Authentication via Approuter and CDS Authorization

AppRouter Authentication
1. Add App Router and UI5 as dependencies in package.json

MyKotaSrv and MyKotaApp Connection
2. Set MyKotaSrv URI as destination in manifest.yaml
3. Add MyKotaSrv destination in xs-app.json with basic authentication. Approuter will handle forwarding of AuthToken to MyKotaSrv
4. Add localDir webapp with XSUAA authentication
5. Update webapp/manifest.json DataSources with relative path of MyKotaSrv destination configured in xs-app.json.
6. Update BaseController.js ajax call with relative path of MyKotaSrv destination configured in xs-app.json

Basic UI Config to reflect CDS Authorization in MyKotaSrv
7. Update UnitAvailSea.controller.js/_onPatternMatched method with try-catch block for handling of CDS Authorization messages.
8. On error, display message pop up with error status code and text.
9. Redirect to new target "Others" containing basic Message Page to block section if user is unauthorized to READ/GET

New view "Others"
10. Create Others.view.xml containing basic MessagePage
11. Update webapp/manifest.json targets with the new view