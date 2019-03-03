# Testing

## Clasificación de tipos de test \(según Sandro Mancuso\)

* **Acceptance Test** – to test a behavior of the system. The entry point is usually the Application Service \(from DDD, Use Case in [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) or Action in [Interaction-Driven Development](https://codurance.com/2017/12/08/introducing-idd/)\). External dependencies \(e.g. Databases\) can be mocked \(white box testing\) or we could use the real implementation \(black box testing\)
* **Unit test** – the unit under test is a single class or a small group of classes
* **Component Test** – the unit under test is the Domain Model
* **Feature Test** – the unit under test is the Application Service  and the Domain Model
* **Integration Test** – testing classes at the system boundaries \(e.g. testing the SQL implementation of a Repository\)
* **User Journey Test** \(the unit under test is the UI and the backend is mocked\)

You start with an Acceptance Test, then move to the other test types, as needed, while mocking collaborators.

