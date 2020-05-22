# Nodebird Clone Coding - 6
### next는 동적 주소를 처리하지 못한다
때문에 express와 프론트를 연결해주기로 했다

쿼리스트링을 이용하면 가능은 하다!

### case 깨알 문법
switch case 문법에서 결과가 같을 경우에 아래와 같이

동시에 표현이 가능하다
```js
  case LOAD_MAIN_POSTS_REQUEST:
  case LOAD_HASHTAG_POSTS_REQUEST:
  case LOAD_USER_POSTS_REQUEST:
  return {
    ...state,
    mainPosts: [],
   };
```

### Link태그를 이용하여 프론트단에서 처리하기

```js
<Link href={`/user/${Post.User.id}`}><a><Avatar>{post.User.nickname[0]}</Avatar></a></Link>
=> express단에서 서버요청으로 처리되기 때문에 페이지가 새로 렌더링이 된다, 즉 ajax방식으로 처리되지 않고 깜빡임이 발생하게 된다
<Link href={{ pathname: '/user', query: { id: post.User.id } }}><a><Avatar>{post.User.nickname[0]}</Avatar></a></Link>
=> 서버의 요청으로 가지 않고 프론트 단에서만 해결하게 되어 깜빡임이 발생하지 않게 된다
```

### 게시글이 먼저 있는지 확인!

댓글 목록을 불러오는 api를 짜는데 zeroCho님이 강조하신 것은 게시글이 먼저 있는지 확인하는 것이다

없다면 에러처리를 해줘야 한다

우리가 게시글을 직접 클릭해서 들어가는 것이기에 항상 게시글이 있다고 생각할 수 있지만

그 사이 삭제가 된 경우, 사용자가 URL입력을 통하여 들어간 경우들이 생길 수가 있다

물론 이외에 경우도 많을 것이다 당연한 완성도를 위하여서는 처리해줘야 한다

### 오타 조심, 그리고 에러메세지 분석해보기

댓글 추가 기능을 넣는 중에 계속 에러가 났었다

디버깅을 해본 결과 추가된 댓글이 들어가는데 거기에 fullfill 데이터가 담기는 것이었다

비동기 쪽에서 생긴 문제임이 확실함에도 전체 코드를 계속 보느라 시간이 오래걸렸다

문제는 다름 아닌 코드 한 줄에 await를 써주지 않아서였다

비동기의 문제라는 사실을 알 수 있었음에도 전체적인 코드를 보느라 오래걸렸다

어떤 에러가 발생했는지를 파악하고 정밀한 분석을 하는 연습이 필요함을 느꼈다

### 이미지 업로드는 큰 작업!

업로드할 때 이미지와 텍스트등 여러 작업이 있을 때에 이미지를 따로 올리는 것이 좋다

이미지 업로드 자체가 서버의 자원을 많이 잡아먹는 작업이기에 동시에 처리하면 속도가 느리다

### FormData

multer가 FormData는 아래와 같이 처리한다
파일 => req.files
text => req.body

### Post 요청시에 data에 빈 객체 넣어주기
axios를 이용하여 post 요청을 보낼 때에는 넣어줄 데이터가 없더라도 빈 객체를 넣어서 보내야 한다!

```js
axios.post('/api/록퉁구', {}, { withCredentials: true });
```