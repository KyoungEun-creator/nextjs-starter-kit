# 🧘🏻‍♀️ nextjs starter kit

### nextjs 프로젝트 시 불필요한 코드 충돌을 막고 통일성을 높이기 위한 세팅 순서

1. NEXTjs, prettier-plugin-tailwindcss 플러그인 설치

```
npx create-next-app@latest .
npm install -D prettier prettier-plugin-tailwindcss // tailwind className 순서 정렬
```

2. /.prettierignore 파일 생성

```javascript
 node_modules/
.next
public/
```

3. /.prettierrc 파일 생성

```javascript
{
  "semi": true,
  "singleQuote": false,
  "tabWidth": 2,
  "useTabs": false,
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

4. src 폴더 안에 있던 favicon.ico 삭제
5. src > app > page.tsx 초기화 및 nfce 자동완성
6. src > css 폴더 생성
7. 기존 globals.css 파일 → css 폴더 안으로 이동
8. src > app 폴더 안에 있던 layout.tsx 삭제
9. npm run dev 구동 (자동으로 layout.tsx 생성됨)
10. 자동으로 생성된 src > app 폴더 안 layout.tsx 최상단에 globals.css 파일 입력 통한 연결

    ```jsx
    import "@/css/globals.css";
    ```

11. globals.css 파일 내 tailwind import 외 나머지 전부 지우기

```jsx
@tailwind base;
@tailwind components;
@tailwind utilities;
// 위 세 줄만 남겨놓기
```

12. src > components 폴더 생성 (컴포넌트 파일 모음 용도)
13. src > lib 폴더 생성 (라이브러리 파일 모음 용도)
14. .gitignore 파일에 내용 추가

    ```jsx
    # custom
    .env
    package-lock.json
    ```

15. package.json 파일에 내용 추가

    ```jsx
    "scripts": {
        ...
        "format": "prettier --write ."
      },

      // "npm run format" 명령을 날리면 (.prettierrc에 따라) 하위폴더에 포매팅을 전부 일치시킴
      // github 레포에 올리기 전에 사용하고 올리면 불필요한 충돌을 최대한 막을 수 있음
    ```
