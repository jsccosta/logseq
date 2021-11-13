# Static
- Static Members #card #ts
  card-last-interval:: -1
  card-repeats:: 1
  card-ease-factor:: 2.5
  card-next-schedule:: 2021-11-14T00:00:00.000Z
  card-last-reviewed:: 2021-11-13T11:14:51.067Z
  card-last-score:: 1
	- Classes may have static members. These members aren’t associated with a particular instance of the class. They can be accessed through the class constructor object itself.
-
-
- Static Modifiers #card #ts
  card-last-interval:: -1
  card-repeats:: 1
  card-ease-factor:: 2.5
  card-next-schedule:: 2021-11-14T00:00:00.000Z
  card-last-reviewed:: 2021-11-13T11:14:53.663Z
  card-last-score:: 1
	- Static members can also use the same public, protected, and private visibility modifiers:
- Why No Static Classes? #card #ts
  card-last-interval:: -1
  card-repeats:: 1
  card-ease-factor:: 2.5
  card-next-schedule:: 2021-11-14T00:00:00.000Z
  card-last-reviewed:: 2021-11-13T11:14:59.097Z
  card-last-score:: 1
	- TypeScript (and JavaScript) don’t have a construct called static class the same way C# and Java do.
	- Those constructs only exist because those languages force all data and functions to be inside a class; because that restriction doesn’t exist in TypeScript, there’s no need for them. A class with only a single instance is typically just represented as a normal object in JavaScript/TypeScript.