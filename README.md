@When("User enters invalid {string} and {string}")
	public void user_enters_invalid_and(String username, String password) throws InterruptedException {
		signin = new signinpage(driver);
		System.out.println("enters username and password");
		signin.enterUsername(username);
		Thread.sleep(2000);
		signin.enterPassword(password);
	    System.out.println("enters invalid details");
	}
	@Then("User should see error message")
	public void user_should_see_error_message() throws InterruptedException {
		Thread.sleep(2000);
		assertTrue(signin.errorIsDisplayed());
	    System.out.println("error message appears");
	    driver.quit();
	}
