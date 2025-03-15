private WebDriver driver;
	welcomepage welcome;
	homepage home;
	@Given("User is on the welcome page")
	public void user_is_on_the_welcome_page() throws InterruptedException {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/");
		Thread.sleep(1000);
	    System.out.println("user is on welcome page");
	    welcome = new welcomepage(driver);
	}
	@When("User clicks on Enter The Store")
	public void user_clicks_on_enter_the_store() {
		 welcome.clickEnterStore();
		 System.out.println("user clicks on enter store");
		 home = new homepage(driver);
	}
	@Then("User should be navigated to homepage")
	public void user_should_be_navigated_to_homepage() {
		assertTrue(home.logo());
		System.out.println("user navigates to homepage");  
		driver.quit();
	}
