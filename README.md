# AI Game Arcade

AI가 만들고, AI가 평가하고, 기능 테스트를 통과한 작품만 배포한 브라우저 미니게임 갤러리.

## 무엇인가

`gpt-5.4-mini`가 2026 트렌드 장르로 생성한 HTML 단일 파일 브라우저 게임 모음입니다. 각 게임은 사람이 직접 고른 것이 아니라, 다음 파이프라인을 거쳐 자동 선별됩니다.

1. **생성** — `gpt-5.4-mini`가 게임 코드를 만든다.
2. **AI 비전 평가** — 화면을 보고 완성도/플레이 가능성을 점수화한다.
3. **실제 조작 기능 테스트** — 헤드리스 Chrome(CDP)으로 실제 키 입력·클릭을 넣어 동작을 검증한다.
4. **자동 배포** — 기능 테스트를 **통과한 게임만** 이 갤러리에 올라간다.

> 기능 테스트가 없던 초기에는 비전 점수만으로 걸렀으나, 이후 실제 조작 테스트를 게이트로 추가했습니다. 예를 들어 IDLE FORGE는 "클릭해도 수치가 오르지 않는" 동작 버그로 기능 테스트를 통과하지 못해 한때 배포에서 제외되기도 했습니다.

## 수록 게임

총 16종. 점수는 `manifest.json` 기준이며, **비전**은 AI 완성도 평가, **재미**는 플레이 재미 평가 점수입니다.

| 게임 | slug | 비전 | 재미 |
|---|---|---|---|
| CHIME LOOP | `chime-loop` | 86 | 64 |
| LANTERN GRID | `daily-lantern-grid` | 86 | 63 |
| WORD RUSH | `daily-word` | 84 | 78 |
| ECHO RIFT | `echo-rift-survivor` | 81 | 28 |
| GEM MATCH | `gem-match` | 90 | 58 |
| GLOW BLOOM | `glow-bloom-raid` | 80 | 63 |
| IDLE FORGE | `idle-forge` | 88 | 62 |
| MERGE 2048 | `merge-2048` | 84 | 54 |
| MIDNIGHT SIGNAL | `midnight-signal` | 84 | 66 |
| MOSS CLOCK | `moss-clock` | 86 | 62 |
| NEON DASH | `neon-dash` | 84 | 68 |
| ORBIT SWAP | `orbit-swap-sprint` | 86 | 78 |
| TIDE TACTICIAN | `tide-tactician` | 84 | 68 |
| TOWER LINE | `tower-defense` | 78 | 52 |
| DEAD HOUR | `zombie-survival` | 84 | 64 |
| PULSE JUMP | `pulse-jump-arena` | 85 | 72 |

## 플레이 방법

GitHub Pages로 배포되어 있습니다. 브라우저에서 바로 열어 플레이하세요.

- 갤러리 허브: **https://bat1120.github.io/ai-game-arcade/**
- 개별 게임: `https://bat1120.github.io/ai-game-arcade/<slug>/` (예: `.../gem-match/`)

허브(`index.html`)에서 썸네일·점수와 함께 16종을 한눈에 보고 카드를 눌러 각 게임으로 이동합니다.

## 제작 파이프라인

이 저장소는 파이프라인이 만들어낸 **결과물(배포된 게임 갤러리)** 만 담습니다. 생성·평가·배포를 수행하는 파이프라인 소스 코드는 별도 저장소 [`HiMedia13/ai-game-arcade`](https://github.com/HiMedia13/ai-game-arcade)에 있습니다.

## 구조

```
.
├── index.html          # 갤러리 허브 (16종 카드 목록)
├── manifest.json       # 게임 목록·점수(비전/재미) 메타데이터
├── .nojekyll           # GitHub Pages Jekyll 처리 비활성화
└── <slug>/             # 게임별 폴더 (16개)
    ├── index.html      # 게임 본체 (단일 HTML 파일)
    ├── thumb.png       # 갤러리 썸네일
    └── pt_before.png / pt_after.png   # 일부 게임의 기능 테스트 전/후 캡처
```
