# 181112 TIL (HTML doctype)

### Doctype

여러 버전의 HTML이 있는데 이것을 코드의 맨 위에 작성함으로 내가 어떤 버전의 HTML로 마크업할 것인지를 명시한다

HTML5전 버전에는 SGML에 기반해서 상세한 DTD작성이 필요했지만 HTML5에서는 SGML에 기반을 두지 않아서 DTD 참조가 필요 없으며, 최소한의 코드 작성이 기본 방향이라 매우 간단히 선언할 수 있다

HTML5는 `<!DOCTYPE html>` 만 선언해주면 된다!

### QuirksMode & StandardsMode

웹의 역사가 오래됨에 따라 오래된 웹페이지들이 존재한다

그런 페이지들은 지금의 웹표준을 따르지 않아 랜더링 결과가 다를 수 있다

- 스탠다드모드, 지금의 웹 표준을 따르는 해석 방식

- 쿽스모드, 오래된 브라우저의 행동을 모방하도록 만들어진 방식이다
  쉽게 말해 하위 호환성을 위해서 지원되는 방식인 것이다
  비표준을 따라서 랜더링한다, 랜더링 방식은 브라우저마다 다르다

DTD를 명시해주지 않거나 제대로 입력하지 않은 경우 쿽스모드로 해석이 된다