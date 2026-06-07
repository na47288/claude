# 나현 지식공간 — 운영 가이드

## 웹사이트 주소
**https://na47288.github.io/claude/**

---

## 구조 설명

이 사이트는 GitHub에 저장된 파일들이 자동으로 웹페이지로 보이는 방식이에요.

```
claude/ (GitHub 저장소)
  ├── index.html          ← 사이트 뼈대 (사이드바 목록 + 틀)
  ├── articles/           ← 아티클 내용 파일들
  │     ├── macro1.html
  │     ├── semi-sobu.html
  │     ├── semi-siltron.html
  │     ├── semi-oxidation.html
  │     ├── semi-hbm.html
  │     ├── semi-etch.html
  │     ├── semi-deposition.html
  │     ├── semi-metal.html
  │     ├── semi-test.html
  │     ├── semi-packaging.html
  │     ├── semi-chey.html
  │     ├── power-age.html
  │     ├── power-kgrid.html
  │     └── power-package.html
  └── images/             ← 차트·이미지 파일들
```

---

## 새 아티클 추가하는 법

### 1단계 — 아티클 HTML 파일 만들기

`articles/` 폴더에 새 파일을 추가해요. 파일명 규칙:
- 거시경제: `macro-이름.html`
- 반도체: `semi-이름.html`
- 전력: `power-이름.html`
- 데일리 뉴스: `daily-YYMMDD.html`

파일 내용은 `<div class="article-wrap">` 으로 시작하고 `</div>` 로 끝내면 돼요. (전체 HTML 구조 불필요)

### 2단계 — index.html에 사이드바 항목 추가

`index.html`의 사이드바 부분에 버튼 하나 추가:
```html
<button class="nav-sub-item" id="ni-파일명" onclick="showPage('파일명')">
  <span class="nav-sub-dot"></span>
  <span>표시될 제목</span>
  <span class="nav-item-date">06.03</span>
</button>
```

그리고 `pages` 객체에도 추가:
```javascript
'파일명': { file: 'articles/파일명.html', navId: 'ni-파일명', navType: 'sub', bc: ['카테고리', '제목'] },
```

### 3단계 — GitHub에 업로드

Claude에게 이렇게 말하면 돼요:
> "articles/파일명.html 파일 GitHub에 올려줘"

---

## 현재 아티클 목록

### 거시경제
| 파일 | 제목 | 출처 |
|------|------|------|
| macro1.html | 3고(高) 시대 — 고물가/고금리/고환율 | 자체 정리 |

### 경제잡지 — 260611 반도체/전력

**한경비즈니스 1591호 (2026.06.03)**
| 파일 | 제목 |
|------|------|
| semi-sobu.html | '500조 호황'에 반도체 소부장은 잘 크고 있을까? |
| semi-siltron.html | 반도체는 웨이퍼에서 시작한다… SK실트론이 5조 몸값 받는 이유 |
| semi-oxidation.html | 웨이퍼 위 든든한 '보호막' 산화공정, 수율 개선까지 |
| semi-hbm.html | "쌀이 좋아야 밥이 맛있다" 한국 HBM의 비결 |
| semi-etch.html | 높이 쌓을수록 빛난다 — '식각 1인자'와 K-소부장의 도전 |
| semi-deposition.html | 코스닥 60위가 '톱5'로 — 원자층 쌓는 '증착 장비'가 판을 바꿨다 |
| semi-metal.html | 코로나바이러스보다 작게 — 반도체 전기 혈관을 뚫다 |
| semi-test.html | 반도체 건강검진센터 — '수율'을 잡는 자가 시장을 지배한다 |
| semi-packaging.html | 배트 슈트를 입은 반도체 — 'AI 패권'을 조율하는 K-소부장 |
| semi-chey.html | 최태원은 어떻게 반도체 질서를 바꿨나 |

**매경이코노미 2361호 (2026.06.03)**
| 파일 | 제목 |
|------|------|
| power-age.html | AI는 '에너지 블랙홀' — 大전력의 시대가 온다 |
| power-kgrid.html | 전기 먹는 AI, 전력기기 몸값 올랐다 |
| power-package.html | K전력 승부처는 '전력망 패키지' |

---

## 스타일 컴포넌트 치트시트

자주 쓰는 HTML 조각 모음이에요.

### 카드
```html
<div class="card">
  <div class="card-title">제목</div>
  <div class="card-body">내용</div>
</div>
```

### 강조 박스
```html
<div class="hl"><strong>포인트</strong> — 내용</div>
```

### 결론 카드 (검정 배경)
```html
<div class="summary-card">
  본문 내용
  <div style="margin-top:14px; padding-top:14px; border-top:1px solid rgba(255,255,255,0.15); font-size:12.5px; color:rgba(255,255,255,0.6);">
    한 줄 요약 — 
  </div>
</div>
```

### 표
```html
<div class="tbl-wrap">
  <table class="tbl">
    <thead><tr><th>열1</th><th>열2</th></tr></thead>
    <tbody>
      <tr><td class="lbl">항목</td><td class="val">내용</td></tr>
    </tbody>
  </table>
</div>
```

### 흐름도
```html
<div class="flow-wrap">
  <div class="flow">
    <div class="flow-box">단계1</div>
    <div class="flow-arrow">→</div>
    <div class="flow-box">단계2</div>
  </div>
</div>
```

### 배지(뱃지)
```html
<span class="badge badge-blue">파란색</span>
<span class="badge badge-red">빨간색</span>
<span class="badge badge-green">초록색</span>
<span class="badge badge-gray">회색</span>
```
