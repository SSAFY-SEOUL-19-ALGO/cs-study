# ERD(Entity Relation Diagram)의 기본

## ERD(Entity Relationship Diagram)

![Untitled](https://user-images.githubusercontent.com/47595515/211578639-b03a6514-009a-4baf-8bc9-f72b49c92ee0.png)

- 데이터베이스를 구축할 때 가장 기초적인 뼈대 역할
- 엔티티(Entity) 간의 관계(Relationship)들을 정의한 것
- 서비스 구축에 가장 먼저 신경 써야 할 부분
- 시스템의 요구사항을 기반으로 작성
- ERD를 기반으로 데이터베이스를 구축
- 관계

  ![Untitled 1](https://user-images.githubusercontent.com/47595515/211578647-0f5573af-ca57-4776-9195-98a680b81a16.png)
    
- 키

  ![Untitled 2](https://user-images.githubusercontent.com/47595515/211578650-c8ca48d8-105e-4c76-9e94-7b7f2b36df0a.png)
    
    - 기본키(Primary Key) : 유일성과 최소성을 만족
    - 자연키 : 중복되는 것을 제외하고 자연스럽게 뽑아 결정하는 기본키, 언젠가 변함
    - 인조키 : MySQL의 auto increment 등 인조적으로 유일성을 확보하는 키, 기본키는 보통 인조키로 설정
    - 외래키 : 다른 테이블의 기본키를 그대로 참조하는 값
    - 후보키 : 기본키가 될 수 있는 후보들, 유일성과 최소성을 동시에 만족
    - 대체키 : 후보키가 2개 이상일 경우 어느 하나를 기본키로 지정하고 남은 후보키
    - 슈퍼키 : 각 레코드를 유일하게 식별할 수 있는 유일성을 갖춘 키