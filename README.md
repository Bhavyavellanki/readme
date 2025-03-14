@Given("User is signed in")
	public void user_is_signed_in() {
		System.out.println("user signs in");
	}
	@When("User adds a pet to cart")
	public void user_adds_a_pet_to_cart() {
		System.out.println("adds a product");
	}
	@When("User proceeds to checkout")
	public void user_proceeds_to_checkout() {
		System.out.println("proceeds to checkout");
	}
	@When("User confirms the order")
	public void user_confirms_the_order() {
		 System.out.println("confirms order");
	}
	@Then("User should see an order confirmation page")
	public void user_should_see_an_order_confirmation_page() {
	    System.out.println("order confirmed");
	}
