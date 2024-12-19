# Plan Note

## 프로젝트 개요
바이낸스 홈페이지 클론 프로젝트는 최소 요구 사항을 충족한 후 점진적으로 기능을 확장하여 완성도를 높이는 것을 목표로 합니다. 본 프로젝트는 다음과 같은 주요 기술 스택을 사용하여 개발됩니다:

- **Next.js v15**
- **Tanstack Query**
- **Recoil**
- **Tailwind CSS**

## 개발 전 확인 사항

### 1. 기술 스택 리서치 및 기능 문서화
개발 시작 전에 각 기술 스택에 대한 리서치를 진행하고, 프로젝트에 필요한 기능을 문서로 정리합니다.

- [ ] **Next.js v15**

- [ ] **Tanstack Query**

- [ ] **Recoil**

개발 중 필요한 추가 기능이 발생할 경우, 별도로 문서화하여 관리합니다.

### 2. 차트 라이브러리 리서치
비트코인 차트 구현에 필요한 스펙을 정리하고, 이를 충족하는 라이브러리를 조사하여 선정합니다.

- **필요 스펙 정리**
  - 실시간 데이터 반영
  - 다양한 차트 유형 지원 (캔들스틱, 라인 등)
  - 사용자 인터랙션 (확대, 축소, 도구 등)
  - 퍼포먼스 최적화
  - 실제 구현 예시 데이터를 찾기 쉬운지

- **리서치 대상 라이브러리**
  - [ ] [Chart.js](https://github.com/chartjs/Chart.js)
  - [ ] [Recharts](https://github.com/recharts/recharts)
  - [ ] [Lightweight Charts](https://github.com/tradingview/lightweight-charts)
  - 기타 고성능 차트 라이브러리

리서치 결과를 바탕으로 프로젝트 요구 사항에 가장 부합하는 라이브러리를 선택합니다.

## 개발 단계
단계 별로 scope을 정리하여 개발 계획을 수립합니다.

### 0단계: 배포 설계 및 binance api 호출 테스트
- aws lambda, s3, cloudfront, github action 활용 예정
- https://github.com/aws-samples/aws-lambda-nextjs
- binance api 사용하려는 api 호출 테스트
- https://github.com/binance/binance-connector-typescript?tab=readme-ov-file
- 가능하면 websocket도 테스트 해두기

### 1단계: 최소 요구 사항을 충족하는 구현
- binance api로 목업데이터 확보
- 최소한의 데이터에서 임의로 랜덤하게 값이 변동되도록 nextjs 서버 세팅
- polling으로 구현하되 시간간격을 다소 랜덤하게 세팅하여 기본 데이터 세팅 예정
- 데이터 받으면 chart 및 orderbook등 에서 그대로 보여주도록 구현
- 차트는 분봉으로 구현

### 2단계: 데이터 세팅 완료 후 차트 구현
- polling 대신 SSE 사용하여 실시간 데이터 업데이트
  - [lambda sse](https://docs.aws.amazon.com/lambda/latest/dg/configuration-response-streaming.html)
- chart ux 보강 확대 축소 기능

### 3단계: 모킹 데이터가 아닌 실제 데이터로 구현
- nextjs 서버에서 binance api로 polling 구현
- s3 또는 dynamodb 사용하여 데이터 저장
- 차트 월봉, 주봉, 일봉, 시봉, 분봉 구현

### 4단계: 실시간 데이터로 구현
- 웹소켓 연결 설정
- 이동평균선 구현

## 테스트 및 품질 보증
개발이 완료된 후 일부 테스트 코드를 추가하여 기능의 안정성을 확보합니다.

- **단위 테스트**


---
