WebDriver driver;
    WebElement title,products,addtocart,cartbadge; 
    public productpage(WebDriver driver) {
        this.driver = driver;
    }

    public String getTitle() {
        title =  driver.findElement(By.className("title"));
    	return title.getText();
    }

    public int getProductCount() {
    	List<WebElement> products = driver.findElements(By.className("inventory_item"));
        return products.size();
    }

    public void addFirstProductToCart() {
    	addtocart = driver.findElement(By.xpath("//button[contains(text(), 'Add to cart')]"));
        addtocart.click();
    }

    public String getCartBadgeCount() {
    	cartbadge = driver.findElement(By.className("shopping_cart_badge"));
    	return cartbadge.getText();
    }
