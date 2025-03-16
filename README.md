Scenario Outline: Search for an invalid pet and verify no results
    Given I navigate to the main page
    When I search for an invalid pet "<PetName>"
    Then I should see a message indicating no results found

    Examples:
      | PetName  | 
      | Dragon   |
      | Unicorn  |
      | Phoenix  |
