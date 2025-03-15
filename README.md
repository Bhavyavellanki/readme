WebDriver driver;
	WebElement persian;
	
	public WebElement persiancatpresent() {
        return driver.findElement(By.xpath("//h2[text()='Persian']"));
        
    }

	public persiancatpage(WebDriver driver) {
		this.driver = driver;
	}
