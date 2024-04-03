# Kafka CLI 정리

1. kafka-server-start.sh

- 설명: 카프카 서버를 시작하는 sh 파일이다. 카프카 서버를 시작하기 위해선 
ZooKeeper와 Distributed를 실행 시킨 후 사용하려는 속성 파일의 경로를 전달하여야 한다.

- 실행 방법: ./kafka-server-start.sh server.properties

2. zookeeper-server-start.sh

- 설명: 주키퍼 서버를 시작하는 sh 파일이다. 주키퍼는 카프카의 메타 데이터 관리를 수행한다.

- 실행 방법: ./zookeeper-server-start.sh zookeeper.properties

3. connect-distributed.sh

- 설명: 분산 모드를 시작하는 sh 파일이다. 분산 모드는 작업의 자동 균형을 처리한다.

- 실행 방법: ./connect-distributed.sh connect-distributed.properties


4. kafka-consumer-groups.sh

- 설명: 생성된 소비자 그룹에 관한 내용을 출력하는 sh 파일이다.

- 실행 방법: bin/kafka-consumer-groups.sh --bootstrap-server 192.168.1.93:9092

-  --list 옵션: 그룹 목록을 볼 수 있다.

-  --group my_group_name --describe 옵션: 토픽별 offset 정보 등을 알 수 있다.

-  --group my_group_name --delete 옵션: 소비자 그룹을 제거할 수 있다.

5. kafka-console-consumer.sh

- 설명: 특정 토픽에 생성된 콘솔을 수신하는 .sh 파일이다.

- 실행 방법: bootstrap-server와 연결할 서버/포트를 지정한 후 토픽을 입력하여 수신한다.
(예: ./kafka-console-consumer.sh --bootstrap-server 192.168.1.93:9092 --topic a3archive-ipc)

6. kafka-console-producer.sh

- 설명: 특정 토픽에 콘솔을 생성하는 sh 파일이다. 

- 실행 방법: ./kafka-console-producer.sh --bootstrap-server 192.168.1.93:9092 --topic a3archive-ipc

