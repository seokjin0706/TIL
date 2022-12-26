# styled-componets 설치

`npm i -D @types/styled-components`

# 스타일 작성

``` typescript
import styled from 'styled-components';


let Btn = styled.button<{bg: string}>`
  background: ${props => props.bg};
  color : black;
  padding : 10px;

`
<Btn bg="blue">버튼</Btn>
```

#
