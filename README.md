Feature: Shopping Cart Functionality
Scenario: Add items to the cart
Given User navigates to a product page
When User adds product to the cart
Then The product should appear in the shopping cart

Scenario: Remove items from the cart
Given User has items in the shopping cart
When User removes an item from the cart
Then The item should be removed from the cart

Scenario: Update product quantity in the cart
Given User have items in the shopping cart
When User updates the quantity of a product
Then Cart should reflect the updated quantity

