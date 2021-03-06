## Type Casting

JavaScript는 Weak Typing 언어이기 때문에 필요할 때마다 알아서 타입을 변환한다.

    // 다음은 모두 true
    new Number(10) == 10; // Number.toString()이 호출되고 
                          // 다시 Number로 변환된다.

    10 == '10';           // 스트링은 Number로 변환된다.
    10 == '+10 ';         // 이상한 스트링
    10 == '010';          // 엉뚱한 스트링
    isNaN(null) == false; // null은 NaN이 아녀서 0으로 변환된다.

    // 다음은 모두 false
    10 == 010;
    10 == '-10';

> **ES5 Note:** `0`으로 시작하는 숫자 리터럴은 8진수다. 하지만, ECMAScript 5의 strict 모드에서는 더는 8진수로 해석하지 않는다.

이런 문제들은 [strict equal operator](#types.equality)로 **미리 방지해야** 한다. 이 operator로 JavaScript의 많은 결점을 보완할 수 있지만, 아직도 weak typing 시스템 때문에 생기는 문제가 많다.

### 기본 타입 생성자

`Number`나 `String` 같은 기본 타입들의 생성자는 `new` 키워드가 있을 때와 없을 때 다르게 동작한다.

    new Number(10) === 10;     // False, Object와 Number
    Number(10) === 10;         // True, Number와 Number
    new Number(10) + 0 === 10; // True, 타입을 자동으로 변환해주기 때문에 

`new` 키워드와 함께 `Number` 같은 기본 타입의 생성자를 호출하면 객체를 생성하지만 `new` 없이 호출하면 형 변환만 시킨다.

그리고 객체가 아니라 단순히 값이나 리터럴을 사용하면 타입 변환이 더 많이 일어난다.

가능한 정확하게 타입을 변환해주는 것이 최선이다.

### 스트링으로 변환하기

    '' + 10 === '10'; // true

숫자를 빈 스트링과 더하면 쉽게 스트링으로 변환할 수 있다.

### 숫자로 변환하기

    +'10' === 10; // true

`+` 연산자만 앞에 붙여주면 스트링을 쉽게 숫자로 변환할 수 있다.

### Boolean으로 변환하기

'!' 연산자를 두 번 사용하면 쉽게 Boolean으로 변환할 수 있다.

    !!'foo';   // true
    !!'';      // false
    !!'0';     // true
    !!'1';     // true
    !!'-1'     // true
    !!{};      // true
    !!true;    // true
