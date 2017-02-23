#Class : 설계, 정의

    class 클래스명 {
      멤버변수;
      생성자(매개변수, ...) {
        초기화;
      }
      method(매개변수, ...) {
        실행문;
      }
    }

#객체 : 그 설계에 맞게 만들어진 실체

##객체를 생성

    클래스명 레퍼런스변수명 = new 생성자(매개변수, ...);

레퍼런스변수명 : 객체이름

##객체 사용

    레퍼런스변수명.멤버변수;
    레퍼런스변수명.method(매개변수, ...);

-----------------------------

#정보은닉 Information Hidden (캡슐화 Encapsulation)
**객체지향 프로그래밍(OOP, Object-Oriented Programing)의 특징 1.**

##private
아무나 접근하면 안되는 멤버변수, 메소드는 **접근지정자** 를 private으로 지정!

private으로 지정된 멤버변수나 메소드는 접근 불가능하기 때문에 setter나 getter를 통해 접근 가능해진다.

##setter method

    public void set멤버변수(멤버변수와 같은 타입의 매개변수) {
      this.멤버변수 = 매개변수;
    }

*this* 는 매개변수와 멤버변수의 이름이 같을 때 구분하기 위해 사용한다. 이 객체의 멤버변수라고 구분하기 위해 사용한다.

예를 들어,

    class A {
      private int age;
      public void setAge(int a) {
        age = a;
      }
    }

이렇게 매개변수와 멤버변수의 이름이 다르다면 문제 없지만, 매개변수의 이름이 age라면 구분할 수 없다.
그렇기 때문에 아래처럼 *this* 를 사용해준다.

    class A {
      private int age;
      public void setAge(int age) {
        this.age = age;
      }
    }

##getter method

    public 멤버변수타입 get멤버변수() {
      return 멤버변수;
    }

예를 들면,

    class A {
      private int age;
      public int getAge() {
        return age;
      }
    }

----------------------------------

#상속 Inheritance (일반화 Generalization)
**객체지향 프로그래밍(OOP, Object-Oriented Programing)의 특징 2.**

- 부모클래스의 멤버변수나 메소드를 자식클래스것으로 사용.
- private은 상속 안 됨.
- 부모부터 생성한 후에 자식 생성. 생성자는 상속되는게 아니다. 부모없는 자식 없다.
- *extends*

##super
멤버변수나 메소드가 부모와 이름이 같은 경우.

    super.멤버변수;
    super.method();

부모 것을 내 것처럼 쓰니까 구분하기 위해서 super를 붙여주면 부모의 것을 말한다.

##override

    class A1 {
      int a2;
      void a1() {...}
    }
    class A2 extends A1 {
      int a2;
      @override
      void a1() {...}
      void a3() {...}
    }
    class Ex {
      public static void main(String[] args) {
        A1 a = new A2(); //부모 선언, 자식 생성(up-casting)
        a.a2; //부모 A1의 a2
        a.a1(); //자식 A2의 a1() 호출
        //a.a3(); //실행안됨. 왜냐면 A1에 a3()가 없으니까.
      }
    }


-----------------------------

#다형성 (Polymorphism)
**객체지향 프로그래밍(OOP, Object-Oriented Programing)의 특징 3.**

    interface Shape {
      void draw();
    }
    class Triangle implements Shape {
      @override
      void draw() {
        System.out.println("삼각형 그린다.")
      }
    }
    class Circle implements Shape {
      @override
      void draw() {
        System.out.println("원 그린다.")
      }
    }
    class Rectangle implements Shape {
      @override
      void draw() {
        System.out.println("사각형 그린다.")
      }
    }
    class Ex {
      public static void main(String[] args) {
        Shape[] sh = {new Triangle(), new Circle(), new Rectangle()};

        for(int i = 0; i < sh.length; i++) {
          sh[i].draw();
        }
      }
    }

interface나 override를 이용해 구현한다.
