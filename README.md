Feature: Verifying products in Cat category
Scenario: User views available cats for purchase 
Given user in the PetStore HOME page
 When User selects the CATS category 
Then User reaches the cats page with list of available cats with the product id, product name
@persianCat 
Scenario: Buy Persian Cat 
Given User is in Cats Page
When User clicks on the product Id of Persian Cat 
Then User is redirected to Persian Cat page
@ManxCat 
Scenario: Buy Manx Cat
Given User is in Cats Page 
When User clicks on the product Id of manx Cat 
Then User is redirected to Manx Cat product page

Scenario: User verifies the first cat category
Given  User is on the Cats category page
When  User verifies the category is displayed
And User selects first category 
And User selects the first cat product 
And User adds the product to the cart
Then Product should be visible in the shopping cart
