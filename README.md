WebDriver driver;
    WebElement username,password,login, errormessage;
    public loginpage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String uname) {
    	username= driver.findElement(By.id("user-name"));
        username.sendKeys(uname);
       
    }

    public void enterPassword(String pword) {
        password = driver.findElement(By.id("password"));
        password.sendKeys(pword);
    }

    public void clickLoginButton() {
       login = driver.findElement(By.id("login-button"));
       login.click();
    }

    public boolean isErrorMessageDisplayed() {
    	errormessage = driver.findElement(By.cssSelector(".error-message-container"));
        return errormessage.isDisplayed();
    }

    public String getErrorMessage() {
        return errormessage.getText();
    }
