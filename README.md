# WepayApi-Python-
Wepay Api (Python) 

import urllib, urllib2, json

url     = 'https://stage.wepayapi.com/v2/user'
headers = {
	   'Content-Type': 'application/json',
           'User-Agent': 'Codecademy WePay Demo',
           'Authorization': 'Bearer STAGE_df1684a1c7b91f0de51b72e5890891b92d34e47fb3cb48d4dbd8d2a89fa253cc'
	   } # these are the HTTP headers
params  = {
		   'account_id': 161624111,
		   'short_description': 'A brand new soccer ball',
		   'type': 'GOODS',
		   'amount': '24.95'
		   } # any parameters needed for the API call
request = urllib2.Request(url, params, headers)
try:
	response = urllib2.urlopen(request, timeout=30).read()
	print json.loads(response)
except urllib2.HTTPError as e:
	print e
	
from wepay import WePay
wepay = WePay()
wepay = WePay(production=False,access_token='STAGE_df1684a1c7b91f0de51b72e5890891b92d34e47fb3cb48d4dbd8d2a89fa253cc')
response = wepay.call('/preapproval/create', {
	'account_id': 161624111,
	'period': 'monthly',
	'end_time': '2016-12-25',
	'amount': '19.99',
	'short_description': 'A subscription to our magazine.',
	'redirect_uri': 'http://example.com/success/',
	'auto_recur': True
})

print response
