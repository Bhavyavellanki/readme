Feature: Product page functionality
@producttitle
   Scenario: Check whether product title label is displayed
     Given User should login to swag labs using correct "standard_user" and "secret_sauce"
     Then User should see the product title label
      
 @add to cart
  Scenario: Adding products to cart
    Given I am already Logged in as "standard_user"
    When I click Add to Cart on "<item>"
    Then The "remove" button on "<item>" appear
    Examples:
      | item                              |
      | Sauce Labs Backpack               |
      | Sauce Labs Bike Light             |
      | Sauce Labs Onesie                 |
      | Test.allTheThings() T-Shirt (Red) |
   @sort   
   Scenario Outline: Sorting product with given parameter
    Given I am already Logged in as "standard_user"
    And I am on Inventory Page
    When I select sorting method as "<parameter>"
    Then Product is sorted using parameter "<parameter>" 
    Examples:
    | parameter             | 
    | Name (A to Z)         | 
    | Name (Z to A)         | 
    | Price (low to high)   | 
    | Price (high to low)   | 
