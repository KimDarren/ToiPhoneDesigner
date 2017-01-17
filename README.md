# iPhone 이미지 리소스 전달법
## 파일명

파일명은 리소스 중복과 파일명의 중복을 방지하기 위해 아래의 규칙을 따릅니다.

`{type}_{screen name}_{explain}@{ratio}x.{filename extension}`

* {type}
	* 이미지 리소스의 형태입니다.
	* 아이콘의 경우 `ic`, 버튼의 경우 `btn` 등을 사용합니다.
	* 정답은 없지만, 최대한 통일되도록 작명합니다.
* {screen name}
	* 리소스가 보여질 앱 화면의 이름입니다.
	* 여러 화면에서 공통적으로 사용되는 리소스의 경우 `common`을 사용합니다.
* {explain}
	* 리소스에 대한 설명입니다.
* {ratio}
	* 이미지 리소스의 비율입니다.
	* 하단의 **화면 사이즈 대응**을 참고해주세요.
* {filename extension}
	* 파일 확장자입니다.
	* 특별한 이유가 없을 경우, 이미지 리소스의 확장자는 [`png`](https://ko.wikipedia.org/wiki/PNG)를 사용합니다.
	* **소문자**로 작성합니다.

전체적인 틀은 [`Snake Case`](https://en.wikipedia.org/wiki/Snake_case)_(ex. noon\_date)_를 사용해 작명하되, 밑줄문자(`_`)로 구분되는 type, screen name 등의 내용은 [`Camel Case`](https://en.wikipedia.org/wiki/CamelCase)_(ex. noonDate)_를 사용해 작명합니다.

밑줄 문자(`_`)가 아닌 하이픈(`-`)을 사용할 경우, Xcode에서 이미지명 자동완성이 이루어지지 않습니다.

**For example:**
	
```
ic_common_logo@2x.png
btn_logIn_submit@3x.png
btn_signUp_cancel@3x.png
```

**Not:**

```
logo_2x.png
btn_log_in_submit@3.png
btn-signUp-cancel@3x.png
```

## 화면 사이즈 대응

화면 사이즈 대응은 크게 `@1x`, `@2x`, `@3x`로 나뉘어집니다.

위의 **파일명**에 언급했듯, 파일 확장자의 바로 앞에 붙입니다.

* `1x`
	* `1세대 iPhone`, `iPhone3G`, `iPhone3GS`에서 사용되는 리소스입니다.
	* 1개의 pixel이 1 point로 적용됩니다.
	* iOS7 이상을 지원하는 앱의 경우, 1배율 이미지는 필요 없습니다.
* `2x`
	* `iPhone 4`, `iPhone 4S`, `iPhone 5`, `iPhone 5S`, `iPhone5C`, `iPhone SE`, `iPhone 6`, `iPhone 6S`에서 사용되는 이미지입니다.
	* 4개의 pixel이 1 point로 적용됩니다.
	* 따라서, 실제 앱에는 가로와 세로가 각각 2로 나눠진 크기로 보여집니다.
* `3x`
	* `iPhone 6 Plus`, `iPhone 6S Plus`에서 사용되는 이미지입니다.
	* 9개의 pixel이 1 point로 적용됩니다.
	* 따라서, 실제 앱에는 가로와 세로가 각각 3으로 나눠진 이미지가 보여집니다.

현재 iPhone6 이상의 화면 크기를 지원하지 않더라도, 가까운 미래를 위해 3배율 이미지도 함께 전달 부탁드립니다.

## 디자인 가이드
1. 디자인 가이드는 특별한 이유가 없는 한, 가로 `640px` 기준으로 작성합니다.

1. 기본적으로 디자인 가이드에 포함되어야 하는 내용은 아래와 같습니다.
	* 아이콘/이미지 파일명
	* 텍스트 정보
		* 폰트명
		* 크기
		* 색상
	* 요소들의 X, Y 간격
	* 코드로 구현되어야하는 요소들의 굵기/색상 등
	
	_필요에 의해, `자간`, `행간`, `배경색` 등의 정보를 추가할 수 있습니다._

1. 모든 색상값은 RGB 16진수값으로 전달합니다.

	**For example:**
		
	```
	#666666
	333333
	```
	
	**Not:**
	
	```
	(102, 102, 102)
	(R: 51, G: 51, B: 51)
	```

1. 그림자가 들어가는 모든 요소는 아래의 정보를 함께 전달합니다.
	* color
	* radius
	* offset
		* width값과 height값을 각각 전달합니다.
	* opacity
		* 0과 1 사이의 실수값을 전달합니다.
