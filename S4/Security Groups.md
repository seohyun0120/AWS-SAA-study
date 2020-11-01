# Security Groups

## Exam tips

- 인바운드 트래픽은 기본적으로 막혀있다. (security group 들어가서 활성화 필요)
- 아웃바운드 트래픽은 허용된다.
- security group에 반영된 정보는 바로 반영된다.
- security group을 가진 EC2 인스턴스는 여러 개일 수 있다.
- EC2인스턴스에 여러 개의 security group을 붙일 수 있다. (1:1 관계 아님)(하나의 security group에 여러 EC2 인스턴스 가질 수 있음)
(하나의 EC2 인스턴스에 여러 security group 가질 수 있음)
- Security Group은 STATEFUL하다. (inbound 설정하면 outbound이 자동으로 설정되고 vice versa)
- Specifit IP 엑세스를 막을 순 없다. Network Access Control List를 사용해야함
- Rule Allow 가능, Deny 불가능