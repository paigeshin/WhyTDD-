# WhyTDD-

### Process

1. Write a failing test 
2. Make the test pass
3. Refactor 

### Why you should use TDD?

- **Make changes with confidence**
- Automate user interface using UI testing
- Testing helps to create better software architecture
- Help you make decisions

### What should you test?

- **DO** test Application domain
- **DON’T** test generated code
- **DON’T** test issues caught by compiler
- **DON’T** test dependency or third party code
- **DO** test application user interface by automating unit tests

### When should you use TDD

- Greenfield development (new)
- Brownfield development (legacy)
- **Understanding the domain ⇒** Understand specific domains (financial, sports), write a lot of tests
- Hackathon (evalute)

### Common misconceptions about TDD

- **Testing is QA’s Job**
- **TDD takes too long!**
- **My Client Won’t Allow Me**

### Bad Unit Test

```swift
// This doesn't mean anything 
func test_CreatedBankAccountInstance() {
	let bankAccount = BankAccount()
	XCTAssertNotNil(bacnkAccount)
}
```

```swift
// This doesn't mean anything 
func test_AssignUserToBankAccount() {
	let bankAccount = BankAccount()
	bankAccount.user = User()
	XCTAssertNotNil(bankAccount.user)
}
```

### Good Unit Testing

- Independent
- Automatic
- Repeatable
- Readable
