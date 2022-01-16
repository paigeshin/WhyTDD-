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

### Code to be tested

```swift
//
//  Account.swift
//  FirstUnitTest
//
//  Created by paige on 2022/01/16.
//

import Foundation

enum AccountError: Error {
    case insufficientFunds
}

struct Account {
    
    var balance: Double = 0.0
    
    mutating func deposit(_ amount: Double) {
        self.balance += amount
    }
    
    mutating func withdraw(_ amount: Double) throws {
        let netBalance = self.balance - amount
        if netBalance < 0 {
            throw AccountError.insufficientFunds
        } else {
            self.balance -= amount
        }
    }
    
}
```

```swift
import XCTest
@testable import FirstUnitTest

class FirstUnitTestTests: XCTestCase {

    private var account: Account!
    
    // this function is called BEFORE each test
    override func setUp() {
        super.setUp()
        self.account = Account()
    }
    
    func test_WidthdrawFromInsufficientBalance() {
        self.account.deposit(100)
        XCTAssertThrowsError(try self.account.withdraw(300)) { error in
            XCTAssertEqual(error as! AccountError, AccountError.insufficientFunds)
        }
    }
    
    func test_InitialBalanceZero() {
        XCTAssertTrue(account.balance == 0, "Balance is not zero!")
        
    }
    
    func test_DepositFunds() {
        account.deposit(100)
        XCTAssertEqual(100, account.balance)
    }
    
    override class func tearDown() {
        super.tearDown()
        
        // this function is called AFTER each test
    }
    
}
```
