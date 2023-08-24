# 웹소켓과 레디스를 이용한 실시간 선착순 요청처리 만들기

## 2차 요구사항 (2023-08-24)
### Server
- 요청은 순서대로 처리되어야 한다. (Redis SortedSet 사용)
- 정원(1000명)이 다 차면 더 이상 요청을 받지 않는다.
- Redis Pub-Sub 을 사용한다.
- 응답
  - 성공시 처리 순서를 반환한다.
  - 실패시 실패 메시지를 반환한다.

### Client
- 줄서기 버튼을 누르면 HTTP 요청을 보낸다.
- 사용자는 요청시 본인 id 에 해당하는 UUID 를 만들어 요청해야 한다.
- 사용자에게는 내 순번, 총 요청자 정보가 실시간으로 보여져야 한다.

---

## 1차 요구사항 (2023-08-20)
### Server
- 요청은 순서대로 처리되어야 한다. (Redis sortedSet 사용)
- 1건 당 처리 시간은 약 250ms~750ms가 걸린다고 가정한다. (Thread.sleep() 사용)
- 응답
  - 성공시 처리 순서를 반환한다.
  - 실패시 실패 메시지를 반환한다. 

### Client
- 줄서기 버튼을 누르면 HTTP 요청을 보낸다.
- 사용자는 내 순번, 총 요청자 정보가 실시간으로 보여져야 한다.
