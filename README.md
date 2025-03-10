 WebDriver driver;
	loginpage login;
	productpage products;
	
	@Given("User is on the SauceDemo login page")
	public void user_is_on_the_SauceDemo_login_page() {
        driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.get("https://www.saucedemo.com/");
        login = new loginpage(driver);
        test = extent.startTest("login with valid password");
	}

	@When("User enters valid username and password")
	public void user_enters_valid_username_and_password() throws InterruptedException, IOException {	
		 File file = new File("C:\\Users\\BHAVYA\\Desktop\\Selenium Prac\\testdata.xlsx");
	        FileInputStream inputStream = new FileInputStream(file);
	        XSSFWorkbook workbook = new XSSFWorkbook(inputStream);
	        Sheet sheet = workbook.getSheet("Sheet1");

	        for (int i = 1; i <= sheet.getLastRowNum(); i++) {
	            Row row = sheet.getRow(i);
	            for (int j = 0; j < row.getLastCellNum(); j++) 
		        {
		        	String values = row.getCell(j).getStringCellValue();
		        	if(j == 0)
		        	{
		        		driver.findElement(By.id("user-name")).clear();
		        		driver.findElement(By.id("user-name")).sendKeys(values);
		        	}
		        	if(j == 1)
		        	{
		        		driver.findElement(By.id("password")).clear();
		        		driver.findElement(By.id("password")).sendKeys(values);
		        	}
	        }
	        workbook.close(); }
	    }
	@When("Clicks on the login button")
	public void clicks_on_the_login_button() {
		 login.clickLoginButton();
		 products = new productpage(driver);	 
	}

	@Then("User should be navigated to the Products Page")
	public void user_should_be_navigated_to_the_Products_Page() 
	{
		try {
            
            assertEquals("Products", products.getTitle());
            System.out.println("Login Successful - Products Page displayed");
        } catch (Exception e) {
            assertTrue(login.isErrorMessageDisplayed());
            System.out.println("Error message displayed: " + login.getErrorMessage());
        } finally {
            driver.quit();
        }
	}
	@When("User enters an invalid username and password")
	public void user_enters_an_invalid_username_and_password() {
	    login.enterUsername("invalid_user");
	    login.enterPassword("wrong_password");
	}

	@Then("User should see an error message")
	public void user_should_see_an_error_message() {
	    assertTrue(login.isErrorMessageDisplayed());
	    assertEquals("Epic sadface: Username and password do not match any user in this service", login.getErrorMessage());
	    System.out.println("Error message displayed: " +login.getErrorMessage());
	    driver.quit();
	}
