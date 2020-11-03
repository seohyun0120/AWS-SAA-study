# EC2 Placement Groups

## Exam tips

- clustered placement group은 여러 Availability Zone으로 확장할 수 없음
- spread placement랑 partitioned group은 가능(대신 같은 리전에 있어야 함)
- placement group에 명시한 이름은 uniq해야한다
- 일부의 타입 인스턴스들만 placement group에 설치될 수 있음 (Computed Optimized, GPU, Memory Optimized, Storage Optimized)
- placement group을 합칠 수는 없다
- 현재 존재하는 existing instance를 placement group으로 옮길 수 있다. 대신 옮길 때, 인스턴스는 멈춰있는 상태여야한다. AWS CLI나 SDK를 사용해서 인스턴스를 옮기거나 삭제해야하고, 아직까진 콘솔로 불가하다
