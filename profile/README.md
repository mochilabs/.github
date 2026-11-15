<div align="center">
  <img src="https://avatars.githubusercontent.com/u/261911938?s=200" alt="mochiLabs" width="120" height="120" />
  <h1>mochiLabs</h1>
  <p>
    디스코드 음악 봇 <a href="https://github.com/mochilabs/SiruBOT">SiruBOT</a>과 Lavalink v4 오디오 플러그인, 관련 백엔드 서비스를 개발하고 운영합니다.
  </p>
  <p>
    <a href="https://kafuu.space">웹사이트</a> ·
    <a href="https://status.kafuu.space">서비스 상태</a> ·
    <a href="https://discord.gg/Np9X5VqPdF">디스코드 서버</a>
  </p>
</div>

## 주요 프로젝트

### [SiruBOT](https://github.com/mochilabs/SiruBOT)

디스코드 음악 봇과 웹 대시보드, 백엔드 서비스를 하나에 담은 TypeScript 모노레포입니다.

- Lavalink v4 기반 재생, 대기열 관리, 반복·셔플·탐색, 슬래시 명령어 검색 자동 완성, SponsorBlock 건너뛰기, 챕터, 싱크 가사를 지원합니다.
- Next.js와 React 19로 작성된 웹 대시보드에서 실시간 플레이어 제어, 서버 설정, 개인 플레이리스트, 청취 통계, 티켓, 방송 알림(YouTube·Twitch·치지직), 샤드 상태를 다룹니다.
- `bot`, `dashboard`, `data-api`, `shardmanager`, `storage`, `notifier` 6개 독립 프로세스와 4개 공용 패키지로 구성되며, Redis pub/sub, 내부 HTTP, WebSocket으로만 통신해 무중단 샤드 재배치를 지원합니다.

### [lavalink_mixer](https://github.com/mochilabs/lavalink_mixer)

Lavalink v4 서버에서 Opus 인코딩 전에 오디오를 합성하는 Kotlin 플러그인입니다. Lavalink 소스 수정 없이 단독 JAR로 동작합니다.

- 곡 쌍의 BPM, 비트 그리드, 보컬 구간을 분석해 베이스 스왑(4차 Linkwitz-Riley 크로스오버), 비트 매칭 블렌드, 다운비트 컷, 필터 스윕, 이퀄 파워 크로스페이드 등 6가지 전환 전략 중 하나를 고릅니다.
- EBU R128 음량 측정 및 목표 음량(-14 LUFS) 감쇠, 곡 앞뒤 무음 제거와 실시간 끝무음 감지를 수행합니다.
- 음악 볼륨을 낮추는(ducking) 순차·병렬 공지 오디오 재생과, 에포크·멱등성 키를 사용하는 Protocol v2 서버 주도 큐 제어를 지원합니다.

## 저장소

| 저장소 | 언어 | 설명 |
| --- | --- | --- |
| [SiruBOT](https://github.com/mochilabs/SiruBOT) | TypeScript | 디스코드 음악 봇 플랫폼 모노레포 (`bot`, `dashboard`, `data-api`, `shardmanager`, `storage`, `notifier`) |
| [lavalink_mixer](https://github.com/mochilabs/lavalink_mixer) | Kotlin | 서버 측 크로스페이드, 비트 매칭, 베이스 스왑, 음량 정규화, TTS 덕킹을 수행하는 Lavalink v4 플러그인 |
| [slyrics](https://github.com/mochilabs/slyrics) | TypeScript | 별도 API 키 없이 가사를 조회하는 라이브러리 |
| [lavalink-stats](https://github.com/mochilabs/lavalink-stats) | JavaScript | Lavalink 노드 상태를 주기적으로 수집해 SQLite에 기록하는 모니터링 도구 |
| [yt-cipher](https://github.com/mochilabs/yt-cipher) | TypeScript | Lavalink `remoteCipher` 연동용 YouTube 플레이어 시그니처 복호화 HTTP 서비스 |
| [docker-services](https://github.com/mochilabs/docker-services) | Shell | `kafuu.space` 호스트 서비스용 Docker Compose 설정 모음 |

## 기술 스택

| 영역 | 사용 기술 |
| --- | --- |
| Bot & Web | TypeScript, Node.js 22, Yarn 4, Turborepo, discord.js, Sapphire, lavalink-client, Next.js, React 19, Fastify 5 |
| Audio & Plugins | Kotlin, Java 17, Lavalink v4, Lavaplayer, lavadsp |
| Data & Infra | PostgreSQL, Prisma 7, Redis, SQLite, Docker, GitHub Actions |
