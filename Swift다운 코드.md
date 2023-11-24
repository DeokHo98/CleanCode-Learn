# Swift 다운 코드
## 좋은 코드의 특징
- 잘 작동한다.    
- 읽기 쉽다.    
- 테스트 가능하다.    
- 관리가 쉽다.     
- 외관이 보기 좋다.    
- 변경이 쉽다.     
- 간결하다.   
- 효율적이다.    

## 스위프트를 잘 활용하는 방법
- extension.     
     
```
Bad case

a.lastCharacter("abcd")

static func lastCharacter(_ of: String) -> Character {
    return of.last ?? Character("")
}

GoodCase

"abcd".lastCharacter() 

extension String {
    func lastCharacter() -> Character {
        return self.last ?? Character("")
    }
}
```
    
- 연산 프로퍼티.     
필요한 경우 매게변수 없는 메서드같은경우는 연산 프로퍼티로 구현 할 수있다.       

```
BadCase
"abcd".lastCharacter() 

extension String {
    func lastCharacter() -> Character {
        return self.last ?? Character("")
    }
}

GoodCase
"abcd".lastCharacter

extension String {
    var lastCharacter: Character {
        return self.last ?? Character("")
    }
}
```
     
- 사용자 정의 연산자.   
```
postfix operator ~~

extension String {
    static postfix func ~~ (string: Self) -> Character {
        return string.last ?? Character("")
    }
}

"abcd"~~    
```
    
- 다양한 클로저 표현 방법.   
 후행클로져, 반환타입 생략, 단축인자이름, 암시적 반환표현 등등.   
      
- 옵셔널
옵셔널 사용에서 ! 사용은 절대 금지, 테스트코드나, IBOutlet 같은 특수상황이 아니고서는 절대 금지.     
    
- 빠른 종료 guard
guard문은 if문에 비해 추가로 가지는 의미가 있다.    
gurad는 조건을 충족하지 못하면 흐름이 그대로 중지되는데.   
정말 필요한 확인을 위해서는 if 보다는 guard 구문을 사용하는것이 좋다.     
```
Bad Case

func split(string: String, with token: Character) -> [String] {
  if token.isEmpty {
    return []
  }
  // ...
}

Good Case

func split(string: String, with token: Character) -> [String] {
  guard token.isEmpty == false else {
    return []
  }
  // ...
}

```
