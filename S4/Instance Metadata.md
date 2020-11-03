# Instance Metadata

## Exam tips

- 인스턴스의 정보를 얻고자할 때 사용 (ex) public ip
- `curl http://169.254.169.254/latest/meta-data`로 메타 데이터 얻을 수 있음
- `curl http://169.254.169.254/latest/user-data`로 유저 데이터 얻을 수 있음