 WebDriver driver;
    WebElement usernameField, passwordField, signInButton, errorMessage;

    public Signinpage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String userId) {
        usernameField = driver.findElement(By.name("username"));
        usernameField.clear();
        usernameField.sendKeys(userId);
    }

    public void enterPassword(String password) {
        passwordField = driver.findElement(By.name("password"));
        passwordField.sendKeys(password);
    }

    public void clickSignIn() {
        signInButton = driver.findElement(By.name("signon"));
        signInButton.click();
    }
