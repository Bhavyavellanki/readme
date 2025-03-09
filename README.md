Feature: Add a product to the cart
Scenario: User adds a product to the cart
Given User is logged in
When User adds a product to the cart
Then The cart should show the correct number of items


Feature: Checkout Process on SauceDemo
Scenario: User completes checkout successfully
Given User is in homepage
When User adds  product to  cart
And User proceeds to checkout
And User enters shipping details
And User confirms the order
Then User should see the order confirmation message

Feature: Login to SauceDemo
Scenario: User logs in with valid credentials
Given User is on the SauceDemo login page
When User enters valid username and password
And Clicks on the login button
Then User should be navigated to the Products Page

Scenario: User tries to log in with invalid credentials
Given User is on the SauceDemo login page
When User enters an invalid username and password
And Clicks on the login button
Then User should see an error message

Feature: Verify Products Page

Scenario: Check if all products are displayed
Given User is logged into SauceDemo
When User is on the Products Page
Then All products should be displayed correctly
