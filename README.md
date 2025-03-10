WebDriver driver;
	loginpage login;
	productpage products;
	checkoutpage checkout;
	@Given("User is logged in")
	public void user_is_logged_in() {
				driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.get("https://www.saucedemo.com/");
        login = new loginpage(driver);
        login.enterUsername("standard_user");
        login.enterPassword("secret_sauce");
        login.clickLoginButton();
        products = new productpage(driver);
	}

	@When("User adds a product to the cart")
	public void user_adds_a_product_to_the_cart() {
		products.addFirstProductToCart();
	}

	@Then("The cart should show the correct number of items")
	public void the_cart_should_show_the_correct_number_of_items() {
		 assertEquals("1", products.getCartBadgeCount());
         driver.quit();
	}
