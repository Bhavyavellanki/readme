private WebDriver driver;
	homepage home;
	@Given("I navigate to the home page")
	public void i_navigate_to_the_home_page() throws InterruptedException {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		home = new homepage(driver);
	    Thread.sleep(2000);
	    System.out.println("navigates to home page");
	}
	@When("I search for {string}")
	public void i_search_for(String pet) {
		home.searchForPet(pet);
		System.out.println("searches for a pet");
	}
	@Then("I should see a list of pet results")
	public void i_should_see_a_list_of_pet_results() {
		assertTrue(home.searchIsDisplayed());
		System.out.println("list of pets are displayed");
		driver.quit();
	}
