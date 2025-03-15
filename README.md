 public boolean errorIsDisplayed() {
    	errorMessage = driver.findElement(By.xpath("//li[text()='Invalid username or password.  Signon failed.']"));
    	return errorMessage.isDisplayed();
    }
