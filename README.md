# **딥러닝 기술을 이용한 유해동물 퇴치 알림  서비스**
<br/>

## __이 서비스는 국립 공원 공단과 협업 프로젝트를 진행하여 만든 서비스입니다.__

<br/><br/>

## 최종 결과물

<br/>

![녹화영상2](https://user-images.githubusercontent.com/86835527/179003224-1beced48-566d-4d08-bf6f-dcead03d5fba.gif)

<br/><br/><br/>

## 1. 데이터

<br/>

![사진개수](https://user-images.githubusercontent.com/86835527/179009760-667f6ed5-0a28-4793-bc4a-d07e4e0be02b.PNG)

<br/>

국립공원공단으로부터 약 6만장의 사진 데이터를 제공받았고,   
그 중에서 멧돼지와 고라니가 가장 많은 부분을 차지함을 확인.

<br/><br/><br/>

## 2. 데이터로부터 인사이트 도출

<br/>

멧돼지와 고라니 -> 농작물에 피해를 끼치는 유해동물종임을 조사.  

<br/>

![image](https://user-images.githubusercontent.com/86611917/175793065-b0c58bc6-4de2-4c05-a2ac-8139d738c12c.png)

![image](https://user-images.githubusercontent.com/86611917/175792831-fd8545de-37ae-4722-bdf6-1c9e994cbd37.png)

위의 그래프는 환경부에서 얻어낸 동물별 농작물 피해보상액을 그래프로 시각화 한 것으로,  
단위는 백만원, 유해동물로 인한 피해의 대부분이 멧돼지와 고라니에 편향되어 있는 것을 발견.

<br/><br/><br/>

## 3. 유사사례 조사

<br/>

### __이지워치__   

<br/>

"이지워치"는 현재 국립공원공단에서 실제로 사용 중이며 카메라 반경 안에 일정한 무게가 넘는 생물체가 움직이는 것이 확인되면 호랑이 울음소리를 냄으로서 야생동물을 내쫓는 시스템.

<br/>

### __문제점__   

<br/>

1. 기계하나에 99만원으로 가격적으로 부담이 상당함.  
2. 한가지 경고음만을 사용해 야생동물이 이에대해 학습해서 내성이 생길만한 여지가 있음
3. 25kg 이상의 열이나는 물체를 감지만 하면 호랑이 소리를 짖어내는 바람에 소리가 나오는 횟수가 너무 많아져 소음으로 인한 민원이 자주 발생.

<br/><br/><br/>

## 4. 프로젝트 진행

<br/>

농작물 피해를 예방하며, 기존 서비스의 문제점을 보완하기 위해 영상인식 딥러닝을 이용하여 유해동물중 가장 많은 피해를 주는 “멧돼지와 고라니”를 인식하는 퇴치 서비스를 고안.

<br/>

![image](https://user-images.githubusercontent.com/86611917/175793241-c6217fe1-9244-4ecc-b33c-7fb664d4a689.png)
 
<br/>

1. 멧돼지 피해는 실시간 처리가 중요하므로  
정확도가 높지만 60프레임(1초)를 처리하는데 약 150초가 걸리는 MegaDetector보다  
정확도가 조금 낮더라도 60프레임(1초)를 처리하는데 약 0.9초가 걸리는 Yolo모델을 사용.

<br/>

![카톡](https://user-images.githubusercontent.com/86835527/179016479-e3c7433c-c0a0-4fac-b4c9-e4d92f08fb4a.PNG)

<br/>

2. 피해동물(프로젝트 내에서는 멧돼지만 우선 적용) 감지가 되면 카카오톡 알림 메세지를 송출하도록 구현

<br/><br/><br/>
 
## 5. Summary

<br/>

평가지표 -> Macro F1 Score : 84.8%

Q. Why F1 Score?  

유해동물이라 판단한 것 중에서 실제 유해동물인 Precision  
실제 유해동물 중 유해동물이라 판단한 Recall  
두 지표의 조화평균인 f1-score

이지워치 : 높은 Recall. 하지만 낮은 Precision으로 인한 민원 다수 발생

따라서 trade-off관계인 두 지표의 조화평균인 f1-score을 사용하기로 결정.

<br/>

__참고사항__  

f1-score과 recall중에서 어느 것이 더 나은가는 정답이 없다.  

농작물의 피해를 무조건적으로 예방하려면 recall을 중요시하는게 맞으나  
민원이 너무 많이 발생하면 recall을 좀 낮추더라도 precision을 올려야한다.

상황에 따라 더 필요로 하는 지표를 사용해야 하는 것을 알고 있으며,  
이지워치의 단점인 소음 피해를 해소하기 위해 f1-score를 사용하였다.

<br/><br/><br/>

# 최종결과물
[위에서 확인하기](#딥러닝-기술을-이용한-유해동물-퇴치-알림-서비스)