@Given("User is on the signin page")
	public void user_is_on_the_signin_page() {
	    System.out.println("signinpage");
	}
	@When("User enter valid username and password")
	public void user_enter_valid_username_and_password() {
		System.out.println("enters username and password");
	}
	@When("User click the login button")
	public void user_click_the_login_button() {
		System.out.println("clicks on login");
	}
	@Then("User should be redirected to my account page")
	public void user_should_be_redirected_to_my_account_page() {
		System.out.println("welcome message appears");
	}
	
	@When("User enters invalid username and password")
	public void user_enters_invalid_username_and_password() {
	    System.out.println("enters invalid details");
	}
	
	@Then("User should see error message")
	public void user_should_see_error_message() {
	    System.out.println("error message appears");
	}
