# Code Style Guide: HTML

HTML 코드 작성 가이드를 정의한다.

## 문법
- 들여쓰기 간격은 항상 일정하게 하며, 들여쓸 때에는 1탭을 들여쓴다. (탭의 크기는 공백 4칸으로 설정)
- 속성(attributes)은 항상 큰 따옴표(double quotes)를 사용한다.
- `<area>`, `<br>`, `<img>` 등과 같은 self-closing 요소는 닫는 슬래시를 포함하지 않는다. (HTML5 doctype)
- `<html>`의 자식요소인 `<head>`, `<body>`는 들여쓰기를 하지 않는다.
- `<head>`의 자식요소는 들여쓰기를 하지 않는다.
- `<body>`의 자식요소는 들여쓰기를 하지 않는다.

```html
<!DOCTYPE html>
<html>
<head>
	<title>Page title</title>
</head>
<body>
<div>
	<img src="images/logo.png" alt="LOGO">
	<h1>Hello, world!</h1>
</div>
</body>
</html>
```

## HTML5 문서 타입
모든 HTML 페이지는 HTML5 doctype을 사용하여 가능한 모든 브라우저에서 표준 모드와 일관성있는 렌더링이 적용되도록 한다.
(단, 요구사항에 다른 doctype이 정의 되어 있는 경우 그에 따른다.)

```html
<!DOCTYPE html>
<html>
<head>
	<title>Page title</title>
</head>
</html>
```

## 언어 속성
`<html>`요소에 페이지의 주언어를 속성(`lang`)으로 지정한다. 

[HTML Language Code Reference](http://www.w3schools.com/tags/ref_language_codes.asp) 

```html
<html lang="ko">
<!-- ... -->
</html>
```

## 인터넷 익스플로러 호환 모드

Internet Explorer는 페이지를 랜더링할 IE의 버전을 지정하는 문서 호환성 `<meta>` 태그의 사용을 지원한다. 지정된 DOCTYPE에 상관없이 IE8 이상 버전에서 항상 최신 표준 모드로 렌더링 되도록 `IE=edge`를 사용한다. 

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

## 문자열 인코딩

HTML의 문자셋을 지정하여 콘텐츠의 문자들이 적절하게 렌더링 되도록한다. 일반적으로 UTF-8을 사용한다. 

```html
<head>
  <meta charset="UTF-8">
</head>
```

## CSS/자바스크립트 인클루드

HTML5에서는 일반적으로 CSS와 JavaScript를 포함할때 `type`속성을 지정할 필요가 없다. 각각 기본값으로 `text/css`와 `text/javascript`로 지정이 된다.
(단, HTML5 doctype이 아닐 경우 `type`속성을 지정한다.)

- `<head>`요소 안에 추가한다.
- `<meta>`요소들 다음에 추가한다.
- CSS를 JavaScript 보다 먼저 추가한다.

```html
<!-- External CSS -->
<link rel="stylesheet" href="style.css">

<!-- In-document CSS -->
<style>
	/* ... */
</style>

<!-- External JavaScript -->
<script src="script.js"></script>

<!-- In-document JavaScript -->
<script>
	/* ... */
</script>
```

## 태그 속성 순서

HTML 속성은 가독성을 높이기 위하여 아래의 순서를 준수한다.

- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `role`, `aria-*`

가장 많이 사용하는 `class` 속성을 가장 처음 작성한다.

```html
<a class="link" id="bookmark" data-toggle="modal" href="#">
	Bookmark Link
</a>

<input class="form-control" type="text">

<img src="filename.jpg" alt="Image">
```

## 불리언 속성

부울속성은 값을 선언하지 않는다.
(단, XHTML인 경우 반드시 값을 선언한다. `checked="checked"`) 

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
	<option value="1" selected>1</option>
</select>
```

## 마크업 최소화

HTML을 작성할 때 가능하면 불필요한 부모 요소를 사용하지 않는다. 이는 HTML의 복잡도를 줄이며 성능향상에 도움이 된다. 

```html
<!-- Not so great -->
<span class="avatar">
	<img src="...">
</span>

<!-- Better -->
<img class="avatar" alt="">
```

## 주석 사용

- 주석 기호와 주석 내용 사이에는 반드시 공백을 한 칸 띄운다.
- 주석 내용이 두 줄 이상인 경우 주석 기호와 주석 내용 사이에 줄바꿈을 한다.
- 레이아웃 또는 독립된 콘텐츠 영역의 시작과 끝을 알리는 주석은 시작과 끝 부분에 주석을 작성한다.

```html
<!-- Comments -->

<!--
Block Comments
this is comment text
-->

<!-- contents section -->
<section class="contents">
	...
</section>
<!-- // contents section -->
```
