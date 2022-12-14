# 스토리지 엔진

## InnoDB(mysql 5.5 default)

- **트랜잭션 지원**
- Row Level Lock 지원

### MyISAM

- **트랜잭션 지원X**

- **Read only** 기능이 많은 서비스일수록 **효율적**
    - 항상 테이블에 LOW COUNT 존재
- Table Level Lock 지원

### wiredtiger(mongoDB 3.2 default)

- 로그 기반 병합트리를 이용하여 읽기 성능 포기하고 저장 성능 향상
- 느린 읽기 성능을 보안하기 위해 블룸 필터를 사용

**체크포인트**

- MongoDB는 60초 간격으로 체크포인트를 생성
- 종료되거나 새로운 체크포인트를 작성중 오류 발생시, 마지막 유효한 체크포인트에서 복구 가능

**저널링**

- 체크포인트 간의 모든 데이터 수정 사항 유지
- MongoDB가 종료시 저널을 사용하여 마지막 체크포인트 이후 수정된 모든 데이터 재생산

**압축**

- MongoDB는 모든 컬렉션 및 인덱스에 대한 압축 지원

**메모리**

- **약 50%**의 메모리를 차지
    - (메모리 크기 - 1GB) /2