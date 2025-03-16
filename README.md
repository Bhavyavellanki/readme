WebDriver driver;
	WebElement firstCat,addToCartButton,cartTable, title, description, price, image, availability;
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
	    public String getProductTitle() {
	        title = driver.findElement(By.xpath("(//div[@id='Catalog']//td)[3]"));
	        return title.getText();
	    }

	    public String getProductDescription() {
	        description = driver.findElement(By.xpath("//td[text()='Great for reducing mouse populations']"));
	        return description.getText();
	    }

	    public String getProductPrice() {
	        price = driver.findElement(By.xpath("//td[contains(text(),'$')]"));
	        return price.getText();
	    }

	    public boolean isProductImageDisplayed() {
	        image = driver.findElement(By.xpath("//img[@src='../images/cat2.gif']"));
	        return image.isDisplayed();
	    }

	    public String getProductAvailability() {
	        availability = driver.findElement(By.xpath("//td[contains(text(),'in stock')]"));
	        return availability.getText();
	    }
