
## YOLOv4 Fine tuning 
[Fine tuning for person detection With Google Colab](https://colab.research.google.com/drive/1m2RY228H2zFbvkkoh2d7UdBVr9eaOWem#scrollTo=yAptWoq644la)




#### Procedure
1. Search Dataset for custom training (Keggle)
2.  Annotation with a tool (ex. labelimg)
    train:test  = 8:2 is   desirable
      To prepare Annotation tool >  [[Object Detection links#1. Image Annotation tool]]





[Darknet 명령어 링크.jp ](https://ichiya.netlify.app/posts/2019/12/22/_20191222.html)

#### Memos

---

**1주차 - 데이터 조사 및 라벨링:**

- **데이터 확보:** 실내 인간 이미지 데이터를 찾는 데 어려움을 겪었음.
 Keggle 등 다양한 검색 방법을 시도했지만, 원하는 데이터를 충분히 확보하기 어려웠음. 이틀은 걸린듯
- **LabelImg 활용:** LabelImg 사용 경험이 있었음에도 전부 까먹어서 헤맸음.
Anaconda 패키지 설치 및 Windows용 .zip 파일 다운로드 하여 사용하면 되었었음
- **Label Studio 평가:** LabelImg 대비 가능한 기능은 다양하지만 쉽게 사용하기가 어려워서 사용성이 떨어지는 것으로 느꼈음. 이후 새로 공부해서  활용할지 고민