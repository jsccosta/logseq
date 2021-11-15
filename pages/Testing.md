# The Test Anatomy
## Include 3 parts in each test name
- A test report should tell whether the current application revision satisfies the requirements for the people who are not necessarily familiar with the code: the tester, the DevOps engineer who is deploying and the future you two years from now. This can be achieved best if the tests speak at the requirements level and include 3 parts:
	- What is being tested? For example, the ProductsService.addNewProduct method
	- Under what circumstances and scenario? For example, no price is passed to the method
	- What is the expected result? For example, the new product is not approved
## Structure tests by the AAA pattern
- **Do**: Structure your tests with 3 well-separated sections Arrange, Act & Assert (AAA). Following this structure guarantees that the reader spends no brain-CPU on understanding the test plan:
	- Arrange: All the setup code to bring the system to the scenario the test aims to simulate. This might include instantiating the unit under test constructor, adding DB records, mocking/stubbing on objects and any other preparation code
	- Act: Execute the unit under test. Usually 1 line of code
	- Assert: Ensure that the received value satisfies the expectation. Usually 1 line of code
- **Otherwise**: Not only do you spend hours understanding the main code, but what should have been the simplest part of the day (testing) stretches your brain
## Describe expectations in a product language: use BDD-style assertions
- **Do**: Coding your tests in a declarative-style allows the reader to get the grab instantly without spending even a single brain-CPU cycle. When you write imperative code that is packed with conditional logic, the reader is forced to exert more brain-CPU cycles. In that case, code the expectation in a human-like language, declarative BDD style using expect or should and not using custom code. If Chai & Jest doesn't include the desired assertion and it’s highly repeatable, consider extending Jest matcher (Jest) or writing a custom Chai plugin
- **Otherwise**: The team will write less tests and decorate the annoying ones with .skip()
- Stick to black-box testing: Test only public methods
  white_check_mark Do: Testing the internals brings huge overhead for almost nothing. If your code/API delivers the right results, should you really invest your next 3 hours in testing HOW it worked internally and then maintain these fragile tests? Whenever a public behavior is checked, the private implementation is also implicitly tested and your tests will break only if there is a certain problem (e.g. wrong output). This approach is also referred to as behavioral testing. On the other side, should you test the internals (white box approach) — your focus shifts from planning the component outcome to nitty-gritty details and your test might break because of minor code refactors although the results are fine - this dramatically increases the maintenance burden
- x Otherwise: Your tests behave like the boy who cried wolf: shouting false-positive cries (e.g., A test fails because a private variable name was changed). Unsurprisingly, people will soon start to ignore the CI notifications until someday, a real bug gets ignored…