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

  다음은 kafka-console-consumer.sh에서 사용할 수 있는 옵션들이다:
  --bootstrap-server <String: server to connect to> 필수항목이다.
    
  --consumer-property <String: consumer_prop>  
    사용자 정의 속성을 소비자에게 전달하는 메커니즘으로, key=value 형식으로 사용한다.
    
  --consumer.config <String: config file>  
    컨슈머 설정 속성 파일. 단, [consumer-property]가 이 구성보다 우선한다.
    
  --enable-systest-events  
    소비자의 생명주기 이벤트를 기록한다. (시스템 테스트용)
    
  --formatter <String: class>  
    메시지를 표시하기 위해 사용할 클래스의 이름. (기본값: kafka.tools.DefaultMessageFormatter)
    
  --formatter-config <String: config file>  
    메시지 포매터를 초기화하는 구성 속성 파일. 단, [property]가 이 구성보다 우선한다.
    
  --from-beginning  
    컨슈머가 이미 설정된 오프셋이 없다면, 로그에 있는 가장 이른 메시지부터 시작한다.
    
  --group <String: consumer group id>  
    컨슈머의 컨슈머 그룹 ID.
    
  --help  
    사용법 정보를 출력한다.
    
  --include <String: Java regex (String)>  
    소비에 포함할 토픽의 목록을 지정하는 정규 표현식.
    
  --isolation-level <String>  
    읽기 모드를 설정한다. 'read_committed'로 설정하면 커밋되지 않은 트랜잭션 메시지를 필터링한다.
    'read_uncommitted'로 설정하면 모든 메시지를 읽는다. (기본값: read_uncommitted)
    
  --key-deserializer <String: deserializer for key>  
    키에 대한 역직렬화기.
    
  --max-messages <Integer: num_messages>  
    종료하기 전에 소비할 최대 메시지 수. 지정되지 않으면 소비는 계속된다.
    
  --offset <String: consume offset>  
    소비할 오프셋을 지정한다. 음수가 아닌 숫자로 지정하거나, 'earliest'는 처음부터, 'latest'는 마지막부터 읽는다.
    (기본값: latest)
    
  --partition <Integer: partition>  
    소비할 파티션. 오프셋이 지정되지 않은 경우 파티션의 끝부터 소비가 시작된다.
    
  --property <String: prop>  
    메시지 포매터를 초기화하기 위한 속성들. 기본 속성에는 다음이 포함된다:
    print.timestamp=true|false
    print.key=true|false
    print.offset=true|false
    print.partition=true|false
    print.headers=true|false
    print.value=true|false
    key.separator=<key.separator>
    line.separator=<line.separator>
    headers.separator=<line.separator>
    null.literal=<null.literal>
    key.deserializer=<key.deserializer>
    value.deserializer=<value.deserializer>
    header.deserializer=<header.deserializer>
    
  --skip-message-on-error  
    메시지 처리 중 오류가 발생하면 멈추지 않고 건너뛴다.
    
  --timeout-ms <Integer: timeout_ms>  
    지정된 경우, 소비 가능한 메시지가 지정된 시간 동안 없으면 종료한다.
    
  --topic <String: topic>  
    소비할 토픽.
    
  --value-deserializer <String: deserializer for values>  
    값에 대한 역직렬화기.
    
  --version  
    Kafka 버전을 표시한다.
    
  --whitelist <String: Java regex (String)>  
    DEPRECATED: --include 대신 사용한다. --include가 지정된 경우 무시된다.
    소비할 토픽 목록을 지정하는 정규 표현식.


6. kafka-console-producer.sh

- 설명: 특정 토픽에 콘솔을 생성하는 sh 파일이다. 

- 실행 방법: ./kafka-console-producer.sh --bootstrap-server 192.168.1.93:9092 --topic a3archive-ipc

  다음은 kafka-console-producer.sh에서 사용할 수 있는 옵션들이다:
  
  --batch-size <Integer: size>  
    동기적으로 전송되지 않는 경우에 메시지를 한 번에 보낼 배치 크기. 
    만약 max-partition-memory-bytes가 설정되어 있다면 이 옵션은 대체된다. (기본값: 16384)
  
  --bootstrap-server <String: server to connect to>  
    REQUIRED unless --broker-list (deprecated) is specified. 연결할 서버(들)를 지정한다.
  
  --broker-list <String: broker-list>  
    DEPRECATED, --bootstrap-server 대신 사용하며, --bootstrap-server가 지정되면 무시된다.
  
  --compression-codec [String: compression-codec]  
    압축 코덱을 지정한다. 'none', 'gzip', 'snappy', 'lz4', 'zstd' 중 하나를 선택한다.
    값이 지정되지 않으면 기본값은 'gzip'이다.
  
  --help  
    사용법 정보를 출력한다.
  
  --line-reader <String: reader_class>  
    표준 입력에서 줄을 읽는 데 사용할 클래스의 이름을 지정한다. 기본적으로 각 줄은 별개의 메시지로 읽힌다. (기본값: kafka.tools.ConsoleProducer$LineMessageReader)
  
  --max-block-ms <Long: max block on send>  
    전송 요청 중 블록할 최대 시간. (기본값: 60000)
  
  --max-memory-bytes <Long: total memory in bytes>  
    서버에 보낼 대기중인 레코드를 버퍼링하는 데 사용하는 총 메모리. 
    이 옵션은 프로듀서 구성에서 `buffer.memory`를 제어하는 데 사용된다. (기본값: 33554432)
  
  --max-partition-memory-bytes <Integer: memory in bytes per partition>  
    파티션 당 할당된 버퍼 크기. 이 옵션은 프로듀서 구성에서 `batch.size`를 제어하는 데 사용된다. (기본값: 16384)
  
  --message-send-max-retries <Integer>  
    메시지가 전달되지 않은 경우 프로듀서가 포기하고 해당 메시지를 삭제하기 전에 재시도할 횟수를 지정한다. 
    이 옵션은 프로듀서 구성에서 `retries`를 제어하는 데 사용된다. (기본값: 3)
  
  --metadata-expiry-ms <Long: metadata expiration interval>  
    리더십 변경이 없더라도 메타데이터를 강제로 새로 고침할 시간 간격 (밀리초). 
    이 옵션은 프로듀서 구성에서 `metadata.max.age.ms`를 제어하는 데 사용된다. (기본값: 300000)
  
  --producer-property <String: producer_prop>  
    사용자 정의 속성을 프로듀서에 전달하는 메커니즘으로, key=value 형식으로 사용한다.
  
  --producer.config <String: config file>  
    프로듀서 구성 속성 파일. [producer-property]가 이 구성보다 우선한다.
  
  --property <String: prop>  
    사용자 정의 속성을 메시지 리더에게 전달하는 메커니즘으로, key=value 형식으로 사용한다.
  
  --reader-config <String: config file>  
    메시지 리더의 구성 속성 파일. [property]가 이 구성보다 우선한다.
  
  --request-required-acks <String: request required acks>  
    프로듀서 요청의 필수 'acks'. (기본값: -1)
  
  --request-timeout-ms <Integer: request timeout ms>  
    프로듀서 요청의 ack 타임아웃. 양수 및 0이 아닌 값을 가져야 한다. (기본값: 1500)
  
  --retry-backoff-ms <Long>  
    각 재시도 전에 프로듀서가 관련 주제의 메타데이터를 새로 고친다. 
    리더 선출에는 약간의 시간이 걸리므로 이 속성은 메타데이터를 새로 고치기 전에 프로듀서가 대기하는 시간을 지정한다. 
    이 옵션은 프로듀서 구성에서 `retry.backoff.ms`를 제어하는 데 사용된다. (기본값: 100)
  
  --socket-buffer-size <Integer: size>  
    tcp RECV 크기. 이 옵션은 프로듀서 구성에서 `send.buffer.bytes`를 제어하는 데 사용된다. (기본값: 102400)
  
  --sync  
    메시지 전송 요청을 동기적으로 보내면, 도착하는 대로 한 번에 하나씩 동기적으로 전송된다.
  
  --timeout <Long: timeout_ms>  
    비동기 모드에서 프로듀서가 메시지를 큐에 넣어 대기할 최대 시간을 지정한다. 밀리초 단위로 지정된다.
    이 옵션은 프로듀서 구성에서 `linger.ms`를 제어하는 데 사용된다. (기본값: 1000)
  
  --topic <String: topic>  
    REQUIRED: 메시지를 생성할 토픽 ID.
  
  --version  
    Kafka 버전을 표시한다.


