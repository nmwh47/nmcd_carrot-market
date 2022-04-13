# Carrot Market

## #3 Setup
### #3.0 NextJS Setup
NextJS 프로젝트 초기화 (Node.js 12.22.0 이상)
npx create-next-app@latest --typescript
https://nextjs.org/docs/getting-started

NextJS, React 최신 버전 설치 (2022.1월 기준 React 18버전)
npm i next@latest react@rc react-dom@rc
https://nextjs.org/docs/advanced-features/react-18/overview

🚨 중요! 🚨
TypeError: Cannot set properties of undefined (setting 'reactRoot')
2022년 2월 이후로 next@latest으로 설치시 next: 12.1.0버전 이상으로 설치되고, 설치 후, npm run dev로 실행했을 때 위와 같은 오류가 발생하시는 분들은 next.config.js파일에 experimental: {reactRoot:true}를 추가해주시면 버전 다운그레이드 없이 정상적으로 진행하실 수 있습니다.
(추후에 수정될 버그로 보입니다.)
```
/** @type {import('next').NextConfig} */
const nextConfig = {
reactStrictMode: true,
experimental: {
reactRoot: true,
},
};

module.exports = nextConfig;
```

소프트웨어 배포 생명 주기 (Software Release Life Cycle)
1. Alpha: 소프트웨어 테스트를 시작하는 첫 단계
2. Beta: 알파의 뒤를 잇는 소프트웨어 개발 단계
3. RC(Release Candidate): 최종 릴리즈 후보
4. RTM: 완성된 버전

### #3.1 TailwindCSS Setup
Tailwind CSS설치 및 초기화
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p (-p를 붙이면 postcss.config.js파일까지 생성)
https://tailwindcss.com/docs/installation/using-postcss

Prettier를 통한 TailwindCSS 클래스 자동 정렬 플러그인
(TailwindCSS 공식 Prettier플러그인)
blueschist님이 소개해주신 TailwindCSS 클래스 자동 정렬 플러그인입니다. 사용 방법은 아래와 같이 설치 후, 파일 저장시 클래스가 순서에 맞게 자동으로 정렬되도록 도와줍니다.
npm install -D prettier prettier-plugin-tailwindcss
```
// 클래스 정렬 전
button class="text-white px-4 sm:px-8 py-2 sm:py-3 bg-sky-700 hover:bg-sky-800"

// 클래스 정렬 후
button class="bg-sky-700 px-4 py-2 text-white hover:bg-sky-800 sm:px-8 sm:py-3"
```
https://tailwindcss.com/blog/automatic-class-sorting-with-prettier
https://github.com/tailwindlabs/prettier-plugin-tailwindcss

클래스 정렬 기준
https://tailwindcss.com/blog/automatic-class-sorting-with-prettier#how-classes-are-sorted

## #4 TOUR OF TAILWIND
### #4.0 Introduction
TailwindCSS
마크업에서 직접 모든 디자인을 구축하도록 구성할 수 있는 flex, pt-4, text-center 및 rotate-90과 같은 클래스로 가득 찬 유틸리티 최초의 CSS 프레임워크입니다.
https://tailwindcss.com

Tailwind CSS IntelliSense (확장 프로그램)
Tailwind CSS IntelliSense는 Visual Studio Code 사용자에게 자동 완성, 구문 강조 표시 및 린팅과 같은 고급 기능을 제공하여 Tailwind 개발 환경을 향상시킵니다.
https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss

TailwindCSS 클래스 검색 사이트
https://tailwind.build/classes

+ 중간중간에 자동완성이 안 보이시는 분들은 스페이스로 한 칸 띄면 다시 자동완성을 볼 수 있습니다

### #4.1  Test Drive part One
1. 일반적으로 px-1처럼 뒤에 숫자가 붙으면 숫자(1) x 4인 4px이 적용되고, rem은 숫자(1) / 4인 0.25rem이 이 적용됩니다.
ex) px-1 => padding: 0.25rem/* 4px */;
+ border-2처럼 예외도 존재
ex) border-2 => border-width: 2px;

2. x는 left랑 right, y는 top과 bottom을 의미합니다.
ex) px-1 => padding-left, padding-right
ex) py-1 => padding-top, padding-bottom

### #4.2 Test Drive part Two

### #4.3 Test Drive part Three
이모지
⬅️ 🔙
⭐️
💖

### #4.4 Modifiers
TailwindCSS Modifier 리스트

기본적으로 Tailwind에 포함된 모든 단일 modifier의 빠른 참조 테이블입니다.
```
TailwindCSS Modifier (일반 CSS)
hover (&:hover)
focus (&:focus)
active (&:active)
first (&:first-child)
disabled (&:disabled)
sm (@media (min-width: 640px))
md ( @media (min-width: 768px))
lg (@media (min-width: 1024px))
dark (@media (prefers-color-scheme: dark))
등등
```
https://tailwindcss.com/docs/hover-focus-and-other-states#quick-reference