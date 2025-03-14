@Given("user in the PetStore HOME page")
	public void user_in_the_pet_store_home_page() {
	    System.out.println("homepage");
	}
	@When("User selects the CATS category")
	public void user_selects_the_cats_category() {
		System.out.println("selects cats category");
	}
	@Then("User reaches the cats page with list of available cats with the product id, product name")
	public void user_reaches_the_cats_page_with_list_of_available_cats_with_the_product_id_product_name() {
		System.out.println("reaches cat page");
	}
	@Given("User is in Cats Page")
	public void user_is_in_cats_page() {
		System.out.println("cat page");
	}
	@When("User clicks on the product Id of Persian Cat")
	public void user_clicks_on_the_product_id_of_persian_cat() {
		System.out.println("selects persian cat");
	}
	@Then("User is redirected to Persian Cat page")
	public void user_is_redirected_to_persian_cat_page() {
		System.out.println("persian cat page");
	}
	@Given("User is on the Cats category page")
	public void user_is_on_the_cats_category_page() {
	    System.out.println("cats page");
	}
	@When("User verifies the category is displayed")
	public void user_verifies_the_category_is_displayed() {
		 System.out.println("category is displayed");
	}
	@When("User selects first category")
	public void user_selects_first_category() {
		 System.out.println("selects first cat page");
	}
	@When("User selects the first cat product")
	public void user_selects_the_first_cat_product() {
		 System.out.println("selects first cat");
	}
	@When("User adds the product to the cart")
	public void user_adds_the_product_to_the_cart() {
		 System.out.println("adds first product");
	}
	@Then("Product should be visible in the shopping cart")
	public void product_should_be_visible_in_the_shopping_cart() {
		 System.out.println("product is visible");
	}
