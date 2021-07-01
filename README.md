# 🤓 WebSquare에 대해 알아보자.
### ✏️ WebSquare5
- namespace 기반의 코딩
- default로 사용하는 객체명 : scwin
- <form>을 이용한 전송, 이동 방식으로 통신하지 않고 Submission이라는 객체를 생성하여 통신
- Tool 상단 손가락 버튼 클릭, 그리기 모드를 Absolute로 적용
- Design 컴포넌트 배치시 왼쪽 Palette View에서 사용하고자 하는 컴포넌트 선택하여 사용
- Component 모드 선택시 websquare5의 모든 객체 확인 가능
- 예) inputbox 생성 후 실제 browser에서 실행시키려면 tool 상단 빨간색 실행 버튼 or F7
- 제공되는 브라우저 말고 크롬 등으로 실행하고 싶으면 빨간색 실행 버튼 옆 버튼 클릭하고 경로 지정해서 등록
- 상세 기능 도움말 F1
- 속성 제어 : 우측 Property 확인하기
- id 등록후 script 이동, id 입력후 . 누르면 해당 컴포넌트가 사용할 수 있는 API 목록 확인 가능(ctrl+space)  
	
  ex)  
  scwin.onpageload = function() {  
       ipt1.setValue("356752");  
  };  
	
  initValue 속성과 함께 적용했을 경우 onPageload 부분의 수행시점은 모든 컴포넌트를 그려준 이후에 반영되므로 onPageload 부분에서 실행한 setValue를 통해 적용한 값이 최종 반영됨.
- 객체 선택>우클릭>이벤트 추가 or Property에서 파란색 P버튼 말고 빨간색 E버튼 클릭>선택후 script 버튼 누르면 자동으로 생성됨  
  
  ex)  
  scwin.ipt1_onviewchange = function(info) {  
       debugger;  
       alert(info.newValue);  
  };  
	
  브라우저 화면>우클릭>검사>console>info;입력하면 {oldValue:"98654", newValue:"356752"} 출력됨  
- 컴포넌트의 style 제어 : Help 옆 style 선택 ex)text-align: right;  
  파일내에 직접 css를 사용하는 internalCSS를 적용한다면 style 우측 Add Internal Style 버튼 클릭>script에 자동 생성됨  
	
  <style type="text/css"><![CDATA[   
       .aa {background-color: orange;}  
    ]]></style>   
  aa 클래스를 Property에 class 속성에 적용하면 class 적용됨.  
  외부 css 파일을 import : style 우측 import External Style 버튼 클릭  
  <?xml-stylesheet href="/src/main/webapp/resources_ux/css/common.css" type="text/css"?> 이렇게 소스 상단에 적용됨  
  Design 화면>우클릭>import External Style클릭해도되고 Project Explorer에서 Design 화면에 드래그드롭해도 됨.  
- 우측 하단 Component : Component를 통해 생성된 파일의 전체적인 구조 파악 가능, 컴포넌트 id 및 class 등으로 검색 가능  
  head - javascript 로직, data객체 및 통신 객체 등  
  body - 화면 상 그려진 컴포넌트  
- Snippet : 미리 디자인 된 컴포넌트 쉽게 복사 사용 가능, 퍼블리셔가 생성하여 전달하여 우측 import Snippets 버튼 클릭후 개발Tool에 import하여 사용
  
### ✏️ 화면 생성
- New>WebSquare Page
- 스크립트는 javascript 로직 작성
- 파일을 생성하면 onPageload : 페이지 로딩 후 실행  
  onPageunload : 페이지 종료 후 실행 이벤트가 자동 등록됨.

### ✏️ DataCollection
- data 객체를 생성하고 관리
- DataMap : 단건 data 관리
- DataList : 다건 data 관리
- LinkedDataList : 생성된 dataList에서 별도의 조건을 주어 filter 된 data를 확인(viewer용으로 제한적)
- AlliasDataMap : Page Coding에서 자식에서 부모의 dataMap 객체를 참조할 때
- AlliasDataList : Page Coding에서 자식에서 부모의 dataList 객체를 참조할 때

### ✏️ Submission
- 웹스퀘어의 통신 객체 생성 및 관리

### ✏️ Source
- Design, Script, DataCollection, Submission에서 정의한 내용을 하나의 xml 파일로 확인
- 가급적 코딩은 Script를 이용하기

### ✏️ 속성
- initValue : 초기값 부여
- displayFormat : 숫자 형태의 format 적용(dataType : number, displayFormat : #,###) 단, inputbox에 fucus가 없는 경우에만 적용  
	        focus 유무와 상관 없이 적용시키려면 applyFormat 속성 값을 all로 변경
- id : API에 대한 제어를 위해 객체에 대한 id를 속성으로 적용. websquare의 컴포넌트는 id를 부여하면 해당 id가 페이지 내에서 전역 변수로 자동 등록됨으로, id 기준으로 API를 작성하면 됨.  
     ipt1(객체의 id) == document.getElementById("ipt1")

### ✏️ 컴포넌트
- Inputbox : 다양한 Property를 지원하여 간단하게 value 제어 가능
- Spinner : 버튼을 사용하여 텍스트 필드의 값의 증감을 조절. Property로 최소값, 최대값, 증감의 범위 등을 간단하게 설정 가능
- Secret : HTML의 input type = "password"와 유사한 인터페이스 제공, 입력된 value가 [*]로 화면에 표시됨
- InputCalendar : Calendar 컴포넌트와 Input 컴포넌트의 복합 컴포넌트. 달력에서 선택한 날짜가 Input 컴포넌트에 출력되며 validCheck 속성을 이용해 유효한 날짜인지 체크 가능
- textarea : 글쓰기 가능
- Editor : CK Editor 최상위 버전 내장
- 폼을 구성하는 컴포넌트로 텍스트나 이미지 출력용 컴포넌트  
  TextBox : 긴 문장 구성시 사용 권장  
  Span : TextBox보다 가벼움. HTML span Tag와 동일. 짧은 글자나 변경되는 값에 사용  
  Image : 이미지 출력  
- Checkbox : 나열된 항목 다중 선택
- SelectBox : 여러 개의 항목 중 1가지 선택
- MultiSelect : Ctrl Key로 여러 항목 선택 가능, 모바일에서 불가능
- CheckCombobox : selectbox + checkbox 항목 다중 선택
- AutoComplete : SelectBox 컴포넌트와 같이 나열된 목록에서 항목 선택 가능, 사용자가 입력한 값을 자동완성 및 검색기능 제공
- PageList : page 관리 컴포넌트. 일반적으로 GridView와 함께 사용
- Calendar : 달력 종류 3가지
- ScheduleCalendar : 일정을 달력에 출력
- Trigger : type에 따라 이미지 형태의 버튼과 button 형태로 사용 가능
- Anchor : hyperlink 정의 가능, CSS 적용하여 버튼으로 사용
- Upload : 단건의 파일 업로드
- Multiupload : 다건의 파일 업로드
- Group : 여러 컴포넌트를 그룹화시킬 수 있는 레이아웃용 컴포넌트. 하위에 컴포넌트들을 배치시킬 수 있음. 입력용 컴포넌트의 value를 초기화(init) 기능 등 가능.  
             value를 가질 수 없으므로 value 설정 필요시 Textbox 컴포넌트와 함께 사용
- TableLayout : 표 만들 때 사용
- Generator : 특정 영역이 반복되어 표현되거나 동일한 영역을 동적으로 추가/삭제해야 할 때 사용하는 컴포넌트. for문과 유사.
- SlideHide : 특정 영역을 사용자가 지정한 이벤트가 발생하면 좌, 우 또는 상, 하 중 사용자가 지정한 방향으로 영역이 슬라이드 되면서 보이거나 숨김처리 가능. ex)퀵 메뉴
- Switch : 특정 영역에 여러 개의 case로 화면을 구성하고 화면을 동적으로 변경할 수 있음(슬라이드)
- Accordion : 좁은 화면에서 화면을 접고 펼치면서 구성 할 수 있음
- IFrame : 부모 페이지와 id가 중복된 컴포넌트가 있어도 사용 가능. 별도의 브라우저 영역이므로 페이지 리소스를 IFrame 개수만큼 내려받기 때문에 많을수록 로딩 느려짐
- WFrame : JSP의 include처럼 웹스퀘어 xml 화면 파일을 현재 화면에 include할 때. 공통이 되는 top, left의 메뉴 구성시.
- TabControl : 다건의 탭과 콘텐츠 생성 가능, 동적으로 탭 생성 및 삭제
- WidgetContainer : 구성된 컨테이너의 위치 배열 정보를 import/export 가능. 접속된 사용자별로 화면 구성 개인화 처리 가능.
- GridView : DataCollection을 Binding하여 편리하게 데이터 표현. 행과 열을 정의하여 그리드 표현. 헤더, 바디, 풋터를 설정하여 활용 가능. 각 컬럼마다 다른 타입 지정 가능.  
  정렬 : GridView의 헤더 클릭시 데이터 정렬 지원. Property에서 sortable 옵션을 정의하여 사용 가능  
  필터 : 대상건의 값을 사용자가 조건을 정의하여 필터 처리 가능. Property에서 useFilterList 옵션을 정의하여 사용 가능  
  컬럼이동 : GridView에서 헤더를 마우스로 drag하여 컬럼을 이동할 수 있음. Property에서 columnMove 옵션을 정의하여 사용 가능  
  소계(subtotal) : 대상건의 일정그룹의 값을 처리  
  합계(footer) : GridView 전체의 연산 처리  
  inputType이 expression일 경우 계산식함수(SUM, AVG, MIN, MAX, COUNT) 사용 가능  
  ExcelDownload : GridView의 제공되는 데이터 포맷 그대로 엑셀 다운로드 가능. chart 구성하는 스크립트 작성해서 다운로드시 차트 추가 가능  
- Pivot : 행과 열을 변경하여 데이터 표현할 때 사용
- Treeview : 계층 구조를 가지는 데이터를 Tree 형태로 출력. 각 노드에 checkbox와 image를 넣을 수 있고 마우스 드래그 드롭 이용해 Data(노드)를 주고 받을 수 있음.
- FusionChart : InfoSoft Global사의 제품으로 FusionChartXT가 OEM 라이센스로 제공되고 있음.
- MapChart : 행안부 데이터를 이용한 지도 형태의 차트  

### ✏️ 그리기모드
- Block level element : Group, Textbox, GridView 등
- Inline level element : Span, InputBox, Trigger, Anchor 등
- 두가지 방법을 가장 많이 씀.  
  Static Position : position이 정의되지 않았거나 position:static;으로 정의된 경우. 소스(코드)의 순서와 display 값에 따라 배치되며 위치 속성(left,top,right,bottom)들은 무시됨.  
  ex) style="width:150px; height:24px;"  
	
  Absolute Position : 기준 점(left,top,right,bottom)을 잡고 크기(width, height)를 지정하여 배치하는 방법. 렌더링 보정 위해 모든 컴포넌트의 top, left 값을 비교하여 렌더링 순서를 일일이 맞춰야 하는 불편함이 있기 때문에 선호하지 않는 방법. static Mode를 많이 사용함.    
  ex) style="position:absolute; left:20px; top:10px; width:150px; height:24px;"  
	
- Group과 같은 Block level 요소에서는 width 값을 주지 않으면 알아서 100%로 맞춰서 그려주는 성질이 있음. height 값도 마찬가지.
- 객체 생성할 때 margin-right:300px;을 주어 맨 오른쪽 배치하려해도 가장 오른쪽으로 배치되지 않음 -> 객체 생성시 float 기능 사용하기. float: right 선택
- inline level에 float이 적용되어 있으면, 이를 감싸는 Block level에서는 반드시 overflow 속성이 지정되어 있어야 함.   
  ex)overflow: hidden;
- 각 Group과 browser간의 간격을 주려면 각 Group들을 모두 선택후 우클릭->Group 눌러 최상단 Group 생성, 최상단 Group에 padding 적용하여 구현
- tableLayout으로 테이블 형태 그리기
- 화면 사이즈가 줄어들었을 때 가변적으로 디자인 변경(적응형 웹) : table선택 후 속성에서 adaptive -> layout, adaptiveThreshold -> 700(반드시 숫자만)으로 지정
- GridView : height 값은 꼭 지정해야만 영역을 표시함
- Snippet에 폴더를 만들어서 그려낸 Group을 하나하나 Snippet에 이름을 지정한 후 저장해서 다른 파일에서도 가져다가 사용 가능

### ✏️ 데이터 바인딩
1. 기본값 셋팅이 필요한 Component들에 대해 모두 id 부여(해당 id가 전역변수로 인식되어 script에서 바로 사용 가능)  
  공백 불허, '-' 사용 권장하지 않음, unique한 id 사용하기, 
2. inputbox에 script로 값을 입력할 때는 setValue API 사용  
	
	[예제]  
   	scwin.onpageload = function() {  
            ui_name.setValue( "Test" );  
            ui_date.setValue( $p.getCurrentServerDate( "yyyyMMdd" ) ); //오늘 날짜를 구해오는 API  
       }  
	
3. 하드코딩 방법  
  selectbox, radio, checkbox를 더블 클릭 -> Component 편집창 열림 -> + 버튼 눌러서 이름, 값 입력 후 저장. 하단에 All Option 체크하면 -전체- 도 표현됨.     
  Choose Option 하면 -선택- 이라고 표현됨.(label 변경 가능), All과 Choose 동시 적용 가능  
  radio 설정시 Span Direction : rows로 하면 가로 방향으로 표현됨. none이나 cols는 세로 방향, Span Count는 지정된 열과 행의 갯수 표시  
4. API를 이용한 방법  
  addItem API 사용  
	
	[예제]  
  	scwin.onpageload = function() {  
            ui_name.setValue( "Test" );  
            ui_date.setValue( $p.getCurrentServerDate( "yyyyMMdd" ) ); //오늘 날짜를 구해오는 API  
            ui_gender.addItem( "F", "여자", 0 );  
	ui_gender.addItem( "M", "남자", 1 );  
       }  
	
5. dataList와 연동하는 방법  
  DataCollection에 DataList나 DataMap을 생성.   
  map은 key, list는 column으로 구성됨.  
  key나 column을 입력해준(ex. id : code, name name : 코드, 코드명 dataType : text, text) 후 맨 하단에 use data를 체크해서 초기값 넣어서 확인해보기  
  바인딩 할 체크박스 더블 클릭후 BindItemSet체크  
  - NodeSet : 연결하려는 dataList명(ex. data:dc_role)  
  - Label : 항목으로 보여질 컬럼명(ex. name)  
  - Value : 값으로 보여질 컬럼명(ex. code)  
  script에 값을 넣어주기(data 형식에 따라)  
  setData : 1차원 Array  
  setXML : xml Object  
  setJSON : json Object  
	
	[예제]  
   	scwin.onpageload = function() {  
            ui_name.setValue( "Test" );  
            ui_date.setValue( $p.getCurrentServerDate( "yyyyMMdd" ) ); //오늘 날짜를 구해오는 API  

            ui_gender.addItem( "F", "여자", 0 );  
	ui_gender.addItem( "M", "남자", 1 );  
  
	var jsonData = [{"code":"01", "name":"총괄"}  
		       ,{"code":"02", "name":"부서담당"}  
		       ,{"code":"03", "name":"공통"}  
		       ,{"code":"04", "name":"개발"}  
		       ,{"code":"05", "name":"디자인"}  
		       ];  
  
	dc_role.setJSON( jsonData ); //json 객체, 뒤에 false가 default로 생략 가능(기존 data를 지우고 신규 data만 적용, true는 기존 data에 붙여넣기 적용)  
	//data 객체와 binding할 때  
	ui_role.setNodeSet( "data:dc_role", "name", "code" );  
       };  
	
	
