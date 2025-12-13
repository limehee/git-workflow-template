## 관련 이슈 및 링크
> Closes #이슈번호
> Linear: [Link](...)
> Figma: [Link](...)

## 변경 사항
<!-- 이번 PR에서 작업한 내용을 요약해 주세요. -->
기존 `UserService`의 인증 로직을 `AuthService`로 분리하고, JWT 발급 과정을 리팩토링했습니다.

## 구체적 작업 내용
<!-- 상세 작업 내용을 리스트 형태로 기술해 주세요. -->
- **AuthService 구현**: `login()`, `reissueToken()` 메소드 구현
- **JWT Provider 리팩토링**: Access/Refresh 토큰 생성 로직 분리
- **테스트 코드 추가**: 인증 서비스에 대한 단위 테스트 5종 추가 (`AuthServiceTest`)
- `SecurityConfig` 설정 변경: `/auth/**` 경로 허용

## 검증 방법
<!-- 로컬이나 개발 서버에서 어떻게 검증했는지 작성해 주세요. -->
- [ ] 로컬 환경에서 `/api/v1/auth/login` 호출 시 Access Token 정상 발급 확인
- [ ] 만료된 토큰으로 접근 시 401 Unauthorized 응답 확인
- [ ] `./gradlew test` 실행하여 전체 테스트 통과 확인

## 스크린샷
<!-- UI 변경 사항이나 로그 스크린샷이 있다면 첨부해 주세요. -->

## 특이 사항
<!-- 리뷰어가 참고해야 할 추가적인 정보가 있다면 남겨주세요. -->
이번 변경으로 인해 `application.yml`에 `jwt.secret` 키가 변경되었습니다. 로컬 환경 변수를 업데이트해주세요.
