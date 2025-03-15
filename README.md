WebDriver driver;
	catscategorypage catspage;
	manxcatpage manxpage;
	@Given("User is on the Cats category page")
	public void user_is_on_the_cats_category_page() {
		driver = new EdgeDriver();
		catspage = new catscategorypage(driver);
		catspage.navigateToCatsCategory();
	    System.out.println("cats page");
	}
	@When("User verifies the category is displayed")
	public void user_verifies_the_category_is_displayed() {
		Assert.assertTrue(catspage.isCategoryDisplayed());
		 System.out.println("category is displayed");
	}
	@When("User selects first category")
	public void user_selects_first_category() {
		 catspage.selectManxCat();
		 System.out.println("selects first cat page");
	}
	@When("User selects the first cat product")
	public void user_selects_the_first_cat_product() {
		manxpage = new manxcatpage(driver);
		manxpage.selectFirstCat();
		 System.out.println("selects first cat");
	}
	@When("User adds the product to the cart")
	public void user_adds_the_product_to_the_cart() {
		manxpage.addToCart();
		 System.out.println("adds first product");
	}
	@Then("Product should be visible in the shopping cart")
	public void product_should_be_visible_in_the_shopping_cart() {
		assertTrue(manxpage.isProductInCart());
		 System.out.println("product is visible");
		 driver.quit();
	}
