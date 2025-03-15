WebDriver driver;
    WebElement checkoutButton,clickconfirm,confirmmsg;
	public checkoutpage(WebDriver driver) {
		this.driver = driver;
	}
	public void clickContinue() {
		checkoutButton = driver.findElement(By.name("newOrder"));
		checkoutButton.click();
	}
	public void clickConfirm() {
		clickconfirm = driver.findElement(By.linkText("Confirm"));
		clickconfirm.click();
	}
	public boolean confirmmessage() {
		confirmmsg = driver.findElement(By.xpath("//li[text()='Thank you, your order has been submitted.']"));
		return confirmmsg.isDisplayed();
	}
