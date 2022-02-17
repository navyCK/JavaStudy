## ArrayList

고정 크기의 배열을 동적 형태로 사용할 수 있다.

```java
public class ArrayListUse {
	public static void main(){
		//고정 형태의 배열 사용
		Person people[] = new Person[5];
		//동적 형태의 배열 사용
		ArrayList<Person> people2 = new ArrayList<Person>();
		
		//해당 객체 추가하기
		people[0] = new Person();
		people[1] = new Person();
		people[2] = new Person();

		//ArrayList의 경우 add메소드를 통해서 추가한다.
		people2.add(new Person());
		people2.add(new Person());
		people2.add(new Person());
		
		//불필요한 객체 제거 기능 index가 2이므로 맨 마지막 세번째에 들어간 객체 제거
		people2.remove(2);
		
	}
}

```
