# S3 Object Lock and Glacier Vault Lock [SAA-C02]

## Exam tips

- WORM model(write once read many):  S3 Object Lock 사용
- Individual object || applied across the bucket
- Governance mode
  - 권한이 없으면 overwrite, delete 불가 / 잠금 설정 변경 불가
- Compliance mode
  - 루트 권한 사용자도 overwrite, delete 할 수 없음
- S3 Glacier Vault Lock
  - WORM 같이 컨트롤을 세분화할 수 있음
  - 한 번 정책을 잠글 경우, 바꿀 수 없음