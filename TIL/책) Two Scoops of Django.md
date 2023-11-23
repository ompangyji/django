## 핵심 개념

- 단순 명료하게
단순함의 법칙을 적용하되 바보 같은 가정으로 너무 단순화된 구현을 하지는 않도록 주의하자
- 모델은 크게, 유틸리티는 모듈로, 뷰는 가볍게, 템플릿은 단순하게
뷰와 템플릿을 제외한 다른 부분에 더 많은 로직을 넣는 방법을 추천한다. 템플릿 태그와 필터는 가능한 한 최소의 로직을 포함하고 있어야 한다.
- 시작은 장고 기본 환경으로부터
- 장고의 디자인 철학을 이해하도록 한다.
장고 디자인 철학에 대한 문서를 보면 장고에서 특별한 제약과 도구들을 제공하는 이유를 이해하는 데 큰 도움이 된다.
[[Design philosophies]]
- 12팩터 앱
웹 기반 애플리케이션 디자인의 통합 전략
https://12factor.net/ko/

# 1장 코딩 스타일
## 1.1 읽기 쉬운 코드를 만드는 것이 왜 중요한가
흩어진 퍼즐을 짜 맞추는 작업을 덜 해도 되므로 개발자의 뇌가 덜 피곤해지고, 프로젝트 규모에 상관없이 유지 관리가 쉬워지며, 프로젝트를 개선하기 위한 작업 또한 훨씬 수월해진다.
- 축약적이거나 함축적인 변수명은 피한다.
- 함수 인자의 이름들은 꼭 써준다.
- 클래스와 메서드를 문서화한다.
- 코드에 주석은 꼭 달도록 한다.
- 재사용 가능한 함수 또는 메서드 안에서 반복되는 코드들은 리팩터링을 해둔다.
- 함수와 메서드는 가능한 한 작은 크기를 유지한다. 어림잡아 스크롤 없이 읽을 수 있는 길이가 적합하다.

## 1.2 PEP 8
파이썬 공식 스타일 가이드
https://peps.python.org/pep-0008/
! 현재 프로젝트의 기존 관례를 함부로 바꾸지 않도록 한다.
※ 코드 품질을 위해 flake8을 이용하자

## 1.3 임포트에 대해
다음과 같은 순서로 그룹을 지을 것을 제안한다.
1. 표준 라이브러리 임포트
2. 코어 장고 임포트
3. 장고와 무관한 외부 앱 임포트
4. 프로젝트 앱 임포트
```python
# Stdlib imports
from math import sqrt
from os.path import abspath

# Core Django imports
from django.db import models
from django.utils.translation import gettext_lazy as _

# Third-party app imports
from django_extensions.db.models import TimeStampedModel

# Imports from your apps
from splits.models import BananaSplit
```

## 1.4 명시적 성격의 상대 임포트 이용하기
모듈의 패키지를 하드 코딩하거나 구조적으로 종속된 모듈을 어렵게 분리해야하는 경우들을 피할 수 있다.
```python
# 나쁜 예제

```
문제 없이 작동하지만 하드 코딩된 임포트 문들은 이식성 면에서나 재사용성 면에서 문제가 된다.

##
