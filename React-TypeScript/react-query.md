# react-query
* 실시간으로 데이터를 게속 갱신할 때 사용(API GET 요청...)
* ajax 요청 시 몇 초마다 데이터를 자동으로 다시 가져온다.
* ajax 실패 시 몇 초마다 데이터를 자동으로 다시 가져온다.
* ajax로 가져온 결과를 state로 공유할 필요가 없다. 
* 여러 컴포넌트에서 같은 url로 ajax 요청 시 캐싱 기능이 있어서 중복 요청하지 않는다.

## 설치
`npm install @tanstack/react-query`

## import
``` typescript
import { QueryClient, QueryClientProvider, useQuery } from '@tanstack/react-query' 

```

## 세팅
QueryClientProvider로 App 감싸기

[index.tsx]
``` typescript
root.render(
  <QueryClientProvider client={queryClient}>
    <React.StrictMode>
        <Provider store={store}>
          <BrowserRouter>
          <App />
          </BrowserRouter>
        </Provider>
        
      </React.StrictMode>
  </QueryClientProvider>
 
);
```

react-query로 ajax 요청하기

[App.tsx]
``` typescript
let result = useQuery({
queryKey: ['test'],
queryFn: ()=> axios.get('url')
                    .then((a)=>{ 
                    console.log('요청됨')
                    return a.data
                    })
                
})

{result.isLoading && '로딩중'}
{result.error && '에러'}
{result.data && result.data.name}
```

