# Launch Our First EC2 Instance

## Exam tips

- Termination Protection은 기본적으로 꺼져있으므로 수동으로 켜줘야한다.
- EBS-backed 인스턴스가 종료될 때, 루트 EBS 볼륨이 삭제되도록 되어있다. 따라서 root volume만 삭제되고 다른 나머지 볼륨들은 삭제되지 않는다.
- Default AMI의 EBS 루트 볼륨은 암호화할 수 있다. 서드 파티 제품을 사용하거나, console로 접근하거나, API를 사용해서 암호화하면 된다.
- 추가적인 볼륨들도 암호화할 수 있다.
