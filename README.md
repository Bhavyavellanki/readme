Feature: User Login
Scenario: login with valid credentials
Given User is on the signin page
When User enter valid username and password
And User click the login button
Then User should be redirected to my account page
Scenario: login with invalid credentials
Given User is on the signin page
When User enters invalid username and password
And User click the login button
Then User should see error message
