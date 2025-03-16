 WebDriver driver;
	 WebElement usernameField, passwordField, repeatedPasswordField, 
	              firstNameField, lastNameField, emailField, phoneField, 
	              address1Field, address2Field, cityField, stateField, zipField, countryField,
	              languageDropdown, favoriteCategoryDropdown, listOptionCheckbox,
	              bannerOptionCheckbox, saveAccountButton;

	    public registerpage(WebDriver driver) {
	        this.driver = driver;
	    }

	    public void openRegistrationPage() {
	        driver.get("https://petstore.octoperf.com/");
	        driver.findElement(By.linkText("Enter the Store")).click();
	        driver.findElement(By.xpath("//*[@id=\"MenuContent\"]/a[2]" )).click();
	        driver.findElement(By.xpath("//div[@id='Catalog']/a" )).click();
	    }

	    public void enterUserInformation(String username, String password, String repeatPassword) {
	        usernameField = driver.findElement(By.name("username"));
	        passwordField = driver.findElement(By.name("password"));
	        repeatedPasswordField = driver.findElement(By.name("repeatedPassword"));
	        
	        usernameField.sendKeys(username);
	        passwordField.sendKeys(password);
	        repeatedPasswordField.sendKeys(repeatPassword);
	    }

	    public void enterAccountInformation(String firstName, String lastName, String email, String phone, 
	                                        String address1, String address2, String city, String state, 
	                                        String zip, String country) {
	        firstNameField = driver.findElement(By.name("account.firstName"));
	        lastNameField = driver.findElement(By.name("account.lastName"));
	        emailField = driver.findElement(By.name("account.email"));
	        phoneField = driver.findElement(By.name("account.phone"));
	        address1Field = driver.findElement(By.name("account.address1"));
	        address2Field = driver.findElement(By.name("account.address2"));
	        cityField = driver.findElement(By.name("account.city"));
	        stateField = driver.findElement(By.name("account.state"));
	        zipField = driver.findElement(By.name("account.zip"));
	        countryField = driver.findElement(By.name("account.country"));
	        
	        firstNameField.sendKeys(firstName);
	        lastNameField.sendKeys(lastName);
	        emailField.sendKeys(email);
	        phoneField.sendKeys(phone);
	        address1Field.sendKeys(address1);
	        address2Field.sendKeys(address2);
	        cityField.sendKeys(city);
	        stateField.sendKeys(state);
	        zipField.sendKeys(zip);
	        countryField.sendKeys(country);
	    }

	    public void enterProfileInformation(String language, String category) {
	        languageDropdown = driver.findElement(By.name("account.languagePreference"));
	        favoriteCategoryDropdown = driver.findElement(By.xpath("//*[@id=\"Catalog\"]/form/table[3]/tbody/tr[2]/td[2]/select"));
	        listOptionCheckbox = driver.findElement(By.name("account.listOption"));
	        bannerOptionCheckbox = driver.findElement(By.name("account.bannerOption"));
	        
	        new Select(languageDropdown).selectByVisibleText(language);
	        new Select(favoriteCategoryDropdown).selectByVisibleText(category);
	        listOptionCheckbox.click();
	        bannerOptionCheckbox.click();
	    }

	    public void saveAccountInformation() {
	        saveAccountButton = driver.findElement(By.name("newAccount"));
	        saveAccountButton.click();
	    }
