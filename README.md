private WebDriver driver;
	homepage home;
	catscategorypage catspage;
	@Given("user in the PetStore HOME page")
	public void user_in_the_pet_store_home_page() throws InterruptedException {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		home = new homepage(driver);
	    Thread.sleep(2000);
	    System.out.println("homepage");
	}
	@When("User selects the CATS category")
	public void user_selects_the_cats_category() {
		home.selectCat();
		System.out.println("selects cats category");
		catspage = new catscategorypage(driver);
	}
	@Then("User reaches the cats page with list of available cats with the product id, product name")
	public void user_reaches_the_cats_page_with_list_of_available_cats_with_the_product_id_product_name() {
		assertTrue(catspage.isCategoryDisplayed());
		System.out.println("reaches cat page");
		driver.quit();
	}
	
