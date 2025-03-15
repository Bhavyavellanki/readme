Feature: Shopping flow in Demo Web Shop

  Scenario: User purchases a smartphone from Electronics
    Given the user opens the demo webshop application
    Then the user should see the correct page title
    When the user navigates to Electronics and then Cell Phones
    And the user selects a smartphone
    Then the user should see the correct price
    And the shopping cart should be empty
    When the user adds the product to cart
    Then the shopping cart should show one item
    When the user goes to the cart
    And the user attempts to checkout
    Then an error message should appear
    When the user accepts terms of service
    And the user attempts to checkout again
    Then the user should proceed with the checkout process
