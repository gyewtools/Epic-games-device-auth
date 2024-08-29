# Epic-games-device-auth
Epic games device auth docs (unofficial)

Device auth epic games undocumented docs

Type : post
Endpoint : https://account-public-service-prod.ol.epicgames.com/account/api/oauth/token
Headers : {"Content-Type": "application/x-www-form-urlencoded", "Authorization": f"Basic {SWITCH_TOKEN}"}
Payload : {"grant_type": "client_credentials"}

You can use the switch token OThmN2U0MmMyZTNhNGY4NmE3NGViNDNmYmI0MWVkMzk6MGEyNDQ5YTItMDAxYS00NTFlLWFmZWMtM2U4MTI5MDFjNGQ3
This will return an access token that can be used to get a device code

**Get device code**
Url : https://account-public-service-prod03.ol.epicgames.com/account/api/oauth/deviceAuthorization
Headers : {"Content-Type": "application/x-www-form-urlencoded", "Authorization": f"Bearer {access_token}"} (access token we got from switch token request)
Payload : {"prompt": "login"}

This will return a device code.

**Fetch access_token from device auth url**
URL : https://account-public-service-prod.ol.epicgames.com/account/api/oauth/token
HEADERS : {"Content-Type": "application/x-www-form-urlencoded", "Authorization": f"Basic {SWITCH_TOKEN}"}
PAYLOAD : {"grant_type": "device_code", "device_code": device_code}

Send this every 5-10 seconds until user authenticates, when done it will return some info including an access_token and account_id


**Additional fortnite-related apis**

URL : https://fortnite-public-service-prod11.ol.epicgames.com/fortnite/api/game/v2/profile/{account_id}/client/QueryProfile?profileId=common_core&rvn=-1
Make sure account_id is the one received from the oauth/token device code request
Headers : {"Authorization": f"Bearer {access_token}", "Content-Type": "application/json"}

This will return vbucks info
make sure to do the account_id again

**Fetch stw**

URL : https://fortnite-public-service-prod11.ol.epicgames.com/fortnite/api/game/v2/profile/{account_id}/public/QueryPublicProfile?profileId=campaign
Headers : {"Authorization": f"Bearer {access_token}", "Content-Type": "application/json"}
Make sure to get ur account_id there in the url 
has_stw = "YES" if "tutorial" in str(data) else "NO"


Make sure to star the repo and give credits if ur goona make something out of this
