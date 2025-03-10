WebDriver driver;
	loginpage login;
	productpage products;
	@Given("User is logged into SauceDemo")
	public void user_is_logged_into_SauceDemo() {
		 driver = new ChromeDriver();
	     driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
	     driver.get("https://www.saucedemo.com/");
	     login = new loginpage(driver);
	     login.enterUsername("standard_user");
	     login.enterPassword("secret_sauce");
	     login.clickLoginButton();
	     products = new productpage(driver);
	 }

	@When("User is on the Products Page")
	public void user_is_on_the_Products_Page() {
        assertEquals("Products", products.getTitle());
	}

	@Then("All products should be displayed correctly")
	public void all_products_should_be_displayed_correctly() {
	        assertTrue(products.getProductCount() > 0);
	        System.out.println("All products are displayed correctly");
	        driver.quit();  
	}
