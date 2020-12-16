# naver vibe data crawling
- 네이버 음악 서비스인 vibe 의 오늘 Top 100 차트의 데이터 크롤링

## 1. page information
- Request URL: https://apis.naver.com/vibeWeb/musicapiweb/vibe/v1/chart/track/total
- Requests Method : GET
- type : 동적페이지

## 2. parsing
- xml 형태의 데이터를 json 형태로 변환시켜주는 xmltodict 패키지를 사용
```
import requests
import json
import xmltodict
```
### 1) url settings
```
start, display = 1, 300
url = "https://apis.naver.com/vibeWeb/musicapiweb/vibe/v1/chart/track/total?start={}&display={}".format(start, display)
print(url)
```
- https://apis.naver.com/vibeWeb/musicapiweb/vibe/v1/chart/track/total?start=1&display=300

### 2) requests
- xml 형태의 정렬이 안된 데이터가 출력된다.
- 필요한 데이터를 가져오기 위해 엘리먼트를 찾아야한다.
```
response = requests.get(url)
response

=====<print>=====

<Response [200]>
```

- 데이터 확인
```
response.text
```

![vibe_response](./images/vibe_response.PNG)

### 3) xml -> json
- xmltodict 패키지의 기능을 사용하면 xml 형태의 데이터를 json 형태로 바꿔준다.
```
datas = json.dumps(xmltodict.parse(response.text))
datas = json.loads(datas)
```

![vibe_json](./images/vibe_json.PNG)

### 3) data search
- 가수명, 앨범명, 랭킹순위 등 필요한 데이터가 dict 의 6 개 하위에 들어있다.
```
basic_cate = datas["response"]["result"]["chart"]["items"]["tracks"]["track"][1]
```

![vibe_dict](./images/vibe_dict.PNG)

### 4) data parsing
- 기본 카테고리를 사용하여, 랭킹, 아티스트명, 노래명, 앨범명, 앨범장르 데이터를 파싱
- 아티스트명은 dict 의 구조가 달라서 예외처리를 사용
```
dfs = []
basic_cate = datas["response"]["result"]["chart"]["items"]["tracks"]["track"]

for i in range(len(basic_cate)) :
    
    ranking = basic_cate[i]["rank"]["currentRank"]
    
    try : 
        artistName = basic_cate[i]["artists"]["artist"]["artistName"]
    except :
        #artistName = datas["response"]["result"]["chart"]["items"]["tracks"]["track"][i]["album"]["artists"]["artist"]["artistName"]
        artistName = "Various Artist"
    
    trackTitle = basic_cate[i]["trackTitle"] 
    albumTitle = basic_cate[i]["album"]["albumTitle"]
    albumGenres = basic_cate[i]["album"]["albumGenres"]
    
    dfs.append({
        "ranking" : ranking,
        "artistName" : artistName,
        "trackTitle" : trackTitle,
        "albumTitle" : albumTitle,
        "albumGenres" : albumGenres,
    })
```

- 데이터 프레임으로 전환
- 1위 부터 300위 까지의 데이터가 잘 저장됐다.
```
top_list = pd.DataFrame(dfs)
```

![vibe_df](./images/vibe_df.PNG)






















