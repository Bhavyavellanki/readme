Feature: User Registration

  Scenario Outline: Register a new user on JPetStore
    Given User should be on the Registration Page
    When User enters User Information "<Username>" "<Password>" "<RepeatPassword>"
    And User enters Account Information "<FirstName>" "<LastName>" "<Email>" "<Phone>" "<Address1>" "<Address2>" "<City>" "<State>" "<Zip>" "<Country>"
    And User enters Profile Information "<Language>" "<Category>"
    And User clicks on Save Account Information
    Then User should be Registered Successfully
    And User should be redirected to the home page of JPetstore

Examples:
   | Username  | Password   | RepeatPassword | FirstName | LastName  | Email             | Phone      | Address1 | Address2 | City          | State  | Zip    | Country | Language | Category |
   | Bhavya123 | Bhavya@123 | Bhavya@123     | Vellanki  | Bhavya    | bhavya@gmail.com  | 7989710535 | Vizag    | Vizag    | Visakhapatnam | andhra | 522616 | India   | english  | DOGS     |

