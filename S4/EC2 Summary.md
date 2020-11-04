# Summary

## EC2 (Elastic Compute Cloud)

- 클라우드내에서 computer capacity의 사이즈를 조정할 수 있는 웹서비스
- 새로운 서버 인스턴스를 얻고 실행하는 시간을 몇 분으로 줄일 수 있다
- 컴퓨팅 요구사항이 변경될 때마다 스케일 업 다운 할 수 있다
- 4개의 요금제 모델
  - 1. on-demand: 정해진 금액대로 시간 당 측정
  - 2. reserved: 1년/3년의 기간동안 계약을 하고 사용함, 더 길게 계약할 수록 할인율 증가
  - 3. spot: 비딩 시스템, 직접 원하는 금액을 적는 것
  - 4. dedicated hosts: 물리적 EC2 서버를 유저에게 할당, 금액적인 부분이 매력적

- spot instance가 ec2에 의해서 중단되었을 경우 돈 지불할 필요 없지만, 직접 종료시켰을 경우엔 인스턴스가 실행된 시간만큼 돈을 지불해야한다.

## EBS

- 클라우드 안의 가상 하드디스크 드라이브
- termination protection은 기본적으로 꺼져있으므로 켜야한다.
- EBS-backed 인스턴스, 인스턴스가 종료되었을 때, 루트 EBS 볼륨을 삭제하는 것이 기본 액션
- EBS 루트 볼륨의 default AMI는 암호화할 수 있다. (서드파티 사용 혹은 CLI나 콘솔로 접속)
- 추가적인 볼륨들도 암호화 할 수 있다

## Security Groups

- 인바운드 트래픽은 기본적으로 블락되어있다
- 아웃바운드 트래픽은 허용
- Security Group 변경 시 바로 적용
- EC2인스턴스에 여러개의 security group 붙일 수 있다

- STATEFUL (80번 포트 열면, 인바운드 아웃바운드 전부 열린다)
- Network ACL은 stateless (인바운드, 아웃바운드 전부 열어야함)
- 특정 아이피 주소를 차단하려면 Secuirty group이 아닌 Network Access Control List를 사용해라
- rule을 작성할 때에는 allow 명세 가능, deny 명세 불가능

- SSD
  - General Purpose SSD
  - Provisioned IOPS SSD
- HDD
  - Throughput Optimized HDD
  - Cold HDD
  - EBS Magnetic

## EBS Sanpshots

- 볼륨은 EBS에 존재, EBS는 하드디스크라고 생각해라
- 스냅샷은 S3에 존재, S3는 디스크 사진이라고 생각해라
- 스냅샷은 볼륨의 각 시간을 복사한 시점과도 같다
- 스냅샷은 증분가능하다. 마지막 스냅샷 이후의 바뀐 블록만 S3로 이동된다.
- 첫 스냅샷은 시간이 좀 걸린다.
- 루트 디바이스의 역할을 하는 EBS 볼륨의 스냅샷을 찍으려면 인스턴스를 멈춰야한다.
- 볼륨과 스냅샷에서 AMI를 생성할 수 있다.
- 사이즈와 스토리지 타입을 바꾸는 것과 함께 즉석에서 EBS 볼륨 사이즈를 바꿀 수 있다.
- EC2인스턴스와 동일한 availability zone에 볼륨이 존재한다.

## Migrating EBS

- [AZ 변경] 스냅샷 생성 -> 스냅샷으로부터 AMI 생성 -> EC2인스턴스를 새로운 AZ에서 실행하기 위해 AMI 사용
- [리전 변경] 스냅샷 생성 -> 스냅샷으로부터 AMI 생성 -> 다른 리전으로 AMI 복사 -> 복사된 AMI를 새로운 리전, 새로운 EC2인스턴스에서 실행

## EBS Encryption

- 암호화된 볼륨의 스냅샷은 자동으로 암호화된다.
- 스냅샷은 암호화되지 않은 것만 공유 가능
- 다른 AWS 계정과 공유할 수 있거나 퍼블릭으로 만들 수 있다.
- 암호화된 스냅샷으로부터 복구된 볼륨은 자동으로 암호화된다.

## Enhanced Networking

ENI Elastic Network Interface

- 기본적인 네트워킹에 사용
- 프로덕션과 로깅 네트워크를 분리하면서 낮은 비용으로 사용하고 싶을 때
- 여러개의 ENI를 각 네트워크에서 사용해라

Enhanced Network

- 속도: 10Gbps ~ 100Gbps 사이
- high, reliable throughput

Elastic Fabric Adaptor

- OS by-pass, Machine Learning, HPC에서 사용

## CloudWatch

- 퍼포먼스 모니터링
- 대부분의 AWS 서비스 모니터링할 수 있다
- EC2 CloudWatch는 5분에 한 번씩 / detailed monitoring으로 1분간격으로 설정
- 퍼포먼스에 관한 것
- 대시보드 생성해서 AWS 환경에서 일어나는 일들을 확인
- 일정 분계점 이상 넘어가면 노티해주는 알람 
- AWS 리소스의 상태가 변경되는 것에 대해 반응할 수 있도록 함
- 로그를 aggerate, monitor, store할 수 있도록 도와줌

## CloudTrail

- API호출

## CLI

- 어디서든 접속 가능
- IAM에서 설정해주어야함

## Roles

- 엑세스 키, 비밀 엑세스 키로 인스턴스에 접근하는 것보다 Role이 더 편하고 쉽다
- 콘솔과 커맨드라인으로부터 생성된 이후에 EC2인스턴스에 할당할 수 있다.
- 어느 리전에서든 사용할 수 있다. universal

## Metadata & Userdata

- 169.254.169.254/latest/user-data
- 169.254.169.254/latest/meta-data

## EFS

- Network File System version 4 protocol
- 쓴 만큼 지불
- 페타바이트만큼 스케일업가능
- 동시 NFS 연결의 수 천개 지원
- 데이터는 하나의 region에 다수의 AZ에 저장된다.
- Read After Write

## EFS

- highly resilient storage for Linux instances, Linux based application

## Amazon FSx for Windows

- 윈도우 기반 애플리케이션의 중앙화된 스토리지가 필요할 때

## Amazon FSx for Lustre

- hight spped, high-capacity 
- 금융 모델링, HPC 
- S3에 직접 데이터 등록

## Placement Groups

- Clustered Placement Group
  - Low Network Latency / High network Throughput
- Spread Placement Group
  - Individual Critical EC2 instances
- Partitioned
  - Multiple EC2 instances HDFS, HBase, Cassandra

- clustered placement group은 여러 Availability Zone으로 확장할 수 없음
- spread placement랑 partitioned group은 가능(대신 같은 리전에 있어야 함)
- placement group에 명시한 이름은 uniq해야한다
- 일부의 타입 인스턴스들만 placement group에 설치될 수 있음 (Computed Optimized, GPU, Memory Optimized, Storage Optimized)
- placement group을 합칠 수는 없다
- 현재 존재하는 existing instance를 placement group으로 옮길 수 있다. 대신 옮길 때, 인스턴스는 멈춰있는 상태여야한다. AWS CLI나 SDK를 사용해서 인스턴스를 옮기거나 삭제해야하고, 아직까진 콘솔로 불가하다

## AWS WAF

- [WAF] block malicious IP address , block specific countries, cross-site scripting, SQL injections