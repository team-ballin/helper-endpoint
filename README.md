# Sport Total x Ballin Video Linking
## Api Documentation

### Endpoint
provided by mail

### Method
POST

### Headers
name | required | value
--- | --- | ---
Content-Type | true | application/json
X-Access-Token | true |

### Body

#### With Match Id
name | required | type | note
--- | --- | --- | ---
matchId | true | String |
hlsUrl | true | String |
mp4Url | true | String |

#### Without Match Id
name | required | type | note
--- | --- | --- | ---
homeClubAffiliateId | true | String |
awayClubAffiliateId | true | String |
matchDate | true | Unix Timestamp |
competitionId | false | String | remove potential match ambiguity
hlsUrl | true | String |
mp4Url | true | String |

### Example

```bash
# With matchId
curl -X POST $ENDPOINT \
  -H "Content-Type: application/json" \
  -H "X-Access-Token: $ACCESS_TOKEN" \
  -d '{"matchId": "22078637", "mp4Url": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4", "hlsUrl": "."}'

# Without matchId
curl -X POST $ENDPOINT \
  -H "Content-Type: application/json" \
  -H "X-Access-Token: $ACCESS_TOKEN" \
  -d '{"homeClubAffiliateId":"501969","awayClubAffiliateId":"501900","matchDate":"1589627457","competitionId":"362734", "hlsUrl": "-", "mp4Url": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"}'
```

### Success

response example:
```json
{
  "success": true
}
```

### Errors

status | when
--- | ---
404 | We can't find the match with provided inputs
400 | Inputs are mal formated
403 | x-access-token header is wrong
500 | Something went wrong, please contact us

error example:
```json
{
  "success": false,
  "status": 403,
  "details": "Forbidden",
}
```




