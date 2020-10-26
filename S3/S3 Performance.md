# S3 Performance

## Exam tips

- prefix 설정
  - mybucketname/folder1/subfolder1/myfile.jpg
- prefix 당
  - 3500 PUT, COPY, POST, DELETE 
  - 5500 GET, HEAD
- 여러 prefix써서 더 좋은 퍼포먼스를 낼 수 있다.

- SSE-KMS를 쓸 경우,KMS limit 알아두기
- 파일 업로드 시, multipart upload 사용하기
- 파일 다운로드 시, s3 byte-range fetches 사용하기
