# json 방식

### 1) requsets, json 패키지 호출
```
import requests
import json
```
### 2) url setting
```
service_key = " "
params = " "
callback_url = " "
url = callback_url+params+service_key
```

### 3) requests
- 호출결과 확인 : 200 : ok / 300,400 : error
```
response = requests.get(url)
response   
```

### 4) json 구조 확인
```
response.text   
```

### 5) json 에서 dict 추출
- json 타입에서 dict 타입의 부분을 추출하기위해, 상위의 항목을 확인한다.
- dict 에서 key 를 확인한다. 보통 실제 데이터는 item, items 에 들어있다.
```
datas = rsponse.json()['key 이름']
datas.keys()
```

### 6) 데이터프레임으로 변환
```
df = pd.DataFrame(datas['item']) 
df
```
