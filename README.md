WebDriver driver;
    shoppingcartpage shoppingCart;
    @Given("User have items in the shopping cart")
	public void user_have_items_in_the_shopping_cart() {
    	driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        shoppingCart = new shoppingcartpage(driver);
        shoppingCart.navigateToProductPage();
 	    System.out.println("navigates to product page");
 	    shoppingCart.addProductToCart();
	   System.out.println("user adds items");
	}
	@When("User updates the quantity of a product")
	public void user_updates_the_quantity_of_a_product() throws InterruptedException {
		shoppingCart.updateProductQuantity("2");
		Thread.sleep(2000);
		System.out.println("user adds items");
	}
	@Then("Cart should reflect the updated quantity")
	public void cart_should_reflect_the_updated_quantity() {
		assertTrue(shoppingCart.isQuantityUpdated("2"), "Quantity not updated");
		System.out.println("cart gets updated");
		driver.quit();
	}
