# AMI Types (EBS vs. Instance Store)

## Exam tips

- Instance Store Volumes는 Ephemeral Storage라고 불리기도 한다. 만약에 멈추게 되면 모든 데이터를 잃기 때문
- Instance Store Volumes은 멈출 수 없다. 기본적인 호스트가 실패하게 될 경우, 데이터를 잃는다.
- EBS backed instance는 멈출 수 있다. 멈추더라도 데이터를 잃지는 않는다.
- 재부팅할 수 있으며, 데이터를 잃지는 않는다.
- 종료될 경우 Root Volume들은 삭제된다. EBS 볼륨은 AWS에게 유지하라고 말할 수 있다.