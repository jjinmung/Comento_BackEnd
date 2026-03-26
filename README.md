# 🌐 Network Study: HTTP & Browser Workflow

이 문서는 네트워크의 기초인 HTTP 통신 방식과 브라우저의 동작 원리를 학습하고 정리한 기록입니다.

---

## 1. HTTP(HyperText Transfer Protocol) 통신
HTTP는 클라이언트(브라우저)와 서버 간에 데이터를 주고받기 위한 **응용 계층 프로토콜**입니다.

### 📍 주요 특징
*   **비연결성 (Connectionless):** 클라이언트가 요청을 보내고 서버가 응답을 마치면 연결을 끊어버리는 방식입니다. 자원 낭비를 줄일 수 있습니다.
*   **무상태성 (Stateless):** 서버가 클라이언트의 이전 상태를 기억하지 않습니다. (이를 보완하기 위해 쿠키, 세션, 토큰 등을 사용합니다.)
*   **구조:** 
    *   **Request:** `Method(GET, POST...)`, `Path`, `Version`, `Headers`, `Body`
    *   **Response:** `Version`, `Status Code(200, 404...)`, `Headers`, `Body`

---

## 2. 브라우저에 URL을 입력했을 때의 전체 과정
사용자가 브라우저 주소창에 URL을 입력하면 다음과 같은 복잡한 단계를 거쳐 화면이 나타납니다.

### Step 1: DNS Lookup (주소 찾기)
브라우저는 도메인 이름(예: `www.google.com`)을 컴퓨터가 이해할 수 있는 **IP 주소**로 변환하기 위해 DNS 서버에 요청을 보냅니다.

### Step 2: TCP 3-Way Handshake (연결 수립)
데이터를 전송하기 전, 클라이언트와 서버 간의 신뢰성 있는 연결을 위해 세 번의 확인 과정을 거칩니다. (SYN -> SYN-ACK -> ACK)

### Step 3: HTTP Request & Response (데이터 요청 및 응답)
1.  **Request:** 브라우저가 서버에 HTML, 이미지 등의 데이터를 달라고 요청을 보냅니다.
2.  **Response:** 서버는 요청을 확인하고 해당 데이터를 응답 메시지에 담아 보냅니다.

### Step 4: Browser Rendering (화면 그리기)
받아온 데이터를 브라우저 엔진이 처리하여 사용자에게 보여줍니다.
1.  **Parsing:** HTML을 읽어 `DOM 트리`를, CSS를 읽어 `CSSOM 트리`를 만듭니다.
2.  **Render Tree:** 위 두 트리를 합쳐 화면에 실제로 보일 `Render 트리`를 생성합니다.
3.  **Layout & Paint:** 각 요소의 위치를 계산하고 화면에 실제 픽셀을 채웁니다.

---

## 🚀 Summary Table

| 단계 | 핵심 키워드 | 주요 역할 |
| :--- | :--- | :--- |
| **DNS** | IP 변환 | 도메인 주소를 실제 서버 주소로 매핑 |
| **TCP** | Handshake | 서버와 클라이언트 간 연결 통로 개설 |
| **HTTP** | Request/Response | 실질적인 데이터 교환 |
| **Rendering** | DOM / CSSOM | 코드 데이터를 시각적 화면으로 변환 |

---
