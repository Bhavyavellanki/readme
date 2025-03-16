Scenario: Verify Home Page Title
Given User is on the welcome page
When User clicks on Enter The Store
Then User should be navigated to homepage
And The Title of the page should be "JPetStore Demo"

private WebDriver driver = tc_homepage.driver; // Get driver from tc_homepage

	    @Then("The Title of the page should be {string}")
	    public void the_Title_of_the_page_should_be(String expectedTitle) {
	        String actualTitle = driver.getTitle();
	        assertEquals(actualTitle, expectedTitle);
	        System.out.println("Page title verified: " + actualTitle);
	        driver.quit(); 
	    }

