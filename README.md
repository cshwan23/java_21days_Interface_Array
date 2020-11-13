# java_21days_Interface
인터페이스 코딩

#인터페이스



package com.fff.erp;

//import com.yyy.erp.Animal;
//import com.yyy.erp.Elephant;
//import com.yyy.erp.Lion;

// [Speed] 인터페이스 선언 

interface Speed{
	
	//속성변수 선언 
	public int startSpeed = 10;
// public, final 빼도 들어가있다 무조건 갖고있다 이점 명심 
	
	//추상메소드 선언 
	public void speedUp(); //{}생략 
	public void speedDown();
	//바디없는메소드인에 왜 abstract 가 없죠? (있다니까 생략해도 다 들어가 있는거래니까인터페이스특징자체가넣어주니까.)
	//객체화를 시켜서 오버라이딩을 시켜야함.
	//오버라이딩 
	//슈퍼클래스의 메소드를 내 영역안에 갖고오는것
	// 이름이 같은 메소드 // 접근지정자 같거나크다 // 매개변수 갯수 같고// 매개변수 자료형 같고//리턴형같고 
}


//어떤 의무가 있나? 재정의가. 바디없는메소드는 car 클래스는 재정의를 하러 들어가야함
//->재정의를 안하면 추상클래스가 된다. 객체화가 안되니까 재정의를 해야 그래야 구현이 되니까. 
//인터페이스를 구현받았다? 빨리 1. 스피드의 메소드를 오버라이딩 해야겠구나. 2. 오버라이딩 규칙대로 따라줘야겠구나 - 표어
//인터페이스 = 오버라이딩 그래야 1. 객체화를 시키고 그래야 2. 메소드를 호출하지..
//***************************************
//*[Speed 인터페이스] 를 구현받은 [Car 클래스]선언 
//***************************************
	class Car implements Speed{
	
	//* 속성변수 선언 
	int nowSpeed = startSpeed;  //(상속처럼 그냥 갖다 쓰는구나 인터페이스도 상속개념)
	
	//오버라이딩을 꼭해야하는 이유 => 객체화를 해야하므로 -> 객체화를 해야 메소드를 호출이 가능하므로.
	//반드시 오버라이딩을 해야하는건 아니다. 에러만 난나고 객체화가 안될뿐. 추상클래스가 될뿐 
	
	//*[오버라이딩 메소드] 선언
	public void speedUp() {
		nowSpeed++;
	} // 이 speedUp 메소드를 주석처리 시키면 Car 클래스에서 에러가 난다. 인터페이스의 메소드를 다 재정의하지않아서 
	// 부모쪽 바디없는 메소드가 있어서 abstract를 붙여야 한다.  
	
	//*[오버라이딩 메소드] 선언

	public void speedDown() {
		nowSpeed--;
	}
	
//	오버라이딩 다했겟다. [고유메소드] 하나 만들자.
	//*[고유 메소드] 선언
	public int getSpeed() {
		return nowSpeed;
	}
	
	
}





//*******************************************************
//*[CarExe 클래스]를 객체화하고 메소드 호출하는 [CarExe 클래스] 선언  
//*******************************************************
public class CarExe {

	public static void main(String[] args) {

		//*******************************************************
		// <1> 객참변수 car 선언
		// <2> 생성자 Car() 를 소유한 Car 클래스를 찾아 메모리에 올려 객체화
		// <3> 메모리에 올려진 Car 클래스의 생성자 Car() 호출
		// <4> 객체의 메모리 위치 주소값을 리턴하여 변수 car에 저장 
		//*******************************************************
		Car car = new Car();
		
		//*******************************************************
		// Car 객체의 메소드 호출 
		//*******************************************************
		car.speedUp();
		
		System.out.println(car.getSpeed());
		car.speedDown();
		car.speedDown();
		System.out.println(car.getSpeed());
		
		System.out.println(Speed.startSpeed);
//		인터페이스에서 속서변수는 호출가능 / 메서드는호출불가능
//		인터페이스명.속성변수로 호출가능
		
		
	}

}
/*


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문1>	int nowSpeed = startSpeed;를
		int nowSpeed = ++startSpeed;로 수정하면?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
=> 에러발생. 컴파일발생.
=> 인터페이스 내부의 속성변수는 final 의 성격을
   가지고 있어 데이터 갱신이 불가능하기 때문
=> car 클래스에서 에러가 발생하여 컴파일 실패한다. 


interface 안의 속셩변수는 절대 못바꿔
interface 성격은 규칙이다.
절대적인 규칙을 선언한 대상이다.
본사 규칙이다.
인터페이스 자체가 규칙을 나열되어이 있는 놈이다. 


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문2>	public int startSpeed = 10;를
		private int startSpeed = 10;로 수정하면?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ



//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

 => 에러발생. 컴파일 실패
 => 인터페이스의 메소드, 속성변수는 무조건 public의 성격이다.
   그러므로 인터페이스 쪽에서 에러가 발생한다. 
   
   
   
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문3>	public void speedUp() {nowSpeed++;} 을
		void speedUp() {nowSpeed++;} 로 수정하면?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ



//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
  => 에러발생, 컴파일 실패
  => 인터페이스의 메소드는 public이 붙든 안붙든
  	 무조건 public 성격을 가지고 있으므로 오버라이딩 규칙을 지켜야함.
  	 오버라이딩 시 접근지정자는 슈퍼클래스(인터페이스)보다 크거나 같아야한다. 
 
<오버라이딩 규칙>
부모 메서드를 자식클래스에서 그대로 가져다 사용.
사용규칙  1. 메소드명 같아야.
        2. 접근지정자 같거나 커야한다.
 		3. 리턴형 같타야한다
 		4. 매개변수 갯수 같아야 한다.
 		5. 매개변수 자료형 같아야 한다. 



//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문4>	만약 public void speedUp(){nowSpeed++}를 생략하면? *******
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
=> 에러발생. 컴파일 실패
=> 인터페이스가 소유한 메소드를 모두 재정의(overriding) 하지 않으면.
   이 클래스도 [추상클래스]가 되므로 car class 앞에 abstract 가 붙어야 합니다.
   
   => [car class 마빡에 abstract 를 붙여서] car class는 추상클래스가 되니 에러는 안나지만
   => 그 밑에 실행 클래스에서 에러가 또 터진다.
   => 객체화가 안되었는데 객체화를 시도하고 있다.  
   		Car car = new Car();에서 에러가...
   => 추상클래스는 객체화가 불가능한데.. 객체화를 시도하는 new 에서 에러가 터진다.



 <인터페이스 관련 문제>
 

//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문5>  아래 문자의 답은?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


public interface Foo{
int k = 4;   //2
}
				   동등한 
Which three are equivalent to line 2? (Choose three.)
A. final int k = 4; 
B. public int k = 4; 
C. static int k = 4; 
D. abstract int k = 4; 
E. volatile int k = 4; 


//정답 a,b,c
 * 
// 인터페이스의 성격은 public / final / static 성격을 가지고 있다. (인터페이스의 정의)
 * abstract는 왜 안돼. 속성변수에 무슨 abstract가 붙어. 

 인터페이스가 소유한 속서변수 앞에 public final static 의 성질 가진다.
 인터페이스가 소유한 추상메소드 앞에 public abstract 의 성질을 가진다.


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문6>  아래 문자의 답은?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

public interface Test {
	int frood = 42;
}
class TestImp implements Test{
}
class Exe{
	public static void main(String[] args){
	System.out.println(Test.frood++);
	}
}

What is the result?
A. 0
B. 1
C. 42
D. 43
E. comilation fails
F. An exception is thrown at runtime.
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

정답 E
interface 속성변수는 없어도 final이다..
절대적인 진리데이터인데 왜 업데이트하냐구,..

인터페이스가 소유한 속변수 앞에 public final static 의 성질 가진다.


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문7>  아래 문자의 답은?
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
public interface Test {
	int frood = 42;
}
class TestImp1 implements Test{
	static int frood;

}
class Exe{
	public static void main(String[] args){
	TestImp1.frood++;
	System.out.println(TestImp1.frood);
	}
}

What is the result?
A. 0
B. 1
C. 42
D. 43
E. comilation fails
F. An exception is thrown at runtime.

//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
Answer : B

TestImp1.frood++;에서 frood;는 TestImp1 class의 frood 다. 인터페이스의 frood가 아니다..


TestImp1 class 의 
static int frood;  앞에 final static int frood; 파이널을 붙이면
에러. 데이터를 고칠수도 없고. 수동초기화를 해야하니까 바로 ; 나오는게 아니라 데이터도 나와야 한다.



//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문8>  아래 문자의 답은?********이해 안됨 어렵다******
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
interface IO{
	public int method1(int x, int y);
	public long method1(long x, long y);
}


Which compiles?
	A. interface II extends IO {}
	B. interface II implements IO {}
	C. abstract class C1 extends IO {
	 		public int method1(int x, int y) {return 0;}
	 	}
	D. abstract class C1 implements IO {
			public int method1(int x, int y) {return 0;}
			public short method1(long x, long y) {return 0;}
			}
	E. class C1 implements IO {
		public int method1(int x, int y) {return 0;}
		public short method1(long x, long y) {return 0;}
		}
			
			
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
			
정답 a 인터페이스 끼리 상속가능. 

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

B는 인터페이스는 인터페이스를 구현할수가 있냐. 인터페이스는 인터페이스를 상속
	인터페이스는 클래스로 구현.. implements를 extends 로 바꿔야한다.

C는 왜안되냐  인터페이스가 상속해주는건 인터페이스 밖에 없다.......
	extends 가 아니라 implements여야하는데 에러.
	
D는 왜 안되냐.  오버로딩 해야하는데 밑에는 리턴형이 달라서 short에서 터진다.
    long으로 고친다고 되냐? 오버라이딩은 됬는데 왜 마빡에 abstract 붙여?
	완벽해도 abstract 붙여도 된다. 왜냐하면 객체화 불가하다고 선언하는거다.
	
E도 오버라이딩에서 short 때문에 안된다.
	
	 
	
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문9>  물음표 자리에 들어가서 에러가 없는 코딩을 1개 골라라. (get 메소드의 분석능력)
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
	
	
interface Animal{ void soundOff();}

class Elephant implements Animal{
	
	public void soundOff() {
		System.out.println("Trumpet");
	}
}
class Lion implements Animal{
	public void soundOff() {
		System.out.println("Roar");
	}
}
class Alpha {
	public static Animal get(int no) {
		if (no==1) {
			return new Lion();
		}else{
			return new Elephant();
		}
	}
}

public class Exe {

	public static void main(String[] args) {
//	???
	}

}


 A. new Animal().soundOff();
 B. Elephant e = new Alpha();
 C. Lion a = Alpha.get(1);
 D. new Alpha().get(2).soundOff();
 
 
 
 
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

정답 D
=> new Animal().soundOff(); 는 인터페이스를 객체화 할 수 없기 때문에 에러 
=> Elephatn e = new Alpha(); => Elephant 와 Alpha는 아무른 관계가 없기 때문에 에러
=> Lion a = Alpha.get(1); =>Alpha.get(1)의 리턴형은 Animal이기 때문에 에러
=> new Alpha().get(2).soundOff() => new Alpha().get(2)의 리턴 자료형은 
=> Animal이므로 오버라이딩한 메소드인 soundOff는 호출 가능하다. 


//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


//   A. new Animal().soundOff();
// 바디가 없어서 객체화 자체가 안된다. 
//
//   B. Elephant e = new Alpha();
// 부모클래스가 엘리펀트면 가능. 
// 엘리펀트가 인터페이스인데 알파한테 구현해주면 돼.
// 
// 슈퍼클래스 객체참조변수 = new 서브클래스명(); 
//
//   C. Lion a = Alpha.get(1);
//
// (1) static이 붙었기 때문에 객체생성 안해도 들어와도 상관없다. 
//
// (2)리턴 되는 경우가 lion 이거나 elephant 인데 자료형이 둘다 달라지니까 
// 어느놈이 객체의 메위주가 될지 모르기 때문에 
// 리턴형 매소드 리턴형을 animal 로 한거다 그러면 
// (3)Lion a = Alpha.get(1)의 자료형이 Lion인데 get 호출하면 자료형은 Animal이다.
// 자료형이 달라서 에러다. Lion이 Animal이 나와야 한다. 

//   D. new Alpha().get(2).soundOff();
   // static이 붙어있으면 객체생성하고 들어가도 되고 안하고 들어가도 된다. 
// 자료형은 animal인데 오버라이딩 되므로 soundOff()가 호출 가능하다. 
//핵심은 get 메서드 - 자료형은 1개밖에 못쓰는데 현재 리턴데이터 유형은 2개이다..
// 대신 get으로 된 것은 interface 기 때문에 고유멤버는 호출이 불가능하다.
//get 메소드 왼쪽에 왜 Animal을 썻냐?****이것만알아도된다.

	
	
//이 메소드의 리턴형은 lion/ element로 바야하지만 Animal 로 봐야한다.
	
	리턴형의 객체메위주가 다르면 인터페이스의 객체메위주의 리턴형을 써버린다.
	
	1. 김치용 2. 야채용 그릇 사와라. 햇으면(리턴형이 두개가 다 따로인데)
	다목적 용 그릇을 사오면 둘다 담을 수 있다. (리턴형 하나로 통일 인터페이스)
	
 */


# java_21days_Array
Array 배열 개념/코딩


#Array 배열


package com.ggg.erp;

public class ArrayTest {

	public static void main(String[] args) {
	
	
	// <1> 배열 객체의 메위주가 저장될 kors 변수 선언.
	// <2> 배열 객체 생성
	// <3> 배열 객체 내부에 int형 변수 5개 선언하고 디폴트 값 0 저장
	//	    이때 배열변수에 접근하는 방법은 
	//		객참변수[Index번호]이다.	
	// <4> 배열 객체의 메위주 리턴하여 kors 변수에 저장.
	int[] kors = new int[5];   // <--배열개수 총 5개를 저장. 
	
	System.out.println(kors[0]);
	// 배열변수에 데이터 저장
	kors[0] = 94;
	//객참변수[0번째] = 데이터저장;
	
	kors[1] = 92;
	kors[2] = 82;
	kors[3] = 76;
	kors[4] = 88;
//	kors[5] = 99; 	// 존재하지 않는 인덱스 번호를 거론하면 코딩상 에러는 안난다. 
					//실행하면 에러가 난다. (runtime error)

	//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
	//총점이 저장되는 지역변수 tot 선언..
	// <주의> 지역변수는 자동 초기화 되지 않으므로 수동 초기화 해야함.
	//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
	int tot = 0;
	tot = tot + kors[0];
	tot = tot + kors[1];
	tot = tot + kors[2];
	tot = tot + kors[3];
	tot = tot + kors[4];
	System.out.println( "[국어 총점]=> " + tot);
	
	tot = 0; 
	
	for(int i = 0; i < 5 ; i++) {
		
		tot = tot + kors[i];
		
	}
	System.out.println( "[국어 총점]=> " + tot);
	
	
	// 문제가 있다. 배열 갯수가 몇천개면..
	tot = 0; 
	
	for(int i = 0; i < kors.length ; i++) {
		
		tot = tot + kors[i];
		
	}
	System.out.println( "[국어 총점]=> " + tot);
	
	// 몇개가 들어오던 자동으로 저장됐으면 좋겠다.
	// 데이터가 들어오기 전에 데이터의 갯수를 알아야지만 배열 객체를 생성하니깐 
	// 외부에서 들어오는 다량의 데이터는 DB 에서 들어오는데
	// 몇갠지 알 수 없어서 정확한 수를 배열에 담을수가 없다. 모를 땐 배열 사용하기 힘들다. 
	
	
	//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
	//  한 줄이 갖는 의미.
	// <1> 배열 객체의 메위주가 저장될 skills 변수 선언.
	// <2> 배열 객체 생성
	// <3> 배열 객체 내부에 String 형 변수 3개를 선언하고 디폴트 값 null 저장
	//	    이때 배열변수에 접근하는 방법은 
	//		객참변수[배열변수의 Index번호]이다.	
	// <4> 배열 객체의 메위주 리턴하여 skills 변수에 저장.
	// [배열]의 변수명은 관용적으로 마지막에 s를 붙인다. 혹은 Arr이 붙는다.(~들, Array, 다량의 데이터)
	//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
	String[] skills = new String[3];

	// 배열 변수에 String 형 데이터 저장.
	skills[0] = "JSP";
	skills[1] = "ASP";
	skills[2] = "PHP";
	
	
	// 반복문을 사용하여 배열변수 안의 데이터를 모두 출력 
	tot = 0; 
	
	for(int i = 0; i < skills.length ; i++) {
		
		System.out.println( skills[i]);
		
	}	
   }	
}


/*
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문1> 만약 kors[4] = 99; 다음 줄에 kors[5] = 55; 를 삽입하면?
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

=> 에러가 발생하지는 않지만 실행시 에러가 발생한다.
=> 존재하지 않는 인덱스 번호를 서술하면 코딩상 에러는 없고 실행 시 에러를 발생한다. 

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문2> kors[0] = 94; 이전에 System.out.println(kors[0];을 삽입하면?
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

=> 0 출력. 배열변수는 자동 초기화 된다. 

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문3> kors[0] = 94; 이전에 System.out.println(kors[0];을 삽입하면?
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

=> 에러발생. 현재 배열변수의 자료형은 int 이므로 실수가 저장될 수 없다.
	
	
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문4> 현재 skills 이란 변수에 저장된 데이터의 종류는? 
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

=> 1차원 Array 객체가 들어있다. ( 직선처럼 1자로 되어있어서 1차원 배열객체)

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문5> skills[0] = "JSP"; 이전에 System.out.print(skills[0]);를 출력하면?
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
=> null 출력. 

배열변수는 자동초기화 된다.
현재 배열 변수의 자료형은 참조형이므로 null로 자동 초기화된다.

 기본형이 아니면 디폴트값으로 null 이 들어간다.


<참고> null 이란.
참조형데이터의 하나로서, 객체의 메위주가 아직은 없음. 나중에 들어갈 예정이니
이거라도 가지고 있어라고 하는 일종의 더미 데이터. 객체의 메위주가 들어갈 예정이라고 생각해야함. 

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문6> 

int[] kor = new int[5];
kors[0] = 94;
~
kors[4] = 99;

위 코딩은 다음 형식 3가지로 대체할 수 있다.
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

<대체 형식 1> 
	int[] kors = new int[]{ 94,82,76,88,99 };
<대체형식 2>
	int[] kors = { 94,82,76,88,99 };
<주의> 다음형식은 안됨.
	int[] kors;
	kors = { 94,82,76,88,99 };
	
	
	
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<문7>  메소드 안에서 배열 객체의 메위주를 리턴할 경우 아래처럼 되는게 있고 안되는게 있다.
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

<예1>-OK

int[] xxx(){
int[] kors = new int[5];
kor[0] = 99;
return kors;

//return 배열객체의 매위주를 리턴 하는데 데이터형은 int 다.

<예2>-OK


int[] xxx(){
int[] kor = new int[]{99};
return kor;
}


<예3>-OK
int[] xxx(){
int[] kors = {99};
return kors;


<예4>-OK

int[] xxx(){

return new int[]{99};


<예5>-NG(new 없이 하면 안된다. )
(return 다음바로 중괄호 데이터가 나오면 안된다.나머진 다된다.)

int[] xxx(){

return {99};





 */ 







