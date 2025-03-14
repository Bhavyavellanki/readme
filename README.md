@Given("I navigate to the home page")
	public void i_navigate_to_the_home_page() {
	    System.out.println("navigates to home page");
	}
	@When("I search for a pet")
	public void i_search_for_a_pet() {
		System.out.println("searches for a pet");
	}
	@Then("I should see a list of pet results")
	public void i_should_see_a_list_of_pet_results() {
		System.out.println("list of pets are displayed");
	}
