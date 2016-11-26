# WepayApi-Python-
Wepay Api (Python) 
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
