# Design a banking system like EasyPaisa. 
List down the different components (functionalities) that may be required and the communication/connection amongs these.

1. User Account Management
   1.1 Create an Account
   1.2 Change Password
   1.3 Forgot Password
   1.4 User Login
   1.4 View Balance  
2. Transactions
   2.1 Send Money
     2.1.1 To Another Wallet Account
     2.1.2 To Any Bank
     2.1.3 CNIC
   2.2 Receive Money
     2.2.1 From Bank Account
     2.2.2 From Another Linked Wallet Account
3. Payments
  3.1 Fees
  3.2 Challan Payments
  3.3 Corporate Payments
4. Reports
  4.1 Transaction History
  4.2 Sent Money
  4.3 Receive Money
  4.4 Login History
5. Security
  5.1 User Authentication and Authorization
  5.2 Generate OTP
  5.3 Validate OTP
  5.4 User Blocking Mechanism
6. Notifications (_SMS, EMAIL, WHATSAPP_)
  6.1 System Generated Notifications
  6.2 Transaction Notifications
  6.3 Promotions Notifications
  6.4 Security Related Notifications

**Database**
- SQL - to make it more secure + relational seems to make more sense
- Transaction management would be much better (rollback, etc).
- Maybe in some extended features we could use noSQL.


**Handling multiple/concurrent transactions from different devices?**
- Can block user to login from multiple devices (keep record of devices)
- else: implement different security measures
  - strong locking mechanism for transactions (1 request processed at a time). This mechanism should be at application and on database level both. Manage critical sections when updating balance.

**Scalability**
- multiple users use app at the same time. How to save time in our operations? (discussing notifications flow)
  - can use notification queues instead of function/api call
  - send notification in parallel
  - keep servers close to users region
  - scale up machines at runtime - use load balancers 