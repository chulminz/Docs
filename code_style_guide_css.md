# Code Style Guide: CSS

CSS 코드 작성 가이드를 정의한다.

## 문법

- 들여쓰기 간격은 항상 일정하게 하며, 들여 쓸 때에는 1탭을 들여 쓴다. (탭의 크기는 공백 4칸으로 설정)
- 선택자를 그룹화 할때는 한 줄에 하나의 선택자만 작성한다.
- 쉼표로 구분되는 선택자 간 공백을 제거한다.
- 선언블록의 여는 중괄호 앞에는 공백을 하나 사용한다.
- 선언블록의 속성 선언은 모두 한줄에 작성한다.
- 선언블록의 속성 선언 간 공백 및 속성값 사이 공백은 제거한다.
- 쎄미콜론(;)은 기술적으로는 속성선언의 분리기호(separator)로 사용되지만, 종결기호(terminator)처럼 사용한다.
- 쉼표(,)로 구분된 속성 값은 각각 쉼표 뒤에 공백을 포함한다. (e.g., `box-shadow`)
- `rgb()`,`rgba()`등의 속성값의 쉼표 다음에 공백을 포함하지 않는다.
- 속성 값의 0으로 시작되는 소수점 숫자는 0을 생략한다. (e.g., `0.5` > `.5`, `-0.5px` > `-.5px`)
- 모든 속성명은 소문자를 사용한다.
- 축약이 가능한 속성값은 축약하여 사용한다. (e.g., `#ffffff` > `#fff`, `0px` > `0`)
- 속성 선택자의 속성 값은 따움표("")를 사용한다. (e.g., `input[type="text"]`)

```css
/* Bad */
.selector, .selector-secondary,
.selector[type="text"]{
	padding:15px 15px 15px 15px;
	margin-bottom:15px;
	background-color:rgba(0, 0, 0, 0.5);
	box-shadow:0 1px 2px #ccc,inset 0 1px 0 #fff;
}

/* Good */
.selector,
.selector-secondary,
.selector[type="text"] {padding:15px;margin-bottom:15px;background-color:rgba(0,0,0,.5);box-shadow:0 1px 2px #ccc, inset 0 1px 0 #fff;}

@media (min-width:768px) {
	.selector,
	.selector-secondary {padding:20px;}
}
```

## 속성 선언 순서

관련이 있는 속성을 함께 그룹지어서 다음 순서에 따라 선언한다. 

1. Positioning
2. Box model
3. Typographic
4. Visual

`position` 관련된 속성은 문서의 정상적인 흐름에서 요소를 제거할 수 있고, 박스모델 관련 스타일을 재정의 할 수 있기 때문에 가장 처음에 선언한다. 다음으로 요소의 크기와 위치를 잡아주는 박스모델 속성들을 선언한다. 

```css
.declaration-order {
	/* Positioning */
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	left: 0;
	z-index: 100;

	/* Box-model */
	display: block;
	float: right;
	width: 100px;
	height: 100px;
	margin: 10px;
	padding: 10px;

	/* Typography */
	font: normal 13px "Helvetica Neue", sans-serif;
	line-height: 1.5;
	color: #333;
	text-align: center;

	/* Visual */
	background-color: #f5f5f5;
	border: 1px solid #e5e5e5;
	border-radius: 3px;

	/* Misc */
	opacity: 1;
}
```

## `@import` 사용금지

`<head>` 안에 `<link>`를 사용하여 외부 스타일시트를 참조하며, `@import`의 사용은 가급적 자제를 한다. 

[stevesouders.com - don’t use @import](http://www.stevesouders.com/blog/2009/04/09/dont-use-import/)

```html
<!-- Use link elements -->
<link rel="stylesheet" href="core.css">

<!-- Avoid @imports -->
<style>
  @import url("more.css");
</style>
```

## 미디어쿼리 위치

미디어 쿼리는 가능한 관련 규칙에 가깝게 설정한다. 별도의 CSS파일이나 문서 끝 부분에 모두 모아놓을 경우 나중에 그것을 놓치기 쉬워진다.

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width:480px) {
	.element { ... }
	.element-avatar { ... }
	.element-selected { ... }
}
```

## 주석 사용

- 주석 기호와 주석 내용 사이에는 반드시 공백을 한 칸 띄운다.
- 주석 내용이 두 줄 이상인 경우 주석 기호와 주석 내용 사이에 줄바꿈을 한다.

```css
/* Comments */

/*
Block Comments
this is comment text
*/
```

## 클래스명

- 영문 소문자와 하이픈- 기호를 사용하며, 언더스코어_ 또는 카멜표기법을 사용하지 않는다.
- 과도한 약어 사용을 하지 않는다. `.btn`은 button을 의미하기에 유용하지만, `.s`는 아무것도 의미하지 않는다.
- 가능한 짧고 간결함을 유지한다.
- 의미있는 이름을 사용한다. (구조 또는 표현을 의미하도록)
- 가장 가까운 부모 또는 기본 클래스를 기반으로 접두사 클래스를 사용한다.

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

## 선택자

- 일반적으로 사용되는 태그에는 클래스를 사용한다.
- 각 선택자의 요소의 수는 가능한 3개를 넘지 않도록 한다.


















