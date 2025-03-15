private WebDriver driver;
	homepage home;
	signinpage signin;
	@Given("User is on the signin page")
	public void user_is_on_the_signin_page() throws InterruptedException {
		driver = new EdgeDriver();
		driver.get("https://petstore.octoperf.com/actions/Catalog.action");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		home = new homepage(driver);
	    Thread.sleep(2000);
	    home.clickSignIn();
	    System.out.println("signinpage");
	}
	@When("User enter valid username and password")
	public void user_enter_valid_username_and_password() throws InterruptedException, IOException {
		signin = new signinpage(driver);
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
		        		driver.findElement(By.name("username")).clear();
		        		driver.findElement(By.name("username")).sendKeys(values);
		        	}
		        	if(j == 1)
		        	{
		        		driver.findElement(By.name("password")).clear();
		        		driver.findElement(By.name("password")).sendKeys(values);
		        	}
	        }
	      workbook.close(); }
	}
	@When("User click the login button")
	public void user_click_the_login_button() {
		signin.clickSignIn();
		System.out.println("clicks on login");
	}
	@Then("User should be redirected to my account page")
	public void user_should_be_redirected_to_my_account_page() {
		assertTrue(home.welcomemsg());
		System.out.println("welcome message appears");
		driver.quit();
	}
