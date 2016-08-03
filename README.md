# 은평 살맛나는 마을 지도!
## by [코드포은평](http://codeforep.org)

은평구에서는 거의 매년 다양한 주제로 지역에서 활발하게 활동하는 커뮤니티 및 단체들을 지도로 만들어 주민들에게 알리고 있습니다.
이 프로젝트는 2016년 2월 제작한 마을 공동체 지도를 보고 이런게 있었다니, 웹에 떠 있으면 더 많은 사람들이 볼 수 있지 않을까 하는 생각에서 시작됐습니다.

지역 마을 공동체 지도 예시

- 2016년 마을 공동체 지도 <http://www.ep.go.kr/CmsWeb/resource/image/epmain/sub2/town_large.jpg> - 출처 <http://www.ep.go.kr/CmsWeb/viewPage.req?idx=PG0000003073>
- 2013년 8월호 <http://azine.kr/m/data//201307291126013236.png>
- 2014년 은평마을학교1-2 <http://edu.eunpyeong.go.kr/data/formimg/2014은평마을학교1-2.jpg>

## 작업 과정

처음에는 서버를 마련해서 누구나 회원 가입해서 직접 주제에 맞는 장소나 커뮤니티를 올릴 수 있게 하자는 의견들이 있었습니다.
그러나 이 프로젝트에 참여한 대부분의 사람들은 기획, 개발, 디자인 등 실제 작업에 대해 어떤 곳으로부터 어떠한 지원이나 투자를 받지 않았습니다.
[2016년 은평마을지원사업](http://cafe.daum.net/_c21_/bbs_read?grpid=1QRHf&fldid=AtaB&contentval=00056zzzzzzzzzzzzzzzzzzzzzzzzz)에 코드포 은평이라는 사업명으로 지원 및 선정되어 90만 4천원의 비용을 지원 받았고 대부분 회의할 때 다과비로 사용했습니다.

매주 1시간의 만남과 그 외 여가 시간을 활용해 완성해야 하는 상황이라, 일을 복잡하고 거대하게 만들면 반드시 실패할 수 밖에 없었지요.
그래서 일단 인쇄된 마을 지도를 펼쳐 놓고 한 명씩 주제별로 나누어 구글 스프레드시트에 탭을 만들어 제목과 전화번호, 웹사이트, 위치 좌표 등을 노가다로 일제히 때려 넣었습니다.
사실 그렇게 오래 걸리지도 않았지요. 1시간 동안 하고 이후 짬짬이 남는 시간에 마무리를 해서 2주만에 데이터는 모두 확보할 수 있었습니다.

그 이후에는 어떻게 하면 손 안 데고 코 풀어 볼 수 있을까 고민하다가,
작업한 구글 스프레드시트를 데이터로 입력해 클릭 몇 번으로 바로 앱을 만들어주는 서비스를 활용해서 간단하게 바로 웹지도를 만들 수 있었습니다.
[초기 쌤플 지도앱](https://www.appsheet.com/start/bedbddbc-729f-4b90-a4f2-0bb966c7da3e)

이렇게 빨리 간단하게 힘들이지 않고 만들 수는 있었지만 주제별로 나누어 볼 수도 없고 기능이 제한적이어서 따로 만들자 이렇게 결론이 났고,
[썸맵](http://somemap.kr) 이라는 커뮤니티 맵핑 서비스를 사용해볼까하고 고민해보기도 했으나 그래도 코드포은평이라는 이름으로 뭔가 하자고 모였는데
기왕이면 직접 코드를 써서 올리는게 좋겠다고 의견이 모아져서 눈물을 머금고 독립형으로 [leaflet 라이브러리](http://leafletjs.com)를 활용해 코드를 직접 작성하려고 했습니다.

그러다가 귀찮아져서 아 이런 거 없을까 하고 깃헙을 뒤지던 중 아래 설명한 [BootLeaf](https://github.com/bmcbride/bootleaf) 프로젝트를 발견해서 바로 포크하고 도메인을 연결했습니다.
이후 짬짬이 코드 리뷰를 하면서 함께 노가다로 입력한 데이터를 [GeoJson](http://geojson.org) 형식으로 정리하고 지도도 외국 지도가 아니라 많이 사용하는 네이버 지도로 수정하고,
역시 네이버에서 구, 동 경계 데이터를 얻어서 (네이버 지도에서 은평구, 불광동 이런 식으로 검색하면 경계가 표시되요! 표시가 됐다는 말은 뭔가 로드했다는.. 인스펙터를 살짝 뒤져보면 어렵지 않게 복붙할 수 있습니다.) 로드하도록 코드를 수정하는 등의 과정을 거쳐서 결국 완성해버렸.... ㅜㅜ

## 개발

단순한 웹지도용 반응형 템플릿인 [BootLeaf](https://github.com/bmcbride/bootleaf) 프로젝트를 포크해서 은평구의 재밌는 장소와 커뮤니티 등의 위치를 마커로 찍었습니다.

[BootLeaf](https://github.com/bmcbride/bootleaf) - [예시](http://bmcbride.github.io/bootleaf/)

* [Bootstrap](http://getbootstrap.com/)
* [Leaflet](http://leafletjs.com/)
* [typeahead.js](http://twitter.github.io/typeahead.js/).

[Leaflet.KoreanTmsProviders](https://github.com/tontita/Leaflet.KoreanTmsProviders) - 리플렛용 네이버 지도 타일 레이어 확장.
(원래 다음지도로 해볼까 했는데 얼마전 카카오의 요청으로 다음 지도 타일 레이어가 삭제되었다는... ㅜㅜ)


