---
title: 재정의 참조
description: Starlight 재정의에서 지원하는 컴포넌트 및 속성에 대한 개요입니다.
tableOfContents:
  maxHeadingLevel: 4
---

Starlight의 [`components`](/ko/reference/configuration/#components) 구성 옵션에 대체 컴포넌트에 대한 경로를 제공하여 Starlight의 내장 컴포넌트를 재정의할 수 있습니다.
이 페이지에는 재정의할 수 있는 모든 컴포넌트와 기본 구현에 대한 Github 링크가 나열되어 있습니다.

[컴포넌트 재정의 가이드](/ko/guides/overriding-components/)에서 자세히 알아보세요.

## 컴포넌트

### 헤드

이 컴포넌트들은 각 페이지의 `<head>` 요소 내에 렌더링됩니다.
또한, 반드시 [`<head>` 내에서 사용하는 것이 허용되는 요소](https://developer.mozilla.org/ko/docs/Web/HTML/Element/head#%EA%B0%99%EC%9D%B4_%EB%B3%B4%EA%B8%B0)만 포함해야 합니다.

#### `Head`

**기본 컴포넌트:** [`Head.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Head.astro)

각 페이지의 `<head>` 내에서 렌더링되는 컴포넌트입니다.

최후의 수단으로 이 컴포넌트를 재정의합니다.
기본 컴포넌트에서 렌더링되는 라우트 데이터를 사용자 정의하려면 [`head` 구성 옵션](/ko/reference/configuration/#head), [`head` 프런트매터 필드](/ko/reference/frontmatter/#head), 또는 [라우트 데이터 미들웨어](/ko/guides/route-data/#경로-데이터-사용자-정의)를 사용하는 것이 좋습니다.

#### `ThemeProvider`

**기본 컴포넌트:** [`ThemeProvider.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/ThemeProvider.astro)

다크/라이트 테마를 설정하기 위해 `<head>` 내에서 렌더링되는 컴포넌트입니다.
기본 구현에는 [`<ThemeSelect />`](#themeselect)에서 사용되는 인라인 스크립트와 `<template>`이 포함되어 있습니다.

---

### 접근성

#### `SkipLink`

**기본 컴포넌트:** [`SkipLink.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/SkipLink.astro)

`<body>` 내부에서 첫 번째 요소로 렌더링되며 메인 페이지의 콘텐츠로 이동하는 접근성을 위한 컴포넌트입니다.
기본적으로 키보드의 탭을 통해 선택하기 전까지는 숨겨져 있습니다.

---

### 레이아웃

이 컴포넌트들은 Starlight 컴포넌트들을 배치하고 다양한 중단점에서 보이는 모습을 관리합니다.
이 컴포넌트들을 재정의하면 상당한 복잡성이 발생하므로, 가능하면 하위 수준의 컴포넌트를 재정의하는 것이 좋습니다.

#### `PageFrame`

**기본 컴포넌트:** [`PageFrame.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/PageFrame.astro)  
**명명된 슬롯:** `header`, `sidebar`

대부분의 페이지 콘텐츠를 감싸는 레이아웃 컴포넌트입니다.
기본적으로 header-sidebar-main 레이아웃을 설정하고 슬롯으로 명명된 `header`와 `sidebar` 및 메인 콘텐츠에 대한 기본 슬롯을 포함합니다.
또한, 작은 (모바일) 뷰포트에서 사이드바 탐색 토글을 지원하기 위해 [`<MobileMenuToggle />`](#mobilemenutoggle)를 렌더링합니다.

#### `MobileMenuToggle`

**기본 컴포넌트:** [`MobileMenuToggle.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/MobileMenuToggle.astro)

작은 (모바일) 뷰포트에서 사이드바 탐색 토글을 수행하는 [`<PageFrame>`](#pageframe) 내부에서 렌더링되는 컴포넌트입니다.

#### `TwoColumnContent`

**기본 컴포넌트:** [`TwoColumnContent.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/TwoColumnContent.astro)  
**명명된 슬롯:** `right-sidebar`

메인 콘텐츠 열과 오른쪽 사이드바 (목차)를 감싸는 레이아웃 컴포넌트입니다.
기본적으로 작은 뷰포트에서 하나의 열로 이루어진 레이아웃과 큰 뷰포트에서 두 개의 열로 이루어진 레이아웃 간 전환을 처리합니다.

---

### 헤더

Starlight의 상단 탐색 바를 렌더링하는 컴포넌트입니다.

#### `Header`

**기본 컴포넌트:** [`Header.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Header.astro)

Header 컴포넌트는 모든 페이지 상단에 표시됩니다.
기본적으로 [`<SiteTitle />`](#sitetitle), [`<Search />`](#search), [`<SocialIcons />`](#socialicons), [`<ThemeSelect />`](#themeselect), 와 [`<LanguageSelect />`](#languageselect)를 표시합니다.

#### `SiteTitle`

**기본 컴포넌트:** [`SiteTitle.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/SiteTitle.astro)

사이트 제목을 렌더링하기 위해 사이트 헤더 시작 부분에 렌더링되는 컴포넌트입니다.
기본적으로 Starlight 구성에 정의된 로고를 렌더링하는 논리가 포함합니다.

#### `Search`

**기본 컴포넌트:** [`Search.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Search.astro)

Starlight의 검색 UI를 렌더링하기 위해 사용되는 컴포넌트입니다. 기본적으로 헤더의 버튼과 클릭하면 [Pagefind의 UI](https://pagefind.app/)를 불러오는 검색 모달을 나타내는 코드가 포함되어 있습니다.

[`pagefind`](/ko/reference/configuration/#pagefind)가 비활성화되면 기본 검색 컴포넌트가 렌더링되지 않습니다.
그러나, `Search`를 재정의하면 `pagefind` 구성 옵션이 `false`인 경우에도 사용자 정의 컴포넌트가 항상 렌더링됩니다.
이를 통해, Pagefind가 활성화되지 않았을 때 대체 검색 공급자에 대한 UI를 추가할 수 있습니다.

#### `SocialIcons`

**기본 컴포넌트:** [`SocialIcons.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/SocialIcons.astro)

사이트 헤더에 렌더링되며 소셜 아이콘 링크를 포함하는 컴포넌트입니다.
기본적으로 아이콘과 링크를 렌더링하기 위해 Starlight 구성에서 [`social`](/ko/reference/configuration/#social) 옵션을 사용합니다.

#### `ThemeSelect`

**기본 컴포넌트:** [`ThemeSelect.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/ThemeSelect.astro)

사용자가 선호하는 색 구성표를 선택할 수 있도록 사이트 헤더에 렌더링되는 컴포넌트입니다.

#### `LanguageSelect`

**기본 컴포넌트:** [`LanguageSelect.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/LanguageSelect.astro)

사용자가 다른 언어로 전환할 수 있도록 사이트 헤더에 렌더링되는 컴포넌트입니다.

---

### 전역 사이드바

Starlight의 전역 사이드바에는 메인 사이트 탐색이 포함되어 있습니다.
좁은 뷰포트에서는 드롭다운 메뉴 뒤에 숨겨져 있습니다.

#### `Sidebar`

**기본 컴포넌트:** [`Sidebar.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Sidebar.astro)

전역 탐색이 포함된 페이지 콘텐츠 앞에 렌더링되는 컴포넌트입니다.
기본적으로 충분히 넓은 뷰포트에서는 사이드바로 나타나고, 작은 (모바일) 뷰포트에서는 드롭다운 메뉴로 나타납니다.
또한, 모바일 메뉴 내부에 추가 항목을 표시하기 위해 [`<MobileMenuFooter />`](#mobilemenufooter)를 렌더링합니다.

#### `MobileMenuFooter`

**기본 컴포넌트:** [`MobileMenuFooter.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/MobileMenuFooter.astro)

모바일 드롭다운 메뉴 하단에 렌더링되는 컴포넌트입니다.
기본적으로 [`<ThemeSelect />`](#themeselect)와 [`<LanguageSelect />`](#languageselect)를 렌더링합니다.

---

### 페이지 사이드바

Starlight의 페이지 사이드바는 현재 페이지의 하위 제목을 간략하게 설명하는 목차를 표시합니다.
좁은 뷰포트에서는 고정된 드롭다운 메뉴로 축소됩니다.

#### `PageSidebar`

**기본 컴포넌트:** [`PageSidebar.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/PageSidebar.astro)

목차를 나타내기 위해 메인 페이지의 콘텐츠 앞에 렌더링되는 컴포넌트입니다.
기본적으로 [`<TableOfContents />`](#tableofcontents)와 [`<MobileTableOfContents />`](#mobiletableofcontents)를 렌더링합니다.

#### `TableOfContents`

**기본 컴포넌트:** [`TableOfContents.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/TableOfContents.astro)

더 넓은 뷰포트에서 현재 페이지의 목차를 렌더링하는 컴포넌트입니다.

#### `MobileTableOfContents`

**기본 컴포넌트:** [`MobileTableOfContents.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/MobileTableOfContents.astro)

작은 (모바일) 뷰포트에서 현재 페이지의 목차를 렌더링하는 컴포넌트입니다.

---

### 콘텐츠

이 컴포넌트들은 페이지 콘텐츠의 메인 열에 렌더링됩니다.

#### `Banner`

**기본 컴포넌트:** [`Banner.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Banner.astro)

각 페이지 상단에 렌더링되는 배너 컴포넌트입니다.
기본적으로 페이지의 [`banner`](/ko/reference/frontmatter/#banner) 프론트매터 속성을 사용하여 렌더링 여부를 결정합니다.

#### `ContentPanel`

**기본 컴포넌트:** [`ContentPanel.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/ContentPanel.astro)

메인 콘텐츠 열의 섹션을 감싸는 레이아웃 컴포넌트입니다.

#### `PageTitle`

**기본 컴포넌트:** [`PageTitle.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/PageTitle.astro)

현재 페이지의 `<h1>` 요소를 포함하는 컴포넌트입니다.
기본 구현과 같이 `<h1>` 요소에 `id="_top"`을 설정해야 합니다.

#### `DraftContentNotice`

**기본 컴포넌트:** [`DraftContentNotice.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/DraftContentNotice.astro)

현재 페이지가 초안으로 표시되면 개발 중에 사용자에게 표시되는 알림입니다.

#### `FallbackContentNotice`

**기본 컴포넌트:** [`FallbackContentNotice.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/FallbackContentNotice.astro)

현재 언어에 대한 번역이 제공되지 않는 페이지에서 사용자에게 표시되는 알림입니다.
다국어 사이트에서만 사용됩니다.

#### `Hero`

**기본 컴포넌트:** [`Hero.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Hero.astro)

프론트매터에서 [`hero`](/ko/reference/frontmatter/#hero)를 설정했을 때, 페이지 상단에 렌더링되는 컴포넌트입니다.
기본적으로 큰 제목, 태그라인, 클릭 유도 문구 링크와 선택적 이미지를 표시합니다.

#### `MarkdownContent`

**기본 컴포넌트:** [`MarkdownContent.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/MarkdownContent.astro)

각 페이지의 메인 콘텐츠 주위에 렌더링되는 컴포넌트입니다.
기본적으로 마크다운 콘텐츠에 적용할 기본 스타일을 설정합니다.

Markdown 콘텐츠 스타일은 `@astrojs/starlight/style/markdown.css`에도 노출되며 `.sl-markdown-content` CSS 클래스로 범위가 지정됩니다.

---

### 바닥글

이 컴포넌트들은 페이지 콘텐츠의 메인 열 하단에 렌더링됩니다.

#### `Footer`

**기본 컴포넌트:** [`Footer.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Footer.astro)

각 페이지 하단에 표시되는 바닥글 컴포넌트입니다.
기본적으로 [`<LastUpdated />`](#lastupdated), [`<Pagination />`](#pagination), 그리고 [`<EditLink />`](#editlink)를 표시합니다.

#### `LastUpdated`

**기본 컴포넌트:** [`LastUpdated.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/LastUpdated.astro)

마지막 업데이트 날짜를 표시하기 위해 페이지 바닥글에 렌더링되는 컴포넌트입니다.

#### `EditLink`

**기본 컴포넌트:** [`EditLink.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/EditLink.astro)

페이지를 편집할 수 있는 링크를 표시하기 위해 페이지 바닥글에 렌더링되는 컴포넌트입니다.

#### `Pagination`

**기본 컴포넌트:** [`Pagination.astro`](https://github.com/withastro/starlight/blob/main/packages/starlight/components/Pagination.astro)

Component rendered in the page footer to display navigation arrows between previous/next pages.

이전/다음 페이지 사이에 탐색 화살표를 표시하기 위해 페이지 바닥글에 렌더링되는 컴포넌트입니다.
