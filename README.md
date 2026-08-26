# The Binding of Isaac 모작

Unity로 제작한 2D 탑다운 로그라이크 모작입니다.
방 단위로 나뉜 던전을 돌며 적을 처치하고, 아이템으로 능력치를 쌓아 보스를 잡는 원작의 핵심 루프를 구현했습니다.

## 프로젝트 개요

- **엔진**: Unity `2021.3.16f1`
- **장르**: 2D 탑다운 로그라이크 / 트윈스틱 슈터
- **인원**: 5인 팀 (담당 영역별 폴더 분리)
- **스테이지**: Basement, Cave

## 구현 범위

### 플레이어

- 머리·몸통 분리 조작 — 이동 방향과 발사 방향을 따로 처리
- 눈물(탄) 발사, 사거리·연사·이동속도 스탯 반영
- 피격·무적 시간·사망 연출

### 던전

- 방 단위 이동과 카메라 전환, 방 클리어 판정에 따른 문 개폐
- 문 종류별 처리 — 일반문 / 잠긴문(열쇠) / 보스룸 / 다음 스테이지
- 폭탄으로 부수는 벽, 색깔 바위, 큰 바위, 똥 등 파괴 가능 오브젝트

### 아이템 · 상호작용

- 픽업류 — 하트, 코인, 열쇠, 폭탄
- 패시브 아이템 — The Sad Onion, Blood of the Martyr, Magic Mushroom, Stigmata 등 스탯 변화 적용
- 알약 9종 — 체력·공격력·이동속도·눈물 증감 랜덤 효과
- 상점과 제단(Alter) — 코인 소비 구매, 아이템 획득 연출

### 적 · 보스

- 일반 적 8종 — Charger, Chubber, Clotty, Globin, Horf, Melee, Nest, Pooter (각자 다른 이동·공격 패턴)
- 보스 2종
  - **Monstro** — 점프 낙하, 탄막 확산
  - **Mom** — 발/손 부위별 공격, 부위 피격 판정, HP 바

### 시스템

- 사운드 — BGM/SFX 분리 관리, 볼륨 저장·복원
- 로딩 씬, 메인 메뉴 카메라 연출, 일시정지, 보스 인트로 컷

## 스크립트 구성

담당 영역별로 폴더를 나눠 작업했습니다.

```text
Assets/@Project/
├── BDH/Scripts/          # 플레이어 조작·탄·UI, 아이템 효과 적용, 맵 트리거
├── KHJ_/Scripts/         # 아이템·상점·제단, 문/파괴 오브젝트, 이펙트
│   ├── Items/            #   Alter, Pills, ShopItems, ItemCoin/Heart/Key/Bomb
│   ├── Objects/          #   LockDoor, NewDoorScripts, BombRock, DestroyRock, Fire, Poop
│   └── Effect/           #   BloodGibs, BossDoorEffect, ObjectBreath
├── Park/Script/          # 적 AI 8종, 보스 2종(Monstro·Mom), 탄 처리
├── huneww/Scripts/       # GameManager, 사운드, 로딩·메뉴·일시정지 연출
└── JSJ/Scenes/           # 스테이지 씬 구성 (Basement, Cave)
```

## 실행

Unity `2021.3.16f1`로 프로젝트를 열고 아래 씬을 실행합니다.

```text
Assets/@Project/huneww/MainMenuScene/MainMenu.unity
```

스테이지만 바로 확인하려면 `Assets/@Project/JSJ/Scenes/Basement.unity`를 엽니다.

---

> 학습 목적의 모작 프로젝트입니다. 원작 *The Binding of Isaac* 의 저작권은 Edmund McMillen 및 Nicalis, Inc.에 있습니다.
