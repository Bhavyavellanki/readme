WebDriver driver;
    shoppingcartpage shoppingCart;
    @Given("User has items in the shopping cart")
	public void user_has_items_in_the_shopping_cart() {
    	driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        shoppingCart = new shoppingcartpage(driver);
        shoppingCart.navigateToProductPage();
 	    System.out.println("navigates to product page");
 	    shoppingCart.addProductToCart();
	    System.out.println("user adds items");
	}
	@When("User removes an item from the cart")
	public void user_removes_an_item_from_the_cart() {
		shoppingCart.removeItemFromCart();
		System.out.println("user removes an item");
	}
	@Then("The item should be removed from the cart")
	public void the_item_should_be_removed_from_the_cart() {
		assertTrue(shoppingCart.isCartEmpty(), "Cart is not empty");
		System.out.println("cart gets updated");
		driver.quit();
	}
