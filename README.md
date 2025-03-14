Feature: Checkout Process
Scenario: Complete checkout process
Given User is signed in
When User adds a pet to cart  
And User proceeds to checkout
And User confirms the order
Then User should see an order confirmation page
