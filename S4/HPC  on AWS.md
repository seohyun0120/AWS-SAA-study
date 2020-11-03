# HPC on AWS

## Exam tips

- Data transfer
- Compute, networking
- Storage
- Orchestration, automation
위 네 가지로 HPC 달성할 수 있다. 

- Data Transfer
  - Snowball, Snowmobile 사용해서 큰 사이즈의 데이터 옮기기(terabytes/petabyes worth of data)
  - AWS DataSync 사용해서 S3, EFS, FSx for Windows에 데이터 저장 가능
  - Direct Connect 사용

- Compute, Networking
  - GPU나 CPU 최적화된 EC2 인스턴스
  - EC2 Fleets (Spot Instance, Spot Fleets)
  - Placement Groups (cluster placement groups)
  - Enhanced networking single root I/O virtualization (SR-IOV)
  - Elastic Network Adapter, Intel 82599 Virtual Function(VF) interface
  - Elastic Fabric Adapters

- Storage
  - EBS: 64,000 IOPS with Provisioned IOPS
  - Instance Store: millions of IOPS, low latency

- Network Storage
  - Amazon S3: 객체기반 스토리지
  - Amazon EFS: 파일시스템
  - Amazon FSx for Lustre: HPC-optimized distributed file system, millions of IOPS, backed by S3

- Orchestration, Automation
  - AWS Batch
  - AWS ParallelCluster