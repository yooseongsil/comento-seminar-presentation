---
theme: apple-basic
background: https://source.unsplash.com/collection/94734566/1920x1080
highlighter: shiki
lineNumbers: false
colorSchema: 'dark'
drawings:
  persist: false
layout: intro
title: comento-ui 자동훈!완성
---

# comento-ui 자동훈!완성

JetBrains IDE에서 Vue UI Library 자동 완성 지원하기

<div class="absolute bottom-10">
  <span class="font-700">
    코멘토 유성실
  </span>
</div>

<style>
.slidev-layout p {
  @apply opacity-60
}
.slidev-layout span {
  @apply opacity-30
}
</style>

---
layout: image-right
image: seongsil.jpeg
---

# 발표자 소개

<br>

## 유성실

`유팀장` `시루짱` `짱시루?!?` `임원` `이모` `비선실세`

`정신연령5살` `성실바나스` `인천성실` `우사인성실` 

`셀럽성실` `아이유성실` `아이쿠` `에유` `트레비콜렉터` 

`코멘토 구혜선` `팔씨름챔피언` `컨퍼런스발표자` 

`실시간노션업데이터` `노션24시간상주` 

`열정은 기술을 뛰어넘는다의 인간화` 

`염소사운드장인`

<style>
code {
  font-size: 18px;
  margin-right: 2px;
}
code:before, code:after {
  display: none;
}
</style>

---

# 목차
- 배경
- 본격 삽질기
- 자동 완성 지원하기
- 남은 과제
- 느낀 점

---
layout: section
---

# 배경

---

# 충격 공포 실화

- **아빠**: 울딸 **코멘트** 유튜브 나온거 잘 봤어~😍
<img src="comento_youtube_thumbnail.webp" style="height: 140px" class="mb-4 ml-10">
- **나**: (**코멘토**인데..☹️) 어.. 고마워~~😀
<img src="calmdownman_jjal.png" style="height: 140px" class="ml-7">
---

# 자동 완성의 필요성

<img src="autocomplete.png" class="mb-4">
<span class="opacity-60">네이버에서 코멘트를 이긴 코멘토.jpg</span>

---

# comento-ui

- 1개월 동안 구축한 코멘토 디자인 시스템
- Vue UI 라이브러리 (https://www.npmjs.com/package/comento-ui)
- 코멘토에서는 npm, yarn으로 다운받아서 사용중

---

# comento-ui 실전 코딩

```vue
<c-button>
  버튼
</c-button>
```

---

# comento-ui 실전 코딩

```vue {1}
<c-button type="..." color="...">
  버튼
</c-button>
```
<br>

<div class="flex">
  <img src="oilnam.jpeg" v-click class="mr-10">
  <img src="3ide.png" v-click>
</div>

---

# 자동 완성이 필요한 프론트팀

<img src="autocomplete_agit_jjal_1.png">
<img src="autocomplete_agit_jjal_2.png" v-click>
<img src="autocomplete_agit_jjal_3.png" v-click style="position: absolute; top: 96px; right: 100px">
<img src="autocomplete_agit_jjal_4.png" v-click style="position: absolute; top: 189px; right: 100px">
<img src="autocomplete_agit_jjal_5.png" v-click style="position: absolute; top: 280px; right: 100px">
<img src="autocomplete_agit_jjal_6.png" v-click style="position: absolute; top: 120px; left: 80px; transform: rotate(-5deg)">
<img src="autocomplete_agit_jjal_7.png" v-click style="position: absolute; top: 60px; right: 100px; transform: rotate(3deg)">
<img src="autocomplete_agit_jjal_8.png" v-click style="position: absolute; top: 50%; right: 100px">
<div v-click style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.8)">
  <div class="bg-black py-2 px-4 text-center text-xl" style="position: absolute; top: 50%; margin-top: -30px; left: 50%; transform: translateX(-50%)">
    그러나...<br>
    해당 분기 인프라 담당자였던<br>
    유성실 혼자 하게 되었다
  </div>
</div>

<style>
  img {
    width: 400px;
  }
</style>

---
layout: section
---

# 본격 삽질기
## 의식의 흐름 시점 주의

<style>
    h2 {
        @apply opacity-60;
    }
</style>
---

# End Image
- tag
<img src="vuetify_tag.png">

- props
<img src="vuetify_props.png">

- props value
<img src="vuetify_props_value.png">

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: Vuetify</span>

<style>
img {
  height: 80px;
  @apply mt-2
}
</style>

---

# 가설 세우기

- 파일 형식이 **TS일 때만 자동 완성이 될 것**이다🤔
  - comento-ui는 **JS** 형식이고 자동 완성이 **되지 않음**
  - Vuetify는 **TS** 형식이고 자동 완성이 **됨**

---

# 가설 검증하기

|      이름     | 파일 형식 | component 자동 완성  | props 자동 완성  |
|--------------|:------:|:----------------:|:------------:|
|    Vuetify   |   TS   |        O         |      O       |
| BootstrapVue |   JS   |        O         |      O       |
|    Vuesax    |   JS   |        O         |      X       |

---

# 가설 검증하기

|      이름     | 파일 형식 | component 자동 완성  | props 자동 완성  |
|--------------|:------:|:----------------:|:------------:|
|    Vuetify   |   TS   |        O         |      O       |
| BootstrapVue |   JS   |        O         |      O       |
|    Vuesax    |   JS   |        O         |      X       |

## 👉 파일 형식이 JS여도 자동 완성이 된다

<style>
  table tbody tr:not(:first-of-type) {
    background: rgba(158, 138, 6, 0.2);
  }
</style>

---

# 다시 가설 세우기

<br><br><br>

# 🤯
## 세울 가설이 없다.. 
도대체 **JS에서의 자동 완성**은 어떻게 가능한 걸까?

---

# 개발자의 친구 구글링 🔍✨

<br>

## web-types.json
- JetBrains에서 만든 다양한 웹 프레임워크를 문서화하기 위한 오픈 소스 표준
- 프레임워크에 구애받지 않고 JSON 문법 형식만 지키면 IDE에서 자동 완성 가능

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: https://blog.jetbrains.com/webstorm/2021/01/web-types/</span>

---

# 개발자의 친구 구글링 🔍✨

<br>

## web-types.json
- JetBrains에서 만든 다양한 웹 프레임워크를 문서화하기 위한 오픈 소스 표준
- 프레임워크에 구애받지 않고 JSON 문법 형식만 지키면 IDE에서 자동 완성 가능

## 👉 `web-types.json` 파일이 있으면 JS여도 자동 완성이 된다!

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: https://blog.jetbrains.com/webstorm/2021/01/web-types/</span>


<style>
    code:before, code:after {
        display: none;
    }
</style>
---

# web-types.json 만드는 방법

<br>

## 1. 자체적으로 생성하기

<br>

## 2. 라이브러리 이용하기

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: https://github.com/JetBrains/web-types#distribution</span>
<style> 
    ol {
        list-style: auto;
        @apply mt-10;
    }
    .slidev-layout li {
        @apply text-2xl;
        @apply mb-2;
    }
</style>
---

# web-types.json 만드는 방법

<br>

## 1. 자체적으로 생성하기
- Vue Library들이 대부분 사용 중인 방법 <span class="opacity-60">- JetBrains에서 직접 컨트리뷰트 진행함</span>
  - **[Vuetify](https://github.com/vuetifyjs/vuetify/pull/9440)**
  - **[BootstrapVue](https://github.com/bootstrap-vue/bootstrap-vue/pull/4110)**
  - **[Nuxt.js](https://github.com/nuxt/nuxt.js/pull/7611)**
  - ...

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: https://github.com/JetBrains/web-types#distribution</span>
<style> 
    ol {
        list-style: auto;
    }
    .slidev-layout ul {
        margin-top: 0;
        margin-bottom: 20px;
    }
    code:before, code:after {
        display: none;
    }
</style>
---

# web-types.json 만드는 방법

<br>

## 2. 라이브러리 이용하기
- **[vue-styleguidist](https://vue-styleguidist.github.io/)**: `JSDoc` 라이브러리
- **[vue-docgen-web-types](https://github.com/JetBrains/web-types/tree/master/gen/vue-docgen-web-types)**: `vue-styleguidist`의 내부 패키지인 
  `vue-docgen-api`를 이용하여<br>
  <span class="ml-48">`JSDoc` 구문 분석을 해주는 라이브러리</span>

<span class="opacity-40" style="position: absolute; bottom: 36px">참고: https://github.com/JetBrains/web-types#generating-web-types</span>
<style> 
    ol {
        list-style: auto;
    }
    .slidev-layout ul {
        margin-top: 0;
        margin-bottom: 20px;
    }
    code:before, code:after {
        display: none;
    }
</style>

---

# web-types.json 만드는 방법

<br>

## <span>1. 자체적으로 생성하기</span>
- Vue UI Library들은 `.js` or `.ts` 형식이라 `web-types.json`을 쉽게 추출 가능
- comento-ui는 `.vue` 형식이기 때문에 `web-types.json`으로 추출하기가 까다로움

## 2. 라이브러리 이용하기
- comento-ui의 **기존 구조를 유지**하면서도 `web-types.json`을 추출 가능


<style> 
    ol {
        list-style: auto;
        @apply mt-10;
    }
    .slidev-layout ul {
        @apply mb-16;
    }
    .slidev-layout li {
        @apply text-2xl;
        @apply mb-2;
    }
    code:before, code:after {
        display: none;
    }
</style>
---

# web-types.json 만드는 방법

<br>

## <span>1. 자체적으로 생성하기</span>
- Vue UI Library들은 `.js` or `.ts` 형식이라 `web-types.json`을 쉽게 추출 가능
- comento-ui는 `.vue` 형식이기 때문에 `web-types.json`으로 추출하기가 까다로움

## 2. 라이브러리 이용하기 - 결정 ✅
- comento-ui의 **기존 구조를 유지**하면서도 `web-types.json`을 추출 가능

<style> 
    ol {
        list-style: auto;
        @apply mt-10;
    }
    .slidev-layout ul {
        @apply mb-16;
    }
    h2:first-of-type, ul:first-of-type {
        @apply opacity-30;
    }
    .slidev-layout li {
        @apply text-2xl;
        @apply mb-2;
    }
    code:before, code:after {
        display: none;
    }
</style>

---
layout: section
---

# 자동 완성 지원하기

---

# 자동 완성 지원하기
## 설정 파일 세팅

<br>

<img src="add_package_file_sample.png" style="width: 600px">
<img v-click src="add_setting_file_sample.png" style="width: 300px; position: absolute; right: 150px; bottom: 100px">

---

# 자동 완성 지원하기
## 컴포넌트에 주석 추가

<br>
<img src="component_comment_sample.png" style="width: 500px">

---

# 자동 완성 지원하기
## web-types.json 추출하기

<br>

```vue
  yarn build
```

<br>

<img v-click src="web_types_tree_sample.png" style="height: 300px">

---

# 자동 완성 지원하기
## web-types.json 추출하기

```json {all|7|9,11-13,15-17,20-21}
{
  "name": "comento-ui",
  "contributions": {
    "html": {
      "tags": [
        {
          "name": "c-button",
          "description": "",
          "attributes": [
            {
              "name": "size",
              "description": "크기(small, medium, large, xlarge)",
              "value": {
                "kind": "expression",
                "type": "string"
              },
              "default": "'medium'"
            },
            {
              "name": "color",
              "description": "색상(primary, light-primary, success, error, secondary, info)",
              "value": {
                "kind": "expression",
                "type": "string"
              },
              "default": "'primary'"
            }
          ]
        },
```

---

# 자동 완성 지원하기
## 컴포넌트 적용

- tag
  <img src="sample_tag.png">

---

# 자동 완성 지원하기
## 컴포넌트 적용

- props
    <img src="sample_props.png">
    <img v-click src="sample_props_all.png" style="position: absolute; left: 500px; top: 160px; width: 400px;">

---

# 자동 완성 지원하기
## 컴포넌트 적용

- props value
  <img src="sample_props_value.png" style="width: 500px">

---
layout: section
---

# 남은 과제

---

# 남은 과제

1. **컴포넌트명 자동 등록** <span class="opacity-70">- 진행중</span>
   - 현재는 주석으로 `@displayName`을 입력해야만 자동 완성이 됨
   - 해결 방법:
     - 컴포넌트명에 `C` 추가하기
     - Vue 스타일 가이드에서 컴포넌트명은 단어 하나만 사용하지 말라고 권고하고 있음
     - 우리가 참고하고있는 Vuetify에서도 `v`를 prefix로 사용중

<style>
  ol {
    list-style: auto;
  }
  .slidev-layout ul {
    margin-top: 0;
    margin-bottom: 20px;
  }
  code:before, code:after {
    display: none;
  }
</style>

---

# 남은 과제

1. **컴포넌트명 자동 등록** <span class="opacity-70">- 진행중</span>
    - 현재는 주석으로 `@displayName`을 입력해야만 자동 완성이 됨
    - 해결 방법:
        - 컴포넌트명에 `C` 추가하기
        - Vue 스타일 가이드에서 컴포넌트명은 단어 하나만 사용하지 말라고 권고하고 있음
        - 우리가 참고하고있는 Vuetify에서도 `v`를 prefix로 사용중
2. **VSCode 지원하기** <span class="opacity-40">(우선순위 낮음)</span>
    - 팀원들이 모두 JetBrains IDE를 사용중이지만, 추후 VSCode를 사용하는 팀원들도 생길 수 있기 때문
    - 해결 방법:
        - VSCode 자동 완성에 필요한 파일
            - VSCode에 플러그인 설치: [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
            - comento-ui에 자동 완성 지원 파일 추가: `tags.json`, `attributes.json`

<style>
  ol {
    list-style: auto;
  }
  .slidev-layout ul {
    margin-top: 0;
    margin-bottom: 20px;
  }
  code:before, code:after {
    display: none;
  }
</style>


---
layout: section
---

# 느낀 점

---

# 느낀 점

- 인프라 개선으로 팀원 생산성과 제품 개발 속도를 높일 수 있게 되어 뿌듯했음
<img v-click src="reaction_1.png" style="width: 300px">
<img v-click src="reaction_2.png" style="width: 300px; position: absolute; left: 400px; top: 127px;">
<img v-click src="reaction_4.png" style="width: 300px; position: absolute; left: 400px; top: 240px;">
<img v-click src="reaction_5.png" style="width: 400px; position: absolute; left: 100px; top: 200px;">

---

# 느낀 점

- 인프라 개선으로 팀원 생산성과 제품 개발 속도를 높일 수 있게 되어 뿌듯했음
- 당연하게 사용했던 자동 완성이 어떻게 구현되는지 알 수 있어서 재밌었음

---

# 느낀 점

- 인프라 개선으로 팀원 생산성과 제품 개발 속도를 높일 수 있게 되어 뿌듯했음
- 당연하게 사용했던 자동 완성이 어떻게 구현되는지 알 수 있어서 재밌었음
- shipjs 최고. 배포를 정말 쉽고 편하게 할 수 있음

---

# 참고 자료

- Vuetify (https://github.com/vuetifyjs/vuetify)
- Vuesax (https://github.com/lusaxweb/vuesax)
- BootstrapVue (https://github.com/bootstrap-vue/bootstrap-vue)
- https://blog.jetbrains.com/webstorm/2021/01/web-types/
- https://github.com/JetBrains/web-types#distribution