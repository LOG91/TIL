# React기본9 ZeroChoTV
### ReactRouter
프론트에서 페이지를 라우팅해주는 라이브러리다

#### ReactRouter는 눈속임이다
핵심은 리액트 라우터는 눈속임 이라는 것이다
서버에서 여러 페이지를 제공해주는 것이 아니라 한 페이지이지만
여러 페이지로 보이게 하는 것이다!
아래와 같이 한다면 클릭함에 따라 페이지가 제공이 될 것이다
하지만 제공된 페이지에서 새로고침을 할 경우엔 서버의 Cannot GET 에러를 얻게 된다
서버에 라우팅이 되지 않았기 때문이다!
```jsx
import  { BrowserRouter, Link, Route } from 'react-router-dom';
import { ABC, DEF, GHI } from '../alphabet';

<div>
<BrowserRouter>
  <Link to="/abc">ABC페이지</Link>
  <Link to="/def">DEF페이지</Link>
  <Link to="/ghi">GHI페이지</Link>
  <div>
    <Route path="abc" component={ABC} />
    <Route path="def" component={DEF} />
    <Route path="ghi" component={GHI} />
  </div>
</BrowserRouter>
</div>
```
