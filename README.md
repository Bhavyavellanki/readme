WebDriver driver;
    manxcatpage catpage;
    homepage home;
    catscategorypage category;

@Given("I open the pet store website")
public void i_open_the_pet_store_website() {
    driver = new ChromeDriver();
    driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
    driver.get("https://petstore.octoperf.com/actions/Catalog.action");
    catpage = new manxcatpage(driver);
}

@When("I navigate to the Tailless Manx product page")
public void i_navigate_to_the_Tailless_Manx_product_page() throws InterruptedException {
	home = new homepage(driver);
	Thread.sleep(2000);
	home.selectCat();
	category = new catscategorypage(driver);
	category.selectManxCat();
	catpage.selectFirstCat();	
}

@Then("I should see the product title as {string}")
public void i_should_see_the_product_title_as(String expectedTitle) {
	assertEquals(expectedTitle, catpage.getProductTitle(), "Product title does not match!");
}

@Then("I should see the product description as {string}")
public void i_should_see_the_product_description_as(String expectedDescription) {
	try {
	assertEquals(expectedDescription, catpage.getProductDescription(), "Product description does not match!");
	}
	catch(Exception e) {
		System.err.println("Error verifying product availability: " + e.getMessage());
	}
}

@Then("I should see the product price as {string}")
public void i_should_see_the_product_price_as(String expectedPrice) {
    assertEquals(expectedPrice, catpage.getProductPrice(), "Product price does not match!");
}

@Then("the product image should be displayed")
public void the_product_image_should_be_displayed() {
	assertTrue(catpage.isProductImageDisplayed(), "Product image is not displayed!");
}

@Then("I should see the product availability as {string}")
public void i_should_see_the_product_availability_as(String expectedAvailability) {
	try {
        assertEquals(expectedAvailability, catpage.getProductAvailability(),
            "Expected availability: " + expectedAvailability + " but got: " + catpage.getProductAvailability());
    } catch (Exception e) {
        System.err.println("Error verifying product availability: " + e.getMessage());
    } finally {
	driver.quit();
}
}
