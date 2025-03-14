Feature: Search Functionality
Scenario: Search for pets and verify results
Given I navigate to the home page
When I search for a pet
Then I should see a list of pet results
