@Given("User navigates to a product page")
	public void user_navigates_to_a_product_page() {
	   System.out.println("navigates to product page");
	}
	@When("User adds product to the cart")
	public void user_adds_product_to_the_cart() {
		System.out.println("navigates to product page");   
	}
	@Then("The product should appear in the shopping cart")
	public void the_product_should_appear_in_the_shopping_cart() {
		System.out.println("product appears");
	}
	@Given("User has items in the shopping cart")
	public void user_has_items_in_the_shopping_cart() {
	    System.out.println("user adds items");
	}
	@When("User removes an item from the cart")
	public void user_removes_an_item_from_the_cart() {
		System.out.println("user removes an item");
	}
	@Then("The item should be removed from the cart")
	public void the_item_should_be_removed_from_the_cart() {
		System.out.println("cart gets updated");
	}
	@Given("User have items in the shopping cart")
	public void user_have_items_in_the_shopping_cart() {
	   System.out.println("user adds items");
	}
	@When("User updates the quantity of a product")
	public void user_updates_the_quantity_of_a_product() {
		System.out.println("user adds items");
	}
	@Then("Cart should reflect the updated quantity")
	public void cart_should_reflect_the_updated_quantity() {
		System.out.println("cart gets updated");
	}
