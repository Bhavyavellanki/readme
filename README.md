WebDriver driver;
	catscategorypage catspage;
	persiancatpage persiancat;
	@Given("User is in Cats Page")
	public void user_is_in_cats_page() {
		driver = new EdgeDriver();
		catspage = new catscategorypage(driver);
		catspage.navigateToCatsCategory();
		System.out.println("cat page");
	}
	@When("User clicks on the product Id of Persian Cat")
	public void user_clicks_on_the_product_id_of_persian_cat() {
		catspage.selectPersianCat();
		System.out.println("selects persian cat");
	}
	@Then("User is redirected to Persian Cat page")
	public void user_is_redirected_to_persian_cat_page() {
		persiancat = new persiancatpage(driver); // Initialize PersianCatPage
	    boolean isPresent = false;
	    try {
	        isPresent = persiancat.persiancatpresent().isDisplayed();
	        System.out.println("Persian Cat page is displayed.");
	    } catch (NoSuchElementException e) {
	        System.out.println("Persian Cat page is NOT displayed.");
	    } finally { driver.quit(); }
	    assertTrue("Persian Cat page should be displayed", isPresent);
		System.out.println("persian cat page");
	}
