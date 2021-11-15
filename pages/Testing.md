# The Test Anatomy
- Include 3 parts in each test name
- A test report should tell whether the current application revision satisfies the requirements for the people who are not necessarily familiar with the code: the tester, the DevOps engineer who is deploying and the future you two years from now. This can be achieved best if the tests speak at the requirements level and include 3 parts:
	- What is being tested? For example, the ProductsService.addNewProduct method
	- Under what circumstances and scenario? For example, no price is passed to the method
	- What is the expected result? For example, the new product is not approved
- ```