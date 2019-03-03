# Testing & Refactoring

## Clasificación de tipos de test \(según Sandro Mancuso\)

* **Acceptance Test** – to test a behavior of the system. The entry point is usually the Application Service \(from DDD, Use Case in [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) or Action in [Interaction-Driven Development](https://codurance.com/2017/12/08/introducing-idd/)\). External dependencies \(e.g. Databases\) can be mocked \(white box testing\) or we could use the real implementation \(black box testing\)
* **Unit test** – the unit under test is a single class or a small group of classes
* **Component Test** – the unit under test is the Domain Model
* **Feature Test** – the unit under test is the Application Service  and the Domain Model
* **Integration Test** – testing classes at the system boundaries \(e.g. testing the SQL implementation of a Repository\)
* **User Journey Test** \(the unit under test is the UI and the backend is mocked\)

You start with an Acceptance Test, then move to the other test types, as needed, while mocking collaborators.

## Refactoring

* Use Dependency Breaking techniques \(e.g. Subclass and override method\) in order to write tests for legacy code.
* Test from the shallowest branch, since it contains the lowest number of dependencies.
* Refactor from the deepest branch.
* Use [Test Data Builders](http://blog.ploeh.dk/2017/08/15/test-data-builders-in-c/)  ****to make tests more readable.
* Use [Guard Clauses](http://wiki.c2.com/?GuardClause) to make the happy path more visible.
* Use the [Balanced Abstraction Principle](https://codurance.com/2015/01/27/balanced-abstraction-principle/) to make sure that everything in a method is at the same level of abstraction. Public methods should tell a story.

## Libros & Material

* [Working Effectivery with Legacy Code](https://www.amazon.co.uk/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052)
* [Testing & Refactoring Legacy Code \(video - Sandro Mancuso\)](https://www.youtube.com/watch?v=_NnElPO5BU0)

