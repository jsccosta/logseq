# Static
- Static Members #card #ts
	- Classes may have static members. These members aren’t associated with a particular instance of the class. They can be accessed through the class constructor object itself.
-
-
- Static Modifiers #card
- Static members can also use the same public, protected, and private visibility modifiers:
- class MyClass {
  private static x = 0;
  }
  console.log(MyClass.x);
  Property 'x' is private and only accessible within class 'MyClass'.