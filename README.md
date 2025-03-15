WebDriver driver;
	private WebDriverWait wait;
    WebElement signInLink, searchBox, petImage, search,selectCat, welcomemsg, logo,searchresult;

    public homepage(WebDriver driver) {
        this.driver = driver;
    }

    public void clickSignIn() {
        signInLink = driver.findElement(By.linkText("Sign In"));
        signInLink.click();
    }

    public void searchForPet(String petName) {
        searchBox = driver.findElement(By.name("keyword"));
        searchBox.sendKeys(petName);
        WebElement search = driver.findElement(By.name("searchProducts"));
        search.click();
    }
    public void selectCat() {
    	selectCat = driver.findElement(By.xpath("//img[@src='../images/cats_icon.gif']"));
    	selectCat.click();
    }
    public void clickOnPetCategory(String petCategory) {
    	String xpathExpression = String.format("//img[contains(@src, '%s')]/parent::a", petCategory.toLowerCase());
        WebElement petImage = driver.findElement(By.xpath(xpathExpression));
        petImage.click();
    }
    public boolean welcomemsg() {
    	welcomemsg = driver.findElement(By.id("WelcomeContent"));
    	return welcomemsg.isDisplayed();
    }
    public boolean logo() {
    	logo = driver.findElement(By.xpath("//img[@src='../images/logo-topbar.svg']"));
    	return logo.isDisplayed();
    }
    public boolean isRedirectedToPage(String expectedURL) {
    		return driver.getCurrentUrl().contains(expectedURL);
    		}
    public boolean searchIsDisplayed() {
    	searchresult = driver.findElement(By.xpath("//td[text()='Manx']"));
    	return searchresult.isDisplayed();
    }
      
