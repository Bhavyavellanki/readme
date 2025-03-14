Feature: Verify Pet Images Redirection on Home Page
Scenario Outline: Check if pet images redirect to their respective category page
Given User is on the home page
When User clicks on the pet image for "<Pet Category>"
Then User should be redirected to the "<Expected URL>" page

Examples:
      | Pet Category | Expected URL                      |
      | Fish         | viewCategory=&categoryId=FISH     |
      | Dogs         | viewCategory=&categoryId=DOGS     |
      | Cats         | viewCategory=&categoryId=CATS     |
      | Reptiles     | viewCategory=&categoryId=REPTILES |
      | Birds        | viewCategory=&categoryId=BIRDS    |
