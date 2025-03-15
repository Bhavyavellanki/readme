private WebDriver driver;
	homepage home;
	@Given("User is on the home page")
	public void user_is_on_the_home_page() throws InterruptedException {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		home = new homepage(driver);
	    Thread.sleep(2000);
		 System.out.println("homepage");
	}
	@When("User clicks on the pet image for {string}")
	public void user_clicks_on_the_pet_image_for(String string) throws InterruptedException {
		home.clickOnPetCategory(string);
		Thread.sleep(1000);
	    System.out.println(string);
	}
	@Then("User should be redirected to the {string} page")
	public void user_should_be_redirected_to_the_page(String string) {
		assertTrue(home.isRedirectedToPage(string), "Redirection failed. Expected: " + string + " but got: " + driver.getCurrentUrl());
	    driver.quit();
		 System.out.println(string);
	}
