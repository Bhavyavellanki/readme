@Given("User is on the home page")
	public void user_is_on_the_home_page() {
		 System.out.println("homepage");
	}
	@When("User clicks on the pet image for {string}")
	public void user_clicks_on_the_pet_image_for(String string) {
	    System.out.println(string);
	}
	@Then("User should be redirected to the {string} page")
	public void user_should_be_redirected_to_the_page(String string) {
		 System.out.println(string);
	}
