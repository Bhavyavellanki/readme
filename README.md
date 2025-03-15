WebDriver driver;
	    WebElement firstCat,addToCartButton,cartTable;
		public manxcatpage(WebDriver driver) {
			this.driver = driver;
		}
		public void selectFirstCat() {
	        firstCat = driver.findElement(By.linkText("EST-14"));
	        firstCat.click();
	    }

	    public void addToCart() {
	        addToCartButton = driver.findElement(By.xpath("//a[contains(text(),'Add to Cart')]"));
	        addToCartButton.click();
	    }

	    public boolean isProductInCart() {
	        cartTable = driver.findElement(By.linkText("EST-14"));
	        return cartTable.isDisplayed();
	    }
