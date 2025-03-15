WebDriver driver;
    shoppingcartpage shoppingCart;
	@Given("User navigates to a product page")
	public void user_navigates_to_a_product_page() {
	   driver = new ChromeDriver();
       driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
       driver.manage().window().maximize();
       shoppingCart = new shoppingcartpage(driver);
       shoppingCart.navigateToProductPage();
	   System.out.println("navigates to product page");
	}
	@When("User adds product to the cart")
	public void user_adds_product_to_the_cart() {
		shoppingCart.addProductToCart();
		System.out.println("navigates to product page");   
	}
	@Then("The product should appear in the shopping cart")
	public void the_product_should_appear_in_the_shopping_cart() {
		assertTrue(shoppingCart.isProductInCart(), "Product not found in cart");
		System.out.println("product appears");
		driver.quit();
	}
