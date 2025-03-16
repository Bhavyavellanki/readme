Feature: Validate Product Details on Pet Store
Scenario: Verify all product details of Tailless Manx
Given I open the pet store website
When I navigate to the Tailless Manx product page
Then I should see the product title as "Tailless Manx"
And I should see the product description as "Tailless Manx"
And I should see the product price as "$58.50"
And the product image should be displayed
And I should see the product availability as "In Stock"
