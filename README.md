private WebDriver driver;
	homepage home;
	@Given("I navigate to the main page")
	public void i_navigate_to_the_main_page() {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		home = new homepage(driver);
	    System.out.println("navigates to home page");
	}
	 @When("I search for an invalid pet {string}")
	    public void i_search_for_an_invalid_pet(String petName) {
	        home.searchForPet(petName);
	        System.out.println("Searches for an invalid pet: " + petName);
	    }
	 @Then("I should see a message indicating no results found")
	 public void i_should_see_a_message_indicating_no_results_found() {
	        System.out.println("'No results found' message is displayed.");
	        driver.quit();
	        assertTrue(false);      
	 }
