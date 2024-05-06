## 애플리케이션의 점진적 배포

### 정의
- 특정 기간 동안 일정 비율의 사용자에게만 새로운 버전의 업데이트를 제공하는 기능
- 업데이트가 모든 사용자에게 동시에 제공되지 않고 랜덤으로 선정된 일부 사용자에게 우선 적용됨
- 이후 일정 기간이 지나면 점진적으로 전체 이용자에게 업데이트 배포
- 만약 점진적 배포 기능을 설정하지 않으면, 모든 유저가 업데이트가 가능해짐<br><br>

### 장점
- 새로운 버전에 치명적인 버그나 오류가 발생할 경우, 일부 사용자에게만 업데이트를 제공하여 전체 이용자에게 영향을 최소화할 수 있음
- 문제 발생 시 신속 대응이 가능<br><br>

### 구글 스토어 vs 앱 스토어
구글 스토어와 앱스토어는 각각 단계적 출시(Staged Rollout)와 점진적 출시(Phased Releases)라는 용어로 점진적 배포를 구현하고 있음<br>

**구글 플레이 스토어(단계적 출시; Staged Rollout)**<br>
애플리케이션의 새로운 버전이 **출시된 후 7일 동안**, 점진적으로 자동 업데이트가 활성화된 사용자 중 일정한 비율의 사용자에게만 업데이트가 제공됨<br>
- [Andriod의 단계적 출시](https://support.google.com/googleplay/android-developer/answer/6346149?hl=ko#zippy=)<br><br>

**앱스토어(점진적 출시; Phased Releases)**<br>
새로운 버전의 애플리케이션이 출시된 후 **일정 기간 동안, 일정 비율**의 사용자에게 점진적으로 업데이트가 배포되며, 이 기간은 개발자가 정함<br>

- [iOS의 점진적 출시](https://developer.apple.com/kr/help/app-store-connect/update-your-app/release-a-version-update-in-phases/)
