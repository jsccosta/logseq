# Static
## Static Members
- Classes may have static members. These members aren’t associated with a particular instance of the class. They can be accessed through the class constructor object itself:
-
	- class MyClass {
	  static x = 0;
	  static printX() {
	    console.log(MyClass.x);
	  }
	  }
	  console.log(MyClass.x);
	  MyClass.printX();
-
-
- Static members can also use the same public, protected, and private visibility modifiers:
- class MyClass {
  private static x = 0;
  }
  console.log(MyClass.x);
  Property 'x' is private and only accessible within class 'MyClass'.