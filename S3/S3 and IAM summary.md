# S3 and IAM Summary

# IAM

- Users
- Groups
- Roles
- Policies
  
- 정책은 JSON 형태
- universal
- 루트 계정은 어드민 엑세스 권한이 있음
- 새로운 유저를 생성할 경우, 권한이 없으므로 추가해줘야함
- 유저 처음 생성 시, access key id, secret access keys가 할당됨, 패스워드랑 다르고 커멘드 라인이나 API로만 접근 가능 ( 한 번만 조회 가능)
- MFA 설정하기
- 직접 비밀번호 변경 가능

# S3

- 객체 기반
- 파일 사이즈: 0 Byte ~ 5TB
- 무한 스토리지
- Bucket에 파일이 저장된다
- universal namespace
- ex) https://s3-eu-west-1.amazonaws.com/acloudguru
- 데이터베이스나 os를 설치하기엔 적합하지 않음
- 성공적으로 업로드 시 200 응답코드 반환
- 새로 생성된 버킷은 전부 Private
  - `Bucket Policies`, `Access Control Lists`로 버킷 컨트롤 가능

- Key (Object의 이름)
- Value (데이터)
- Version ID (versioning에 중요)
- Metadata (데이터에 대한 데이터)
- subresources
  - Access Control Lists
  - Torrent
- `PUTS`: Read after write
- `PUTS` `DELETES`: eventual consistency (일관성)

1. S3 Standard
2. S3 - IA: 1번보다 저렴한 요금, S3에 비교적 덜 접근하는 경우
3. S3 One Zone -IA: availiability zone이 하나라서 더욱더 저렴
4. S3 - Intelligent Tiering: 얼마나 자주 사용하는지에 따라 데이터를 자동으로 옮겨준다. (ML사용)
5. S3 Glacier: 회수 시간이 몇 분에서 몇 시간으로 늘어남
6. S3 Glacier Deep Archive: 회수 시간이 12시간임 / 제일 저렴

- SSL/TLS
- Encryption At Rest is archived by
  1. S3 Managed Keys - SSE - S3
  2. AWS Key Management Service, Managed keys - SSE - KMS
  3. Server Side Encryption With Customer Provided Keys - SSE - C
- Client Side Encryption

- 루트 계정에 MFA 활성화하기
- 루트 계정 비밀번호 잘 설정하기
- 결제 계정은 오직 결제만
- Service Control Policies로 AWS 서비스 활성/비활성화 하기

계정 간 S3 버킷 공유
- 버킷 정책 & IAM 사용 (programmatic access only)
- 버킷 ACLs & IAM  (programmatic access only)
- Cross-acount IAM Roles (Programmatic & Console)

Cross Region Replication
- source, destination 전부 활성화 시켜야함
- 버킷의 파일들은 자동으로 복제되지 않음
- 후속 업데이트 파일들은 자동으로 복제된다.
- delete markers는 복제되지 않음
- delete individual versions / delete markers는 복제되지 않음
- Cross Region Replication 이해하기

Lifecycle Policies
- 다른 스토리지 티어들간에 object 움직이는 것 자동화하기
- versioning을 통해 결합
- 현재, 이전 버전에 적용됨

유저들은 각 Edge location에 파일을 업로드하고, 이것들이 S3 bucket으로 업로드된다. `S3 Transfer Acceleration`을 사용하면 속도를 빠르게 할 수 있다.

# Cloud Front

- Edge Location
  - 컨텐츠가 캐시되는 장소
  - AWS Region / AZ과는 다른 것
  - read, write 가능
- Origin
  - CDN이 나뉘는 모든 곳의 근원
  - S3 버킷, EC2 인스턴스, ELB, Route 53 ... 이 될 수 있다.
- Distribution
  - Edge Location의 컬렉션을 포함하고 있는 CDN에게 부여되는 이름
- Web Distribution
  - 웹사이트용
- RTMP
  - 미디어 스트리밍용

# Snowball

- Import to S3, Export From S3

# Storage Gateway

- File Gateway: flat file용, s3에 직접 저장
- Volume Gateway
  - Stored Volumes: 전체 데이터가 사이트에 저장되고 S3에 asynchronous하게 백업된다.
  - Cached Volumes: 전체 데이터가 S3에 저장되고 자주 엑세스되는 데이터들만 사이트에 캐시된다.
- Gateway Virtual Tape Library
  - backup 애플리케이션에 자주 사용됨

# Athena

- SQL 쿼리 실행하기 위함
- interactive query service
- SQL 사용해서 S3에 위치한 데이터를 쿼리할 수 있도록 도와줌
- Serverless
- S3에 저장된 log data 분석에 사용

# Macie

- PII를 위한 보안 서비스
- S3의 데이터 분석하기 위해 AI 사용, PII 알아내기 위함
- CloudTrail logs로 수상한 API 활동 감지
- Dashbaords, Reports, Alerting
- PCI-DSS compliance

