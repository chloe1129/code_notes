# Library

> itertools.combinations(array, 뽑을 숫자)

    조합 라이브러리, 순서와 상관 없게

> itertools.permutations

    순열 라이브러리, 순서와 상관 있게

# Function

> abs(number)

    절댓값 함수

> bin(), oct(), hex()

    각각 정수를 2진수, 8진수, 16진수 문자열로 변환

> chr()

    정수를 받아서 Unicode 코드 포인트가 일치하는 문자를 반환

> ord()

    문자를 받아서 Unicode 코드 포인트를 반환

> enumerate()

    iterable(루프 가능) 개체를 개체의 위치 번호 및 요소의 iterable(루프 지원) 객체로 변환

> format()

    첫 번째 인수의 문자열을 두 번째 인수의 템플릿으로 포맷 된 문자열을 반환

> reversed()

    요소를 역순으로 추출

> round()

    round(123.456,1) -> 123.5
    두 번째 인수의 자리에서 반올림

> zip()

    여러 개의 iterable 자료형이 개수가 동일할 때 사용, 각각의 요소를 나눈 후 순서대로 묶어서 요소 개수 만큼 새로운 iterable 자료형을 생성 (iterable 자료형이란 리스트, 튜플 등)

> replace()

    변수.replace(old, new, [count])
    old : 현재 문자열에서 변경하고 싶은 문자
    new : 새로 바꿀 문자
    count : 변경할 위치, 입력하지 않으면 전체를 변경

> rjust()

    변수.rjust(전체 자리 숫자, 공백이 있을 경우 공백을 채울 텍스트)
    chloe.rjust(7,'.') : ..chloe
