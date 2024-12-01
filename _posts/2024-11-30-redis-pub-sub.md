---
title: "Redis Pub/Sub: 기본 가이드"
date: 2024-12-02
categories: redis
comments: false
---

Redis의 Pub/Sub(Publish/Subscribe) 는 실시간 메시징 시스템의 기초를 제공하는 기능입니다.  
다양한 클라이언트 간에 메시지를 전달할 수 있습니다. 이 글에서는 Redis Pub/Sub의 개념과 사용법을 간결하면서도 실습 중심으로 설명하겠습니다.😊

## Pub/Sub란?
Pub/Sub는 `Publisher`와 `Subscriber` 간의 비동기 메시징 모델입니다.  
Redis에서 Pub/Sub는 알림, 실시간 채팅, 이벤트 스트리밍 같은 다양한 상황에서 활용됩니다.
### 주요 개념
- Publisher: 메시지를 특정 "채널"로 발행합니다.
- Subscriber: 특정 "채널"을 구독하고, 해당 채널로 발행된 메시지를 수신합니다.
- Channel: Publisher와 Subscriber가 메세지를 주고받는 채널

### 동작 흐름
1. Subscriber는 Redis에서 특정 채널을 구독 요청합니다.
2. Publisher는 Redis에 메세지를 발행합니다.
3. Redis는 해당 채널을 구독 중인 모든 Subscriber에게 메세지를 전달합니다.

## Pub/Sub 명령어
1. SUBSCRIBE: 특정 채널 구독
```bash
SUBSCRIBER channel_name
```
2. PUBLISH: 특정 채널로 메세지 발행
```bash
PUBLISH channel_name "message"
```
3. UNSUBSCRIBE: 특정 채널 구독 해제
```bash
UNSUBSCRIBE channel_name
```

## Pub/Sub 예제
`redis-cli`를 사용하여 Pub/Sub 예제를 함께 진행해 보세요.
1. Subscriber 채널 구독
```bash
subscribe notifications
```
**출력 결과**  
![keys]({{ "/assets/images/20241202/subscribe.png"}})  
2. Publisher로 메세지 발행 (다른 터미널에서 실행합니다.)
```bash
publish notifications "Hello, Redis!"
```
**출력 결과**  
![keys]({{ "/assets/images/20241202/publish.png"}})  
3. Subscriber가 메세지 수신  
**notifications 채널에 메세지를 받은 결과**  
![keys]({{ "/assets/images/20241202/subscribe-result.png"}})  

## Pub/Sub 활용 예시
1. 실시간 채팅
사용자 간 실시간 메시지 전달 시스템을 구현할 때 사용합니다.  
예: 여러 사용자가 동일한 채널을 구독하면 채팅방처럼 작동
2. 알림 시스템
서버에서 이벤트 발생 시 사용자에게 실시간 알림 제공합니다.  
예: 특정 상품의 가격이 변경될 때 사용자에게 알림 발송
3. 로그 스트리밍
애플리케이션 로그를 중앙 서버로 실시간 전송 및 모니터링 합니다.  
예: 서버의 에러 로그를 실시간으로 확인

## 결과
Redis Pub/Sub는 실시간 데이터 전달이 필요한 간단한 서비스에 적합합니다.  
Pub/Sub의 개념과 특성을 이해하고 다양한 시나리오에 직접 적용하여 학습해 보세요.
