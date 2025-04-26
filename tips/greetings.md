[![License CC BY-NC-SA 4.0](https://img.shields.io/badge/license-CC4.0-blue.svg)](https://raw.githubusercontent.com/NVIDIA/FastPhotoStyle/master/LICENSE.md)
![Python 3.8](https://img.shields.io/badge/python-3.8-green.svg)
# 2025 세종과학예술영재학교 인문예술창작주간 ('Who am I?') How to utilize Generative Models, 그 두 번째 이야기 강의 안내사항 (25.05.07.-05.09.)

Instructor: **Taewon Kang (강태원)** (itschool [At] itsc [Dot] kr)

PhD Student @ [University of Maryland, College Park (UMD, 메릴랜드 대학교)](https://umd.edu/)

[Department of Computer Science](https://cs.umd.edu) (세종과학예술영재학교 3기 졸업생)

## 후배분들, 안녕하세요?
후배분들 안녕하세요? 처음 뵙겠습니다! 저는 2025 세종과학예술영재학교 (SASA) 인문예술주간에서 **"How to utilize Generative Models, 그 두 번째 이야기"** 강의를 맡게 된 University of Maryland (메릴랜드 대학교 (UMD)), College Park의 PhD Student (Computer Science) 이자 SASA 3기 졸업생인 강태원입니다! 

저는 고려대학교 컴퓨터학과를 학부 20학번 졸업최우등생(___magna cum laude___) 으로 졸업한 대통령과학장학생입니다! 제가 속해있는 미국 대학원인 UMD는 미국 메릴랜드(MD) 주 College Park에 위치해 있습니다. 아마 여러분이 2학년 때 글로벌 프론티어를 미국 동부로 오시면 워싱턴 D.C. 를 방문하게 될텐데, UMD는 워싱턴 D.C. 의 북동쪽에 위치해 있습니다. 강의를 들으시는 여러분들이 1학년(11기) 후배분들로 알고 있는데요, 우선 SASA에 입학하신 것을 진심으로 축하드립니다! 그리고 학교에 들어오셔서 첫 중간고사 보시느라 정말 고생 많으셨습니다! **사전에 아래 사항을 숙지하시고 시간을 내서 정독해주시길 부탁드리겠습니다!**

### 저희는 이틀 동안 무엇을 하게 되나요?
본 강의의 기본적인 방향은 강의 제목에도 적혀 있듯이 여러분이 이틀 동안 Generative Model을 잘 활용(utilize) 해서, 결과물을 도출하고, "AI가 예술을 할 수 있는가?" 라는 질문에 조금이나마 가까이 접근해 보는 것을 목표로 합니다. 텍스트로만 봤을 때 무슨 말인지 잘 안와닿을 수 있다고 생각합니다. 그러기에 제가 2018 인문예술주간에 진행했던 프로젝트 그리고 **과년도(2024년도) 프로젝트 영상** 을 이 링크에서 여러분들이 미리 확인해주시면, 제가 어떤 내용을 전달하고 싶은지 대충 짐작하실 수 있으실 거라 생각합니다.

* [2018 인문예술주간: GAN 진경산수화 프로젝트 페이지](http://itsc.kr/2018/10/27/2018-implementation-of-gan-jinkyeongsansu/)
* [2024 인문예술주간: How to utilize Generative Models 프로젝트 아카이빙](https://youtu.be/WeLmDt36v3M)

[![How to utilize Generative Models](https://img.youtube.com/vi/WeLmDt36v3M/0.jpg)](https://www.youtube.com/watch?v=WeLmDt36v3M) 

여러 생성모델들을 테스트해 본 결과, 본교 GPGPU 서버를 포함한 현실적인 GPU 리소스 문제 그리고 실행 가능한 코드 등 여러 가지 요소를 고려하여 강의에서는 크게 Generative Model 중 Image-to-Image, Image-to-Video, 그리고 Text-to-Video task를 수행하는 Diffusion Model을 다루고자 합니다. 세 모델의 역할은 다음과 같습니다.

* Image-to-Image Diffusion: 원본 이미지와 문장(프롬포트)이 주어졌을 때, 원본 이미지를 문장에 맞추어 변형한 새로운 이미지를 생성함

* Image-to-Video Diffusion: 원본 이미지와 문장(프롬포트)이 주어졌을 때, 원본 이미지를 문장에 맞추어 변형한 새로운 비디오를 생성함 [예시 링크 확인](https://i2vgen-xl.github.io/)

* Text-to-Video Diffusion: 문장(프롬포트) 가 주어졌을 때, 문장을 기반으로 새로운 비디오를 생성함

조금 생소하게 느껴질 수 있습니다만, 제목에서 언급했듯이 여러분이 해야할 일은 알고리즘을 이해하는 것보단 **이 알고리즘을 어떻게 이틀동안 활용(utilize)해서 독창적인 결과를 만들지에 대해서만 중점적으로 고민해 주시면 됩니다.**

예를 들어, Image-to-Video Diffusion 모델을 활용하면 이미지와 가이드를 주는 프롬포트를 활용해 비디오를 제작할 수 있기에 움직이는 사진을 Diffusion Model로 제작하실 수 있으실 겁니다. [시중에 움직이는 그림책도 있죠?](https://www.yes24.com/Product/Goods/104480787) 우리 학교에 있는 정지된 미술작품들을 움직이도록 만드는 방향이 하나의 아이디어가 될 수 있습니다. (실험 결과에 따라 정지된 미술작품 내 캐릭터만 움직이는 스토리텔링도 구현해 볼 수 있을 듯 합니다)

### 저희에게는 어떤 지원이 이루어지나요?
1. **올해는 학교에서 Google Colab Pro (USD 9.99 달러 상당) 유료 계정을 지원** 합니다. 유료계정 권한을 못 받으신 분께서는 저희 담당 지도 선생님께 요청해주시길 부탁드립니다!
2. **Adobe Premier Pro 동영상 제작 툴을 사전에 받아오시길 부탁드립니다.** 학교 Adobe 라이센스 관련해서는 교수학습지원부 관련 선생님께 여쭤보시면 좋을 것 같습니다!

여러분이 실험을 하면서 겪을 수 있는 시행착오는 제가 최대한 배제해두었습니다. 우선 앞서 언급한 세 알고리즘에 대해서는 실행 가능한 코드를 제가 확보해두었고, 그 코드는 여러분의 Google Colab (무료버전 포함) 으로 에러수정 없이 편리하게 실행하여 결과를 확인할 수 있도록 제가 설계해두었습니다. 또한 모두 사전에 학습된 모델(pre-trained model) 이 있기에 학습과정이 따로 필요 없고, 바로 결과도출을 진행하므로 Generative Model 학습에 걸리는 시간에 대한 부담이나 불안감 또한 없을 것입니다. 

이렇게 제가 진행하는 이유는 **저희에게 주어진 이틀이 굉장히 짧기 때문** 입니다. 여러분이 **아무런 사전준비 없이** 강의에 들어와서 수업을 듣고, 기본적인 알고리즘 실행방법에 대한 설명을 수업시간에 모두 들은 이후부터 아이디어를 도출하고 데이터를 수집하게 되면, **아마 시간이 많이 촉박하실 수 있습니다.** 따라서, 아래 내용은 인문예술주간 기간 전 사전에 준비해주시길 부탁드립니다!

* 앞서 언급된 알고리즘을 통해서 어떤 작품을 만들고 싶은지 아이디어를 대략적이라도 **여러 가지 최대한 고민해올 것**
* 작품 제작에 필요한 사진 (원본 이미지) 들을 **여러 장 충분히 확보** 할 것
* 작품을 최종적으로 동영상으로 가공할 때 **필요한 음악이나 기타 요소들** 준비할 것 (가능하면)

이렇게 진행하는 이유는 Generative Model이 후배분들이 원하는 대로 한번에 동작하지 않을 확률이 높기 때문입니다. 설정값 (파라미터) 그리고 프롬포트를 여러 차례 변경하는 과정을 통해 사진에 알맞은 적절한 값을 찾아야 하고, 또 그렇게 했는데 의도한 결과가 도저히 나오지 않으면 다른 아이디어를 시도하거나 조금 변형해야 할 가능성이 있습니다. **그렇기에 작품 아이디어와 아이디어에 필요한 사진 확보는 사전에 조금이라도 진행해주시길 강력 권장드립니다! 먼 미국에서 날아가서 여러분을 도와드리는 만큼 좋은 작품들 많이 만들고 가셨으면 좋겠습니다!** 

### 전시는 어떻게 진행되나요?
2일차 종료 이후 3일차 전시에서는 여러분 동영상 작품을 수합하여 SASA에서 제공하는 노트북에 넣고, SASA 로비에서 상영하는 형태로 전시를 진행할 계획입니다. 그리고, 여러분의 프로젝트를 아카이빙하여 객관적인 자료로 남길 계획입니다. 그래서 2일차 오후에는 제가 보여드린 것처럼 여러분 개개인 또는 팀의 동영상이 나와야 합니다. 그렇기에, **Adobe Premiere Pro 등 작업하기에 편하신 동영상 제작툴을 반드시 컴퓨터에 설치해두시고, 소프트웨어 사용법을 익혀오시면 큰 도움이 될 것 같습니다!**

### 아직도 감이 잡히지 않아요.
추가로 더 궁금하신 사항이 있으시다면 제 이메일 또는 인문예술주간 전용 오픈채팅방으로 연락주세요.

## 저에 대해 더 궁금하신가요?
* 미국 워싱턴 D.C. 그리고 UMD 인근에서 거주하고 있습니다.
* 현재 CS 박사과정 1년차고, Computer Vision 그리고 Artificial Intelligence 분야 연구를 하고 있습니다.
* 2025 여름학기에 Adobe Research에서 research intern으로 근무할 예정입니다!
* [Website](http://itsc.kr)
* [Facebook](https://www.facebook.com/taewonkang.13/)
* [LinkedIn](https://www.linkedin.com/in/taewon-kang/)

## LICENSE
Awesome Tips를 포함한 본 실습자료 일체 무단전재와 복사, 배포, 상업적인 용도의 이용을 금지합니다.

## Reference
