# Changes 

These are the required changes in order to get things working again after the kind folks at Atlassian modified their API due the 
General Data Protection Regulation (GDPR).

## API tokens

https://confluence.atlassian.com/cloud/api-tokens-938839638.html

JIRA_API_KEY=KlFfhSS...L8DzxGSE3EA
JIRA_API_BASE64_ADMIN=a2lmZmluLmdpc...BaklMOER6eEdTRTNFQQ==
JIRA_API_ADMIN_USER=kiffin.gish
JIRA_API_ADMIN_PASSWORD=secret
JIRA_API_ADMIN_EMAIL=kiffin.gish@planet.nl

```
$curl -v --url 'https://gishtech.atlassian.net' --user 'kiffin.gish@planet.nl:KlFfhSS1p2AjIL8DzxGSE3EA'
...
Authorization: Basic a2lmZmluLmdpc2hAcGxhbmV0Lm5sOktsRmZoU1MxcDJBaklMOER6eEdTRTNFQQ==
...
```

```
$ echo -n kiffin.gish@planet:KlFfhSS1p2AjIL8DzxGSE3EA | base64
a2lmZmluLmdpc2hAcGxhbmV0OktsRmZoU1MxcDJBaklMOER6eEdTRTNFQQ==
```

$ curl --request GET --user 'kiffin.gish@planet.nl:KlFfhSS1p2AjIL8DzxGSE3EA' --header 'Accept: application/json' --url 'https://gishtech.atlassian.net/rest/api/2/user/bulk/migration?username=kiffin.gish'
[{"username":"kiffin.gish","accountId":"5c1b0a2b81c1261667adbc97"}]✔ 

```
$ curl -v --request GET --user 'kiffin.gish@planet.nl:KlFfhSS1p2AjIL8DzxGSE3EA' --header 'Accept: application/json' --url 'https://gishtech.atlassian.net/rest/api/2/user/bulk/migration?username=kiffin.gish'
```

## Create User

```
curl --request POST \
  --url 'https://gishtech.atlassian.net/rest/api/2/user' \
  --user 'kiffin.gish@planet.nl:KlFfhSS1p2AjIL8DzxGSE3EA' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data '{
  "password": "abracadabra",
  "emailAddress": "mia@atlassian.com",
  "displayName": "Mia Krystof",
  "name": ""
}'
```

curl --request POST --url 'https://gishtech.atlassian.net/rest/api/2/user' --user 'kiffin.gish@planet.nl:KlFfhSS1p2AjIL8DzxGSE3EA' --header 'Accept: application/json' --header 'Content-Type: application/json' --data '{ "emailAddress": "unknown-1@example.org", "displayName": "Unknown #1" }'
