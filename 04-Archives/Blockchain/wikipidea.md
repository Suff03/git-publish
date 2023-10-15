# 블록체인


[![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/Blockchain.svg/150px-Blockchain.svg.png)](https://commons.wikimedia.org/wiki/File:Blockchain.svg)

블록체인의 대형

**블록체인**([영어](https://ko.wikipedia.org/wiki/%EC%98%81%EC%96%B4 "영어"): block chain은 관리 대상 [데이터](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0 "데이터")를 '블록'이라고 하는 소규모 데이터들이 [P2P](https://ko.wikipedia.org/wiki/P2P "P2P") 방식을 기반으로 생성된 체인 형태의 연결고리 기반 분산 데이터 저장 환경에 저장하여 누구라도 임의로 수정할 수 없고 누구나 변경의 결과를 열람할 수 있는 [분산 컴퓨팅](https://ko.wikipedia.org/wiki/%EB%B6%84%EC%82%B0_%EC%BB%B4%ED%93%A8%ED%8C%85 "분산 컴퓨팅") 기술 기반의 원장 관리 기술이다이는 근본적으로 분산 데이터 저장기술의 한 형태로, 지속적으로 변경되는 데이터를 모든 참여 [노드](https://ko.wikipedia.org/wiki/%EB%85%B8%EB%93%9C_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99) "노드 (컴퓨터 과학)")에 기록한 변경 리스트로서 분산 노드의 운영자에 의한 임의 조작이 불가능하도록 고안되었다. 블록체인 기술은 [비트코인](https://ko.wikipedia.org/wiki/%EB%B9%84%ED%8A%B8%EC%BD%94%EC%9D%B8 "비트코인")을 비롯한 대부분의 암호화폐 거래에 사용된다 [암호화폐](https://ko.wikipedia.org/wiki/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90 "암호화폐")의 거래과정은 탈중앙화된 전자장부에 쓰이기 때문에 블록체인 소프트웨어를 실행하는 많은 사용자들의 각 컴퓨터에서 [서버](https://ko.wikipedia.org/wiki/%EC%84%9C%EB%B2%84 "서버")가 운영되어, 중앙에 존재하는 은행 없이 개인 간의 자유로운 거래가 가능하다.

## 기본 원리

블록체인 아키텍처의 핵심적인 장점은 다음과 같은 것들이다.

블록체인은 대규모의 노드들 사이에서 각 노드에 분산 저장된 장부의 데이터를 항상 있도록 하는 합의 수렴 [알고리즘](https://ko.wikipedia.org/wiki/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98 "알고리즘")으로 볼 수 있다. 이러한 능력은 노드가 익명으로 실행되거나, 연결이 좋지 않거나, 심지어 신뢰할 수 없는 운영자가 참여하는 것도 가능하게 한다.

### 탈중앙

[암호화폐](https://ko.wikipedia.org/wiki/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90 "암호화폐")의 노드는 부분 또는 전체의 블록체인을 가지고 있다. 이것이 페이팔과 같은 시스템에서 필요로 하는, 중앙 집중형 [데이터베이스](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4 "데이터베이스")를 가지고 있을 필요가 없게 한다.

일반적인 장부에는 수표나 영수증 또는 약속어음의 교환내역이 기록되는 반면에, 블록체인은 그것 자체가 거래장부인 동시에 거래증서(수표, 영수증, 약속어음)이다. 비트코인에서는 거래들의 지불되지 않은 결과의 형태로 존재한다고 표현한다.

"지불인 갑이 00원을 수취인 을에게 보내다" 형식의 거래는 소프트웨어 앱(비트코인 지갑앱 등)을 통해 블록체인 네트워크에 뿌려진다. 블록체인 네트워크의 노드들은 거래를 검증한 다음, 자신의 장부에 거래를 추가한다. 그리고 이 거래가 추가된 장부를 네트워크의 다른 노드들에 뿌린다

### 개방형

#### 비허가형
비허가형의 공개형 블록체인망의 장점은 불량한 사용자로부터의 보안을 요하지 않으며 [접근 제어](https://ko.wikipedia.org/wiki/%EC%A0%91%EA%B7%BC_%EC%A0%9C%EC%96%B4 "접근 제어")가 필요없다는 점이다. 즉, [전송 계층](https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EA%B3%84%EC%B8%B5 "전송 계층")으로서 블록체인을 사용하여 다른 곳의 신뢰나 승인 없이 애플리케이션을 네트워크에 추가할 수 있음을 의미한다.[[10]]

#### 허가형[[편집](https://ko.wikipedia.org/w/index.php?title=%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8&action=edit&section=5 "부분 편집: 허가형")]

![<nowiki />](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Crystal_Clear_app_xmag.svg/16px-Crystal_Clear_app_xmag.svg.png) [분산원장](https://ko.wikipedia.org/wiki/%EB%B6%84%EC%82%B0%EC%9B%90%EC%9E%A5 "분산원장") 문서를 참고하십시오.

허가형 블록체인은 접근 제어 계층을 사용하여 네트워크 접근자를 관리한다.[[11]](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8#cite_note-btit-11)

## 종류[[편집](https://ko.wikipedia.org/w/index.php?title=%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8&action=edit&section=6 "부분 편집: 종류")]

- 공개 블록체인(Public blockchain, 개방형 블록체인): 접근 제한이 전혀 없는 블록체인.
- 비공개 블록체인(Private blockchains, 전용 블록체인): 특정 권한이 부여된 비공개 블록체인.[[11]](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8#cite_note-btit-11)
- 하이브리드 블록체인(Hybrid blockchain): 중앙식, 탈중앙식 기능을 모두 갖춘 블록체인.[[12]](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8#cite_note-12)

## 이중 지불 방지[[편집](https://ko.wikipedia.org/w/index.php?title=%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8&action=edit&section=7 "부분 편집: 이중 지불 방지")]

암호화폐들은 신뢰할 수 없는 제3자에 의한 시간표시거래를 블록체인에 추가하는 것을 피하기 위해, [작업증명](https://ko.wikipedia.org/wiki/%EC%9E%91%EC%97%85%EC%A6%9D%EB%AA%85 "작업증명")([proof-of-work](https://ko.wikipedia.org/w/index.php?title=PoW&action=edit&redlink=1 "PoW (없는 문서)")) 또는 [지분증명](https://ko.wikipedia.org/wiki/%EC%A7%80%EB%B6%84%EC%A6%9D%EB%AA%85 "지분증명")([proof-of-stake](https://ko.wikipedia.org/w/index.php?title=PoS&action=edit&redlink=1 "PoS (없는 문서)")) 같은 다양한 시간표시 방법들을 사용한다. 이것은 누구나 쉽게 [이중지불](https://ko.wikipedia.org/w/index.php?title=%EC%9D%B4%EC%A4%91%EC%A7%80%EB%B6%88&action=edit&redlink=1 "이중지불 (없는 문서)")되는 돈의 문제를 회피할 수 있게 한다.[[13]](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8#cite_note-kopstein-13)

## 개발과정[[편집](https://ko.wikipedia.org/w/index.php?title=%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8&action=edit&section=8 "부분 편집: 개발과정")]

블록체인의 첫 구현체 개발은 [비트코인](https://ko.wikipedia.org/wiki/%EB%B9%84%ED%8A%B8%EC%BD%94%EC%9D%B8 "비트코인")으로 시작되었고, 추가적으로 성능개선, 익명성 추가, 저장기능과 스마트 컨트랙([smart contract](https://ko.wikipedia.org/w/index.php?title=Smart_contract&action=edit&redlink=1 "Smart contract (없는 문서)")) 기능들이 개발되었다.[[14]](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8#cite_note-new_era-14) MIS 분야가 매우 중요한 역할을 하였다.