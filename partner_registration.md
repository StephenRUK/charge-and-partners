# API Endpoint - partner registration

If you want to set yourself up as a partner of our system, you need to call our endpoint for partner registration.

| Method           | URL                                                   | Environment                          
|------------------|-------------------------------------------------------|--------------|
| POST             | https://api.and-charge.com/public/v1/partners | Production
| POST             | https://api-pp.and-charge.com/public/v1/partners | Pre Production

## Request payload is as follows:

| Attribute    | Type                               | [Cardinality](syntax.md#cardinality) | max. Length | Description 
|--------------|------------------------------------|-------------|-------------|---------------------------------------------------------------------------------------------------|
| name         |String                              |1            |100          | The name of the partner. Will be visible on our website and on transactions done with this partner
| partnerId    |String                              |1            |100          | A system wide unique identifier of this partner. Pick any ID you see fit. Will not be visible to users
| type         |Enumeration                         |1            |-/-          | The partner type. Possible values are: MSP, ONLINE_SHOP, OFFLINE_SHOP
| logo         |URL                                 |1            |2000         | A url to a logo of this partner. Ideally sized 320x240px; will be visible to users to identify the partner
| web          |URL                                 |1            |2000         | A link to the partners web site
| android      |URL                                 |?            |2000         | A link to an android app of the partner
| iOS          |URL                                 |?            |2000         | A link to an iOS app of the partner
| descriptions |[Description](types.md#description-class) |+            |-/-          | A list of descriptions for that partner (one text per language) explaining the partner within the context of Charge&. Will be visible to users. Please provide translations for at least `de` and `en`

## Response payload is as follows:

| Attribute    | Type                               | Cardinality | max. Length | Description 
|--------------|------------------------------------|-------------|-------------|---------------------------------------------------------------------------------------------------|
| accessToken (Deprecated) |String                  |1            | -/-         | The access token that must be used for requesting data from protected API endpoints. Keep this private and treat it as a secret. Do not store this unencrypted and do not share this with 3rd parties or clients. This attribute is deprecated and will be removed in subsequent versions of this API. Please use attributes accessKeyId and secretAccessKey instead.
| accessKeyId  |String                              |1            |100          | The ID of your API access key. This is your system's user at our token endpoint
| secretAccessKey |String                           |1            |100          | The secret value with which your system authenticates itself at our token endpoint
| name         |String                              |1            |100          | The name of the partner. Will be visible on our website and on transactions done with this partner
| partnerId    |String                              |1            |100          | A system wide unique identifier of this partner. Pick any ID you see fit. Will not be visible to users
| type         |Enumeration                         |1            |-/-          | The partner type. Possible values are: MSP, ONLINE_SHOP, OFFLINE_SHOP
| logo         |URL                                 |1            |2000         | A url to a logo of this partner. Ideally sized 320x240px; will be visible to users to identify the partner
| web          |URL                                 |1            |2000         | A link to the partners web site
| android      |URL                                 |?            |2000         | A link to an android app of the partner
| iOS          |URL                                 |?            |2000         | A link to an iOS app of the partner
| descriptions |[Description](types.md#description-class) |+            |-/-          | A list of descriptions for that partner (one text per language) explaining the partner within the context of Charge&. Will be visible to users. Please provide translations for at least `de` and `en`

## Sample request & response

### Request

   POST https://api.and-charge.com/public/v1/partners
   
   POST data:
```json
   {
   	"name": "Porsche Charging Service",
   	"partnerId": "PCS-001",
   	"logo": "https://connect-store-static01.porsche.com/_ui/images/porsche-logo@3x.png",
   	"web": " https://connect-store.porsche.com/de/de/porsche-charging-service/p/PorscheChargingService",
   	"android": "https://play.google.com/store/apps/details?id=com.porsche.mobilityapp&gl=de&hl=de",
   	"iOS": "https://itunes.apple.com/de/app/mobility-by-porsche/id1286754490?mt=8",
   	"type": "MSP",
   	"descriptions" : [
   		{
   			"lang": "de",
   			"text": "Der Porsche Charging Service integriert Elektromobilität problemlos in deinen Alltag – digital und vielfältig. Er vereint alle Lademöglichkeiten für Plug-in-Hybride und Elektrofahrzeuge und eröffnet dir Zugang zu Ladesäulen unterschiedlicher Anbieter. Nach einer einfachen Anmeldung über My Porsche und dem Kauf im Porsche Connect Store erhältst du die Porsche ID Card und Zugang zur App. Der Porsche Charging Service bietet aktuell ca. 49.000 Ladepunkte in Deutschland, Österreich, Schweiz, Belgien, Niederlande, Spanien, Frankreich, Dänemark, Finnland und Norwegen."
   		},
   		{
   			"lang": "en",
   			"text": "The Porsche Charging Service integrates e-mobility seamlessly into your daily life - digital and versatile. It combine all charging opportunities for plug-in hybrid and electric cars and opens up access to charging stations of various operators. After an easy registration at My Porsche and buying the service within the Porsche Connect store you will receive the Porsche ID Card and access to the Charging App. The Porsche Charging Service offers access to about 49,000 charging stations in Germany, Austria, Switzerland, Belgium, Netherlands, Spain, France, Denmark, Finland and Norway."
   		}
   	]
   }
```

### Response

```json
{
	"id": 4,
   	"name": "Porsche Charging Service",
   	"partnerId": "PCS-001",
   	"logo": "https://connect-store-static01.porsche.com/_ui/images/porsche-logo@3x.png",
   	"web": " https://connect-store.porsche.com/de/de/porsche-charging-service/p/PorscheChargingService",
   	"android": "https://play.google.com/store/apps/details?id=com.porsche.mobilityapp&gl=de&hl=de",
   	"iOS": "https://itunes.apple.com/de/app/mobility-by-porsche/id1286754490?mt=8",
	"descriptions": [{
			"key": "DESCRIPTION",
			"lang": "de",
			"text": "Der Porsche Charging Service integriert Elektromobilität problemlos in deinen Alltag – digital und vielfältig. Er vereint alle Lademöglichkeiten für Plug-in-Hybride und Elektrofahrzeuge und eröffnet dir Zugang zu Ladesäulen unterschiedlicher Anbieter. Nach einer einfachen Anmeldung über My Porsche und dem Kauf im Porsche Connect Store erhältst du die Porsche ID Card und Zugang zur App. Der Porsche Charging Service bietet aktuell ca. 49.000 Ladepunkte in Deutschland, Österreich, Schweiz, Belgien, Niederlande, Spanien, Frankreich, Dänemark, Finnland und Norwegen."
		}, {
			"key": "DESCRIPTION",
			"lang": "en",
			"text": "The Porsche Charging Service integrates e-mobility seamlessly into your daily life - digital and versatile. It combine all charging opportunities for plug-in hybrid and electric cars and opens up access to charging stations of various operators. After an easy registration at My Porsche and buying the service within the Porsche Connect store you will receive the Porsche ID Card and access to the Charging App. The Porsche Charging Service offers access to about 49,000 charging stations in Germany, Austria, Switzerland, Belgium, Netherlands, Spain, France, Denmark, Finland and Norway."
		}
	],
	"status": "INITIAL",
	"accessToken": "<deprecated, do not use this anymore>",
	"accessKeyId": "DF8eS2h9j0hq",
	"secretAccessKey": "<treat this value as a secret, don't share it with anybody else>"
}
```

### Error handling

The following errors are specific to this service:

| Error                      | Http status code                   | Description 
|----------------------------|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| PARTNER_ALREADY_REGISTERED | 400                                | The partner with the given partnerId is already registered. Please use a different partnerId for registration 

Please refer to [error handling](error_handling.md) for the general concept and usage of errors within the API
Please refer to [authentication](authentication.md) for the authentication flow within the API

## Next steps

As soon as you are set up as a partner, you probably want to [__link your users__ with &Charge users](link_accounts.md) to provide them with the services available.