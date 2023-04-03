  ## React 모르는 부분 요약

1. this.state는 this.setState()를 통해 업데이트 할 수 있는 컴포넌트의 상태를 나타낸다.

2. ```
   const { characters } = this.state
   ``` 
   에서 { }의 의미는 
   ```
   const characters = this.state.characters   
   ```
   를 축약하기 위해 {}를 사용한다. {}을 세부적으로 설명하자면 개체에서 값을 추출하고더 짧은 이름을 가진 변수에 할당할 수 있는 구조 분해 할당이다.
    ```
    const { characterData , removeCharacter} = props;
    ``` 
    위 코드는 아래 코드와 같다
    
    ```
    const characterData = props.characterData ; 
    const removeCharacter = props.removeCharacter; 
    ```

3.
    ```
    this.setState({
     characters: characters.filter((character, i )=> {
      return i !== index
    }),
    ```     
     에서  ```characters: character```는 배열을 key로 돌려 주어진 인덱스에서 항목을 제거하여 문자 배열을 필터링하고 새 배을 반환하는 코드이다. 
     
4.
    ```
    this.setState({ characters: [...this.state.characters, character] })
    ```
    는 스프레드 연산자 ...을 통해 기존 character 배열의 복사본을 만든다음, character를 넣어 생성한다.


5.  this.state는 현재 컴포넌트의 state를 참조하고 this.props는 부모의 컴포넌트에서 전달받은 속성를 참조한다.

6.
    화살표 함수를 사용하는 이유는 이벤트 핸들러가 컴포넌트 인스턴스에 자동으로 바인딩 되기 때문이다. 
    하지만 만약 일반 함수를 사용할 경우 수동으로 bind()를 통해 바인딩 해야한다. 
    ```
    handleSubmit = (character) => {
      this.setState({ characters: [...this.state.characters, character] })
    }
    ```
    위 코드를 일반 함수로 나타 내면 아래와 같다
    ```
    function handleSubmit(character) {
      this.setState({ characters: [...this.state.characters, character] })
    }
    
    this.handleSubmit = handleSubmit.bind(this);
    ```
    즉 화살표 함수는 코드의 간결함과 수동 바인딩을 하지 않기 위해 주로 사용한다.

7.
    React에서는 클래스 컴포넌트를 정의할 때 자식 클래스의 생성자에서 super(props)를 사용하여 부모 클래스의 생성자를 호출해야 한다.
    이는 자식 구성 요소가 부모 클래스의 동작과 속성을 상속하고 부모 클래스가 자식 구성 요소를 초기화하기 전에 몇 가지 설정을 수행해야 할 수 있기 때문에 필요하다.
