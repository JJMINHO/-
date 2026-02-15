# Bitball_Project
>Bitball_Project는 Logisim Evoluion을 이용하여 CPU없이 순수 디지털 논리 소자만으로 구현한 야구 시뮬레이션 게임입니다.


## Project Overview
이 프로젝트는 디지털 논리 및 시스템 과목의 텀 프로젝트로, 복잡한 규칙을 가진 스포츠인 야구를 논리회로로 구현하는 것을 목표로 했습니다. 단순한 관전형 시뮬레이션이 아닌, 확률 기반의 타격 시스템과 주루 플레이, 점수 계산, 이닝 교체 등 야구의 핵심 규칙을 하드웨어 레벨에서 구현했습니다.

## 기획 의도
- 복잡한 상태 머신 구현: 스트라이크/볼 판정, 아웃 카운트, 주자 만루 상황 등 다양한 변수를 처리하며 논리회로의 설계를 깊이 있게 이해하고자 했습니다.

- 확률 기반 로직 설계: 난수 생성기를 통해 타자의 타율과 장타율에 따른 현실적인 게임 결과를 도출합니다.

## 사용 기술
Simulator: Logisim (Logisim-evolution)

Components: Logic Gates (AND, OR, NOT), Flip-Flops (D, JK), Counter, Multiplexer, Splitter, ROM, Comparator, Adder etc.

## System Architecture
이 회로는 크게 타격 판정, 주루 플레이, 점수 계산, 게임 진행의 4가지 핵심 모듈로 구성되어 있습니다.

1. 타격 순서 및 스탯 동기화

Modulo-9 Counter: 1번부터 9번 타자까지 순서대로 타석에 들어서도록 제어합니다.

ROM (Read-Only Memory): 각 타자의 타율과 장타율 데이터를 16진수 코드로 저장하여 관리합니다.
                        타자가 타석에 들어서면 해당 타자의 스탯을 불러옵니다.


2. 타격 결과 판정 로직 

난수 생성기 (RNG) : 카운터를 이용해 예측 불가능한 난수를 생성합니다.

비교기 (Comparator) : 생성된 난수와 타자의 타율을 비교하여 Hit 또는 Out을 판정합니다.

Hit인 경우, 다시 난수와 장타율을 비교하여 1루타, 2루타, 3루타, 홈런을 결정합니다.


3. 주루 및 점수 시스템
Shift Register: 1루, 2루, 3루의 주자 상태를 저장합니다.
                안타 발생 시 비트를 시프트(Shift)하여 주자를 진루시킵니다.

Adder : 홈으로 들어온 주자의 수를 감지하여 총 득점에 합산합니다.

7-Segment Display: 현재 점수, 아웃 카운트, 이닝 정보를 시각적으로 표시합니다.


4. 게임 진행 제어 (Out_Counts & Inning)

Counter: 스트라이크/볼/아웃 카운트를 셉니다.

Reset Logic: 3아웃이 되면 주자와 볼카운트를 초기화하고, 이닝 카운터를 1 증가시킵니다.
            공수 교대 로직을 포함합니다.


## 📸 회로도 및 시뮬레이션 (Screenshots)
- Main Circuit
<img width="2558" height="1940" alt="image" src="https://github.com/user-attachments/assets/6a57727c-cd10-4e4c-a428-81aa3ce5b5f2" />

- Batting_Order Circuit

- Base Circuit

- Runner Circuit

- bit_counter  Circuit

- Out_Counts Circuit

- ordering Circuit

- modulo_counter Circuit

- scoring Circuit

- BASEBALL Circuit



## 설치 방법
Logisim-evolution을 설치합니다.

이 저장소를 클론(Clone)하거나 다운로드합니다.

Logisim에서 src/baseball_game.circ 파일을 엽니다.

