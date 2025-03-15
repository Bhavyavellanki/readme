WebDriver driver; 
	@Given("User is signed in")
	public void user_is_signed_in() {
		driver = new ChromeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		homepage home = new homepage(driver);
		signinpage signin = new signinpage(driver);
		home.clickSignIn();
		signin.enterUsername("user1");
		signin.enterPassword("pass");
		signin.clickSignIn();
		System.out.println("user signs in");
	}
	@When("User adds a pet to cart")
	public void user_adds_a_pet_to_cart() throws InterruptedException {
		shoppingcartpage cart = new shoppingcartpage(driver);
		Thread.sleep(2000);
		cart.navigateToProductPage();
		Thread.sleep(2000);
		cart.addProductToCart();
		System.out.println("adds a product");
	}
	@When("User proceeds to checkout")
	public void user_proceeds_to_checkout() {
		shoppingcartpage cart = new shoppingcartpage(driver);
		cart.proceedToCheckout();
		System.out.println("proceeds to checkout");
	}
	@When("User confirms the order")
	public void user_confirms_the_order() {
		checkoutpage checkout= new  checkoutpage(driver);
		checkout.clickContinue();
		checkout.clickConfirm();	
		System.out.println("confirms order");
	}
	@Then("User should see an order confirmation page")
	public void user_should_see_an_order_confirmation_page() {
		checkoutpage checkout= new  checkoutpage(driver);
		assertTrue(checkout.confirmmessage());
	    System.out.println("order confirmed");
	    driver.quit();
	}
