WebDriver driver;
	loginpage login;
	productpage products;
	checkoutpage checkout;
	@Given("User is in homepage")
	public void user_is_in_homepage() {
		driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.get("https://www.saucedemo.com/");
        login = new loginpage(driver);
        login.enterUsername("standard_user");
        login.enterPassword("secret_sauce");
        login.clickLoginButton();    
        products = new productpage(driver);
	}

	@When("User adds  product to  cart")
	public void user_adds_product_to_cart() {
		products.addFirstProductToCart();
		
	}

	@When("User proceeds to checkout")
	public void user_proceeds_to_checkout() {
		checkout = new checkoutpage(driver);
		checkout.goToCart();
		checkout.clickCheckout();
	}
	@When("User enters shipping details")
	public void user_enters_shipping_details() throws InterruptedException {
		checkout.enterCheckoutDetails("Bhavya", "Sree", "12345");
	    Thread.sleep(2000);
	}

	@When("User confirms the order")
	public void user_confirms_the_order() {
		checkout.completePurchase();
	}

	@Then("User should see the order confirmation message")
	public void user_should_see_the_order_confirmation_message() throws InterruptedException {
	    Thread.sleep(2000);
	    assertEquals("Thank you for your order!", checkout.getConfirmationMessage());
	    System.out.println("Order completed successfully: ");
	    driver.quit();    	
	}
