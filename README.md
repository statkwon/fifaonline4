# FIFA.py 사용 방법

## 1. 모듈 불러오기

```py
from FIFA import MetaData, UserData, MatchData, Dataset
```

```py
api_key = 'your own api key'
```

[피파온라인4 Open API](https://developers.nexon.com/fifaonline4)의 '마이페이지'에서 본인의 API 키값을 확인하실 수 있습니다.

---

## 2. 메타 정보

```py
metadata = MetaData()
```

```py
matchtype_dict, matchtype_dict_r = metadata.matchtype()
```

### a. 매치 종류

```py
matchtype_dict
```
<img width="153" alt="스크린샷 2022-05-22 오후 2 56 49" src="https://user-images.githubusercontent.com/57558636/169681034-89699e3e-3d0b-4fd1-a323-a3416f8c3931.png">

```py
matchtype_dict_r
```
<img width="154" alt="스크린샷 2022-05-22 오후 2 57 22" src="https://user-images.githubusercontent.com/57558636/169681054-13aa6612-23f6-4eed-9175-966ff30dde20.png">

### b. 선수 고유 식별자

```py
spid_dict, spid_dict_r = metadata.spid()
```

```py
spid_dict
```
<img width="213" alt="스크린샷 2022-05-22 오후 3 02 05" src="https://user-images.githubusercontent.com/57558636/169681179-7a1551d4-76dd-485a-9f18-e7229bf538c5.png">

```py
spid_dict_r
```
<img width="213" alt="스크린샷 2022-05-22 오후 3 02 40" src="https://user-images.githubusercontent.com/57558636/169681202-75836b2e-04ea-4a1f-a83d-237dcaee1033.png">

### c. 시즌 아이디

```py
seasonid_dict, seasonid_dict_r = metadata.seasonid()
```

```py
seasonid_dict
```
<img width="325" alt="스크린샷 2022-05-22 오후 3 03 14" src="https://user-images.githubusercontent.com/57558636/169681215-190f437d-ade4-4731-9b48-32b312a66577.png">

```py
seasonid_dict_r
```
<img width="326" alt="스크린샷 2022-05-22 오후 3 03 36" src="https://user-images.githubusercontent.com/57558636/169681224-c3374119-f4cd-461d-ac32-22a02b5b7480.png">

### d. 선수 포지션

```py
spposition_dict, spposition_dict_r = metadata.spposition()
```

```py
spposition_dict
```
<img width="157" alt="스크린샷 2022-05-22 오후 3 05 49" src="https://user-images.githubusercontent.com/57558636/169681287-a028f621-4e75-4267-8c04-20134b3bf7f6.png">

```py
spposition_dict_r
```
<img width="157" alt="스크린샷 2022-05-22 오후 3 06 13" src="https://user-images.githubusercontent.com/57558636/169681292-6268aedc-7662-4a15-b55b-33b262377f86.png">

### e. 등급 식별자

```py
division_dict, division_dict_r = metadata.division()
```

```py
division_dict
```
<img width="161" alt="스크린샷 2022-05-22 오후 3 07 44" src="https://user-images.githubusercontent.com/57558636/169681337-07d56ba9-615b-4736-afa4-8fe298dce571.png">

```py
division_dict_r
```
<img width="161" alt="스크린샷 2022-05-22 오후 3 08 07" src="https://user-images.githubusercontent.com/57558636/169681349-fdb819f8-233c-4a7a-9b14-299e640af89d.png">

### f. 선수 이미지

```py
metadata.playersaction(spid_dict_r['박주영'])
```
![image](https://user-images.githubusercontent.com/57558636/169680867-9888ba56-0d20-4e05-8ad8-7ebccf84f637.png)

---

## 3. 유저 정보

```py
userdata = UserData(api_key)
```

### a. 상위 N명 랭커 리스트

```py
ranker_list = userdata.top_n(10)
```
<img width="472" alt="스크린샷 2022-05-22 오후 3 09 56" src="https://user-images.githubusercontent.com/57558636/169681395-6779b9cc-d78b-4c26-ae56-6285963f680b.png">

### b. 유저 고유 식별자

```py
userinfo_dict, userinfo_dict_r = userdata.nick2id(ranker_list)
```

```py
userinfo_dict
```
<img width="391" alt="스크린샷 2022-05-22 오후 3 10 48" src="https://user-images.githubusercontent.com/57558636/169681468-eb9700fe-4979-4d86-bb13-db25eda2651d.png">

```py
userinfo_dict_r
```
<img width="390" alt="스크린샷 2022-05-22 오후 3 10 24" src="https://user-images.githubusercontent.com/57558636/169681449-5874df62-1f96-4f14-a939-c1c0cb3737bc.png">

---

## 4. 매치 정보
```py
matchdata = MatchData(api_key)
```

### a. 매치 기록

```py
matchinfo = matchdata.matchinfo(accessid=userinfo_dict.keys(), limit=5)
```
<img width="693" alt="스크린샷 2022-05-22 오후 3 13 05" src="https://user-images.githubusercontent.com/57558636/169681546-5dc2f76a-d43d-4019-9cac-6abfc9bb6277.png">

```py
matchinfo
```
<img width="242" alt="스크린샷 2022-05-22 오후 3 13 59" src="https://user-images.githubusercontent.com/57558636/169681588-a4a960f6-fa8e-488a-8eef-038371de9a51.png">

### b. 매치 상세 정보

```py
matchdetail = matchdata.matchdetail(matchinfo)
```

```py
matchdetail
```
<img width="475" alt="스크린샷 2022-05-22 오후 3 14 39" src="https://user-images.githubusercontent.com/57558636/169681604-66db0b17-c5bd-41ce-983b-ea4c3f6619e1.png">

---

## 5. 데이터프레임 가공

```py
dataset = Dataset()
```

```py
print(dataset.team_korea())
```
<img width="988" alt="스크린샷 2022-05-22 오후 3 15 45" src="https://user-images.githubusercontent.com/57558636/169681627-da943821-3b3e-4176-9632-0ed02edfe5f8.png">

```py
matchdetail_df = dataset.dataset(matchdetail, spid_dict)
```

```py
matchdetail_df
```
<img width="992" alt="스크린샷 2022-05-22 오후 2 55 24" src="https://user-images.githubusercontent.com/57558636/169681002-419176f9-7b7a-4664-9358-071c15554bac.png">
