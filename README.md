Deployment


Vercel 배포 URL : https://assign05-c01-22500698.vercel.app/


Key Learning


이번 주에 배운 핵심 내용 3가지


CRUD Service


구현한 서비스 주제 : 상품관리 서비스
사용하는 데이터 Field : id, name, description, category, date, price
Create / Read / Update / Delete 구현 방법


1. Create


유저가 먼저 form을 입력하게 하고나서, checkValidity로 html 태그에 적어둔 조건에 맞는 지 확인합니다. 그 후 인풋에 넣은 데이터를 각 인풋에 맞춰서 value를 뽑고, 미리 만들어뒀던 products Array에 푸시합니다. 그후에 다음 데이터를 적을 수 있게 모든 인풋란을 초기화합니다.


2. Read


이미 만들어둔 products의 정보를 가지고, products에 있던 데이터 갯수만큼 반복할 수 있게 반복문을 만들어서, 먼저 데이터 객체 내의 정보들을 하나의 변수로 모은다음, 수정 버튼과 삭제 버튼을 같이 만들고, 그후 데이터 객체 정보를 먼저 보여주고, 그 자식으로 수정버튼과 삭제버튼을 이어서 만드는 작업을 반복합니다. 


3. Update


먼저 수정 버튼을 누르고, 유저가 입력했었던 정보의 value를 다 인풋에 입력합니다. 이때 value는 데이터 저장이 되어있는 products에서 가지고옵니다. 그후에 add 버튼을 누르면 그 인풋에 적어둔 수정본의 내용으로 실제 저장소에 있는 products 정보들이 바뀝니다. 그후 다시 products에 있는 정보들을 보여주면 수정된 내용으로 나오게 하는 로직입니다.


4. Delete


삭제 버튼을 누르면 먼저 confirm()함수가 삭제할건지 안할건지 물어봅니다. 그후 확인을 누르면, splice()함수로 실제 배열에서 data를 선택해서 삭제해주고, 다시 render()함수를 불러주면 삭제된 배열이 반영된 내용이 나옵니다.


JavaScript


이번 과제에서 사용한 주요 JavaScript 기능을 설명합니다.


querySelector() : 입력해둔 조건에 맞는 하나의 요소만 가지고오는 기능을 수행합니다. 이걸 통해서 input값과 button들을 가지고올 수 있습니다.
addEventListener() : 실제 유저와의 상호작용을 할 수 있는 event가 일어났을때 어떤 기능을 할건지를 요소들에 붙이는 기능을 수행합니다.
createElement() : 입력해둔 html 태그들을 동적으로 생성하는 기능을 구현합니다.
appendChild() : 선택한 부모에 자식노드를 붙이는 기능을 수행합니다.
Array : 대표적인 자료구조중 하나로, 인덱스가 존재하는 배열을 기능합니다.
splice : 선택한 배열의 특정 요소를 삭제, 수정 의 기능들을 합니다.


AI / Search Usage


사용한 AI 또는 검색 도구 : chatgpt, google
어떤 문제를 해결하기 위해 사용했는지 : 
1. Array에서 어떻게 추가하고(push), 삭제하고(pop), 조건에 맞춰서 수정하는 지(splice : 원본배열을 수정, filter : 수정된 새로운 배열을 반환)를 모르겠어서 그 부분에 있어서 google과 chatgpt로 학습했습니다.
2. editProduct(product product)를 사용했었는데, 계속 에러가 나서 gpt한테 물어보니 javascript에서는 매개변수를 생성할때, type변수명을 사용하는게 아니라 그냥 변수명만 사용하면 되는 줄 몰랐었습니다. 그 부분에 대해서 학습했습니다.
3. 수정 버튼을 눌럿을때 input에 다시 채워넣기 위해서, newProduct.value.split(" ")을 사용해서 각 값을 쪼개서 사용했었는데, 수정하고 넣다보니 계속 id만 제대로나오고 undefined가 나오고, 내용도 잘안나와서 어떻게 해야할지 모르겠어서 gpt에게 물어봤었는데, 이 코드에 문제점은 <li>는 input과 다르게 값의 value를 가지는 요소가 아니기에 undefined가 일어난다는 것이었다. 
4. 어떻게 Add버튼을 눌렀을때, edit을 저장하는지인가 혹은 new 제품을 저장하는지를 파악할지를 모르겠어서 그 문제를 해결하기 위해서 gpt를 사용했습니다.


실제 코드에 어떻게 적용했는지 - 
1 - push함수를 사용해서, 실제로 유저가 Add버튼을 눌렀을때, 입력을 객체로 만들어 products 배열에 추가했고, 유저가 삭제버튼을 누르면, 그 삭제버튼의 위치인 i를 기준으로 원본 배열에서 splice를 사용해서 제거했습니다. 
2 - 결국 이 코드는 따로 빼서 안만들었지만 javascript에서 매개변수르 어떻게 선언하는지 알게되었습니다.
3 - 더 단순하게 저장된 저장소에서 이미 선택된 i를 사용해서 value를 가지고오는 방법을 사용.
4 - 전역변수 하나를 생성해서, 그 생성한 변수의 default값이 변했다면 수정하는 것으로 보고, 만약 default값이라면 저장하는 것이라고 보는 방법을 사용했습니다.


새롭게 이해한 내용
이번에 Javascript와 css, html을 다양하게 써보면서 실제로 addEventListener를 사용한 function을 조작하는 방법이라던지, 전역변수를 실제 코드에 사용해서 조건문을 수행한다던지 하는 새롭게 알게된 내용이 많았습니다. 


Problem & Solution

구현 중 발생한 문제와 해결 방법

맨처음에 add 기능을 구현중에서 분명히 코드를 잘짰는데 add 버튼을 눌러도 아무런 반응이 없었는데, 알고보니 name부터 date까지 querySelector가 아니라 createElement를 사용중이었습니다. 그래서 바꾸고난 후엔 제대로 동작을 완료했습니다.


Reflection

이번 과제를 통해 새롭게 알게 된 점 또는 궁금한 점




이번 과제를 통해서 appendChild와 createElement를 통해서 동적 페이지를 만들 수 있고, 이 동적 엘리먼트들에 className까지 줘서 css를 특정 엘리먼트에 디자인줄 수 있다는 점을 새롭게 알게된 점입니다.
