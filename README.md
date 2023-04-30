# Sosial Media
Telegram : https://t.me/minsanztuy

# pocketoptionapi
Pocket Option API  
Website    : https://autotradevip.com/id/  
Olmyptrade : https://youtu.be/zTZT7zDlmtU  
Binomo     : https://youtu.be/ww9rVMX5TK4  
IQ Option  : https://youtu.be/4i3YUEDRGWY  
Quotex     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  
Expert Option     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA
Pocket Option     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  

### Import
```python
from pocketoption.stable_api import PocketOption
```
### Login by ssid
PockOption only support ssid login, because GOOGLE reCAPTCHA
if connect sucess return True,None  
if connect fail return False,None 
```python
from pocketoption.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123123\";s:10:\"ip_address\";s:12:\"2.111.11.5\";s:10:\"user_agent\";s:104:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123232;}1232321213","isDemo":0,"uid":"123232132"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
print(check_connect,message)
```
### check_win & buy sample
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123123\";s:10:\"ip_address\";s:12:\"2.111.11.5\";s:10:\"user_agent\";s:104:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123232;}1232321213","isDemo":0,"uid":"123232132"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
if check_connect:
    account.change_balance("PRACTICE")#"REAL"
    asset="EURUSD"
    amount=1
    dir="call"#"call"/"put"
    duration=30#sec
    print("Balance: ",account.get_balance())
    buy_info=account.buy(asset,amount,dir,duration)
    #need this to close the connect
    print("----Trade----")
    print("Get: ",account.check_win(buy_info["id"]))
    print("----Trade----")
    print("Balance: ",account.get_balance())
    #need close ping server thread
    account.close()
```
### GetBalance
```python
from pocketoptionapi.stable_api import PocketOption 
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check,message=account.connect()
account.change_balance("PRACTICE")
balance=account.get_balance()
print(balance)
account.close()
```
### Buy
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check,message=account.connect()
if check:
    account.change_balance("PRACTICE")
    asset="EURUSD"
    amount=1
    dir="call"#"call"/"put"
    duration=60#sec
    print(account.buy(asset,amount,dir,duration))
    account.close()
```
### sell_option
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
if check_connect:
    account.change_balance("PRACTICE")#"REAL"
    asset="EURUSD"
    amount=1
    dir="call"#"call"/"put"
    duration=120#sec
    print("Balance: ",account.get_balance())
    buy_info=account.buy(asset,amount,dir,duration)
    #need this to close the connect
    account.sell_option(buy_info["id"])
    account.close()
```
### get candle
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
import time
if check_connect:
    asset="EURUSD"
    _time=int(time.time())#the candle end of time
    offset=120#how much sec want to get     _time-offset --->your candle <---_time
    period=60#candle size in sec
    print("You will get the candle from: "+str(_time-offset)+" to: "+str(_time))
    print("------\n")
    candle=account.get_candle(asset,_time,offset,period)
    for c in candle["data"]:
        print(c)
    account.close()
```
### check_asset_open
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
import time
if check_connect:
    print("Check Asset Open")
    for i in account.get_all_asset_name():
        print(i,account.check_asset_open(i['asset']))
    account.close()
```
### GET realtime candle
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
import time
if check_connect:
    asset="NZDUSD_otc"
    list_size=10#this is setting how much Quote you want to save
    account.start_candles_stream("NZDUSD_otc",list_size)
    while True:
        if len(account.get_realtime_candles("NZDUSD_otc"))==list_size:
            break
    print(account.get_realtime_candles("NZDUSD_otc"))
    account.close()
```
### get_payment
```python
from pocketoptionapi.stable_api import PocketOption
ssid=r"""42["auth",{"session":"a:4:{s:10:\"session_id\";s:32:\"123123123\";s:10:\"ip_address\";s:12:\"1.2.3.4\";s:10:\"user_agent\";s:123:\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36\";s:13:\"last_activity\";i:123;}123","isDemo":1,"uid":"123"}]"""
account=PocketOption("platform44.po2.capital",ssid) 
check_connect,message=account.connect()
if check_connect:
    
    all_data=account.get_payment()
    for asset_name in all_data:
        asset_data=all_data[asset_name]
        print(asset_name,asset_data["payment"],asset_data["open"])

account.close()
```
