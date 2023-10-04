---
title: 모던 자바스크립트 Deep Dive_배열
date: "2023-05-03"
description: 자바스크립트 공부하는 사람들은 모를 수 없는 그 책..❗️
tag: JS
---
[[JavaScript]]
## 27.1 배열이란?

배열(Array)은 **여러 개의 값을 순차적으로 나열한 자료구조**

-   사용 빈도가 매우 높은 가장 기본적인 자료구조
-   자바스크립트는 배열을 다루기 위한 유용한 메서드를 다수 제공한다.

![1](https://user-images.githubusercontent.com/87301268/235816699-19836b48-7cdc-435e-a56f-68d84d17815e.png)

-   배열이 가지고 있는 값을 **요소(element)** 라고 부르고 자바스크립트의 모든 값은배열의 요소가 될 수 있다.
-   배열의 요소는 **인덱스(index)** 를 가지며 배열은 요소의 개수 즉, **배열의 길이** 를 나타내는 **length** 프로퍼티를 갖는다.
-   배열은 인덱스와 length 프로퍼티를 갖기 때문에 for문을 통해 순차적으로 요소에 접근이 가능하다

![2](https://user-images.githubusercontent.com/87301268/235817003-01496df1-0e19-43ca-b6b1-2369be43e409.png)

하지만 자바스크립트에 배열이라는 타입은 존재하지 않는다. (배열은 객체 타입)

### 배열의 특징

-   `[]`, `Array 생성자 함수(new Array)`, `Array.of`, `Array.from` 메서드로 생성할 수 있다.
-   배열의 생성자 함수는 Array 이며, 배열의 프로토타입 객체는 Array.prototype이다.
-   배열은 객체지만 일반 객체와는 구별되는 독특한 특성이 있다
-   일반 객체와 배열을 구분하는 가장 명확한 차이는 값의 순서와 length 프로퍼티다

![](https://github.com/Choi-HyunHo/blog/assets/87301268/02b35a65-3490-47de-870c-58a074d3ed39)

## 27.2 자바스크립트 배열은 배열이 아니다.

자료구조에서 말하는 배열은

-   **동일한 크기의 메모리 공간이 빈틈없이 연속적으로 나열된 자료구조**를 말한다.
-   즉, 배열의 요소는 **하나의 데이터 타입으로 통일**되어 있으며 서로 연속적으로 인접해 있고, 이러한 배열을 **밀집 배열**이라 한다.

자바스크립트에서의 배열은

-   배열의 요소를 위한 **각각의 메모리 공간은 동일한 크기를 갖지 않아도 되며**
-   **연속적으로 이어져 있지 않을 수도 있다.**
-   배열의 요소가 연속적으로 이어져 있지 않는 배열을 **희소 배열**이라 한다.

> 즉, 자바스크립트의 배열은 일반적인 **배열의 동작을 흉내낸 특수한 객체**이다.

## 27.3 length 프로퍼티와 희소 배열

length 프로퍼티는 값은 요소의 개수, 즉 **배열의 길이를 나타내는 0이상의 정수를 값으로 갖는다.**

-   일반적인 배열의 length는 배열 요소의 개수, 즉 배열의 길이와 언제나 일치하지만
-   희소 배열의 length는 희소 배열의 실제 요소 개수보다 언제나 크다.

> 의도적으로 희소 배열을 만들어야 하는 상황을 발생하지 않으므로 희소배열 사용은 지양하는것이 좋다.

## 27.4 배열 생성

### 27.4.1 배열 리터럴

배열 리터럴은 0개 이상의 요소를 쉼표로 구분하여 대괄호([])로 묶는다.

-   배열 리터럴에 요소를 하나도 추가하지 않으면 length 가 0인 빈 배열이 된다.

![3](https://user-images.githubusercontent.com/87301268/235819467-aa4c0bf6-bee5-4c7c-a507-fe7cb56c9ed4.png)

### 27.4.2 Array 생성자 함수

Array 생성자 함수를 통해 배열을 생성할 수 있다

-   Array 생성자 함수는 전달된 인수의 개수에 따라 다르게 동작하므로 주의가 필요하다

![4](https://user-images.githubusercontent.com/87301268/235819760-04eff9b6-d6fd-4639-a4df-0f9c48877df9.png)

### 27.4.3 Array.of

ES6에서 도입된 Array.of 메서드는 전달된 인수를 요소로 갖는 배열을 생성한다.

-   Array.of 는 Array 생성자 함수와 다르게 전달된 인수가 1개여도 인수를 요소로 갖는 배열을 생성한다.

![5](https://user-images.githubusercontent.com/87301268/235819947-12b6e4b4-b1f4-45bf-bd47-4743cb52ba22.png)

### 27.4.4 Array.from

ES6에서 도입된 Array.from 메서드는 **유사 배열 객체** 또는 **이터러블 객체**를 인수로 전달받아 배열로 변환하여 반환한다.

![6](https://user-images.githubusercontent.com/87301268/235820031-923a8c6d-84bb-46ff-b166-b95bc2408c5c.png)

## 27.5 배열 요소의 참조

배열의 요소를 참조할 때에는 **대괄호([]) 표기법**을 사용한다.

-   존재하지 않는 요소에 접근하면 `undefined`가 반환된다.

![7](https://user-images.githubusercontent.com/87301268/235820167-ceca36e9-424c-413d-9bb9-4fa52c5cc568.png)

배열은 사실

-   **인덱스를 나타내는 문자열을 프로퍼티 키로 갖는 객체다.**
-   따라서 존재하지 않는 프로퍼티 키로 객체의 프로퍼티에 접근했을때 undefined를 반환하는 것 처럼
-   **배열도 존재하지 않는 요소를 참조하면 undefined를 반환한다.**

## 27.6 배열 요소의 추가와 갱신

객체 프로퍼티를 동적으로 추가할 수 있는 것처럼 **배열에도 요소를 동적으로 추가할 수 있다.**

-   존재하지 않는 인덱스를 사용해 값을 할당하면 새로운 요소가 추가된다.
-   이때 length 프로퍼티 값은 자동 갱신된다.

![8](https://user-images.githubusercontent.com/87301268/235820566-90377ad9-3e43-4783-8256-0e5a67e47a48.png)

**이미 존재하는 요소에 값을 재할당하면 요소값이 갱신** 됩니다.

![9](https://user-images.githubusercontent.com/87301268/235820709-cfec310a-385a-42a5-8ce7-5ac537abd224.png)

## 27.7 배열 요소의 삭제

배열은 사실 객체이기 때문에 배열의 특정 요소를 삭제하기 위해 delete 연산자를 사용할 수 있다.

-   이때 delete 연산자는 객체의 프로퍼티를 삭제한다.
-   따라서 배열은 **희소 배열이 되며 length 프로퍼티의 값은 변하지 않으므로 delete 연산자는 사용하지 않는 것이 좋다.**

![10](https://user-images.githubusercontent.com/87301268/235820881-0ae49343-3b11-48f1-a752-c35ea607b5df.png)

## 27.8 배열 메서드

**원본 배열을 직접 변경**하는 메서드와 **새로운 배열을 생성하여 반환**하는 메서드가 있다.

### 27.8.1 Array.isArray

Array 생성자 함수의 정적 메서드로 전달된 인수가 배열이면 true, 배열이 아니면 false를 반환한다.

![11](https://user-images.githubusercontent.com/87301268/235821144-ad73acb3-2900-4702-a456-91762a680eef.png)

### 27.8.2 .indexOf

**원본 배열에서 인수로 전달된 요소를 검색하여 인덱스를 반환**한다.

-   원본 배열에 인수로 전달한 요소와 중복되는 요소가 여러 개 있다면 **첫 번째로 검색된 요소의 인덱스를 반환**
-   원본 배열에 인수로 전달한 요소가 **없다면 -1을 반환**

![12](https://user-images.githubusercontent.com/87301268/235821309-1dc31cf6-2e28-4f55-9a40-eb8ab7b72f3f.png)

ES7에서 도입된 `.includes` 메서드를 사용하면 가독성이 더 좋다

![13](https://user-images.githubusercontent.com/87301268/235821515-8a132cbf-f67c-4c62-b6b9-4f23b4aedd9e.png)

### 27.8.3 .push

인수로 전달받은 모든 값을 **원본 배열의 마지막 요소로 추가**하고 변경된 length 프로퍼티 값을 반환한다.

-   `push` 메서드는 **원본 배열을 직접 변경**한다.

![14](https://user-images.githubusercontent.com/87301268/235824187-1f77401b-2775-4ed3-b7a7-818cd12d9b1c.png)

다만, push 메서드는 성능면에서 좋지 않다.
마지막 요소로 추가할 요소가 하나뿐이라면 `length` 프로퍼티를 사용하여 배열의 마지막 요소에 직접 추가하는 것이 빠르다.

![15](https://user-images.githubusercontent.com/87301268/235824334-6dd7c089-107c-4146-9d4c-b231f4594411.png)

### 27.8.4 .pop

원본 배열에서 **마지막 요소를 제거하고 제거한 요소를 반환한다.**

-   원본 배열이 빈 배열이면 undefined를 반환한다.
-   `push` 메서드는 **원본 배열을 직접 변경**한다.

![16](https://user-images.githubusercontent.com/87301268/235830964-498a3f4a-abcd-43ec-8aaa-4704321f63bf.png)

### 27.8.5 .unshift

**인수로 전달받은 모든 값을 원본 배열의 선두에 요소로 추가**하고 변경된 length 프로퍼티 값을 반환한다.

-   `unshift` 메서드는 **원본 배열을 직접 변경**한다.

![17](https://user-images.githubusercontent.com/87301268/235831154-e5b08293-b13a-4f8d-b301-5259b55488f6.png)

### 27.8.6 .shift

**원본 배열에서 첫 번째 요소를 제거**하고 제거한 요소를 반환한다.

-   원본 배열이 빈 배열이면 undefined를 반환한다.
-   `shift` 메서드는 **원본 배열을 직접 변경한다.**

![18](https://user-images.githubusercontent.com/87301268/235831457-1d91f619-2f14-4d87-ae83-0e25d2456d3c.png)

### 27.8.7 .concat

인수로 전달된 값들(배열 또는 원시값)을 **원본 배열의 마지막 요소로 추가한 새로운 배열을 반환한다.**

-   인수로 전달한 값이 배열인 경우 배열을 해체하여 새로운 배열의 요소로 추가한다.
-   **원본 배열은 변경되지 않는다.**

![19](https://user-images.githubusercontent.com/87301268/235831682-1afde53f-ce03-4599-b742-b0f99be4e145.png)

### 27.8.8 .splice

`push`, `pop`, `unshift`, `shift` 메서드는

1. **모두 원본 배열을 직접 변경**하는 메서드이며
2. 원본 배열의 처음이나 마지막 요소를 추가하거나 제거한다.

**원본 배열 중간에 요소를 추가하거나 제거하는 경우** `splice` 메서드를 사용한다

-   **원본 배열을 직접 변경한다.**

splice 메서드는 3개의 매개변수가 있다.

1. `start`: **원본 배열의 요소를 제거하기 시작할 인덱스이다.** ➡️ start만 지정하면 원본 배열의 모든 요소를 제거한다.
   ➡️ start가 **음수일 경우 배열의 끝에서의 인덱스**를 나타낸다.

2. `deleteCount(옵션)`: 원본 배열의 요소를 제거하기 시작할 인덱스인 **start부터 제거할 요소의 개수이다.**
   ➡️ deleteCount가 0인 경우 아무런 요소도 제거되지 않는다.
3. `items(옵션)`: **제거한 위치에 삽입할 요소들의 목록이다.**
   ➡️ 생략할 경우 원본 배열에서 요소를 제거하기만 한다.

![20](https://user-images.githubusercontent.com/87301268/235832787-3adef992-15ce-412c-9171-032be9ebe265.png)

### 27.8.9 .slice

**인수로 전달된 범위의 요소들을 복사하여 배열로 반환한다.**

slice 메서드는 두개의 배개변수를 갖는다.

1. `start` : 복사를 시작할 인덱스다. ➡️ 음수인 경우 배열 끝에서의 인덱스를 나타낸다.
2. `end(옵션)` : 복사를 종료할 인덱스다. ➡️ end는 생략 시 기본값은 length 프로퍼티 값이다.

-   **원본 배열은 변경되지 않는다.**

![21](https://user-images.githubusercontent.com/87301268/235834630-65c20cfe-8b2f-46b1-ab87-b6c8c13510d1.png)

### 27.8.10 .join

원본 배열의 모든 요소를 문자열로 변환한 후 인수로 전달받은 문자열 즉, **구분자로 연결한 문자열을 반환한다.**

-   **구분자는 생략 가능**하며 기본 구분자는 콤마(,)다.

![22](https://user-images.githubusercontent.com/87301268/235835577-4291ce83-b9e7-4f49-96a9-e9c0ad564a4d.png)

### 27.8.11 .reverse

원본 배열의 순서를 반대로 뒤집는다.

-   이때 **원본 배열이 변경된다.**
-   반환값은 변경된 배열이다.

![23](https://user-images.githubusercontent.com/87301268/235835695-8971e3fc-c12c-4d16-aa04-0c0c121b2f35.png)

### 27.8.12 .fill

ES6에서 도입된 `fill` 메서드는 **인수로 전달받은 값을 배열의 처음부터 끝까지 요소로 채운다.**

-   이때 **원본 배열이 변경된다.**

![24](https://user-images.githubusercontent.com/87301268/235835990-2582b450-e1ae-4c7e-a89e-2f961b72b61a.png)

fill 메서드를 사용하면 **배열을 생성하면서 특정 값으로 요소를 채울 수 있다.**

![25](https://user-images.githubusercontent.com/87301268/235836098-f911cf8c-54ff-4af6-bf97-380e1c057bdf.png)

### 27.8.13 .includes

**배열 내에 특정 요소가 포함되어 있는지 확인**하여 `true` 또는 `false`를 반환한다.

-   **첫 번째 인수로 검색할 대상을 지정한다.**
-   **두 번째 인수로 검색을 시작할 인덱스**를 전달할 수 있다.

두 번째 인수를 생략할 경우 기본값 0이 설정된다.

만약 두 번째 인수에 음수를 전달하면 length 프로퍼티 값과 음수 인덱스를 합산하여(length+index) 검색 시작 인덱스를 설정한다.

![26](https://user-images.githubusercontent.com/87301268/235836635-fb8db83a-b595-4bc3-ab4c-19040a63c885.png)

## 27.9 배열 고차 함수

고차 함수는 **함수를 인수로 전달** 받거나, **인수를 반환하는 함수**를 말한다.

### 27.9.1 .sort

배열의 요소를 정렬한다.

-   원본 배열을 직접 변경하며 **정렬된 배열을 반환한다.**
-   **오름차순**으로 정렬한다.

![27](https://user-images.githubusercontent.com/87301268/235839149-8a90746e-2756-4a26-a1fd-46934013f2d5.png)

숫자 요소로 이루어진 배열을 정렬할 때는 주의가 필요하다

-   sort 메서드의 기본 정렬 순서는 **유니코드** 코드 포인트의 순서를 따른다.
-   따라서 숫자 요소를 정렬할 때는 sort 메서드에 정렬 순서를 정의하는 `비교 함수를 인수로 전달`해야 한다.
-   비교 함수는 `양수`나 `음수` 또는 `0을 반환`해야 한다.

![28](https://user-images.githubusercontent.com/87301268/235839372-7cfb160e-38dc-493b-8124-d7ab4727b421.png)

### 27.9.2 .forEach

**for 문을 대체** 할 수 있는 고차 함수다.

자신의 내부에서 반복문을 통해 **자신을 호출한 배열을 순회**하면서
수행해야할 처리를 콜백 함수로 전달받아 반복 호출한다.

![29](https://user-images.githubusercontent.com/87301268/235839802-0fd1c521-77f7-4daa-a2e7-d1b042aaef27.png)

forEach 메서드의 콜백 함수는

1. forEach 메서드를 호출한 `배열의 요소값`과 `인덱스`
2. forEach 메서드를 호출한 `배열 자체`, 즉 this를 순차적으로 전달받을 수 있다.

![30](https://user-images.githubusercontent.com/87301268/235840145-b1cfe22f-3a69-46f0-92b0-a4625a66413b.png)

### 27.9.3 .map

**자신을 호출한 배열의 모든 요소를 순회**하면서 인수로 전달받은 콜백 함수를 반복 호출한다.

-   콜백 함수의 반환값들로 구성된 **새로운 배열을 반환**한다.
-   요소값을 다른 값으로 매핑한 **새로운 배열을 생성**하기 위한 고차함수다.

![31](https://user-images.githubusercontent.com/87301268/235840823-4927f1cb-0c31-4914-b53a-14d5d6e72374.png)

### 27.9.4 .filter

자신을 호출한 배열의 모든 요소를 순회하면서 인수로 전달받은 콜백 함수를 반복 호출한다.

-   그리고 **콜백 함수의 반환값이 true인 요소로만 구성된 새로운 배열을 반환**한다.
-   이때 **원본 배열은 변경되지 않는다.**

![32](https://user-images.githubusercontent.com/87301268/235841474-1d52df4e-c69c-43e7-a2b3-fda5030a26c2.png)

### 27.9.5 .reduce

자신을 호출한 배열을 모든 요소를 순회하며 인수로 전달받은 콜백 함수를 반복 호출한다.

-   그리고 **콜백 함수의 반환값을 다음 순회 시에 콜백 함수의 첫 번째 인수로 전달**하면서
-   콜백 함수를 호출하여 **하나의 결과값을 만들어 반환**한다.
-   이때 **원본 배열은 변경되지 않는다.**

reduce 메서드는

1. 첫 번째 인수로 콜백 함수
2. 두 번째 인수로 초기값을 전달받는다.

reduce 메서드의 콜백 함수에는 4개의 인수가 있다.

1. 초기값 또는 콜백 함수 이전의 반환값
2. reduce 메서드를 호출한 배열의 요소값과 인덱스
3. reduce 메서드를 호출한 배열 자체(this)가 전달된다.

-   reduce 메서드를 호출할 때는 언제나 초기값을 지정하는 것이 안전하다.

![33](https://user-images.githubusercontent.com/87301268/235842792-7e4cac7a-0899-4bd6-8f46-9bca7973d911.png)

### 27.9.6 .some

자신을 호출한 배열의 요소를 순회하면서 인수로 전달된 콜백 함수를 호출한다.

-   이때 some 메서드는 콜백 함수의 반환값이 **단 한번이라도 참이면 true** **모두 거짓이면 false를 반환한다.**

![34](https://user-images.githubusercontent.com/87301268/235843111-1a0d44d2-2320-4f09-850e-2898fcbe51c9.png)

### 27.9.8 .find

콜백 함수의 **반환값이 true 인 요소가 존재하지 않는다면 undefined를 반환한다.**

-   find 메서드는 **배열이 아니라 요소를 반환**한다.

![35](https://user-images.githubusercontent.com/87301268/235843443-797f9eb7-cb4e-4f97-92e0-d9a6aa497509.png)

### 27.9.9 .findIndex

findIndex 메서드는 자신을 호출한 배열의 요소를 순회하면서

-   인수로 전달된 콜백 함수를 호출하여 **반환값이 true인 첫 번째 요소의 인덱스를 반환한다.**
-   콜백 함수의 반환값이 true인 요소가 존재하지 않는다면 **-1을 반환한다.**

![36](https://user-images.githubusercontent.com/87301268/235844103-bb02ef3b-6f28-4a5e-b82c-726a36710f41.png)