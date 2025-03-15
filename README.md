WebDriver driver;
    WebElement addToCartButton,cartItem,removeButton,cartMessage,quantityField,updateCartButton;
    public shoppingcartpage(WebDriver driver) {
        this.driver = driver;
    }
    public void navigateToProductPage() {
        driver.get("https://petstore.octoperf.com/actions/Catalog.action?viewItem=&itemId=EST-1");
    }

    public void addProductToCart() {
        addToCartButton = driver.findElement(By.linkText("Add to Cart"));
        addToCartButton.click();
    }

    public boolean isProductInCart() {
        cartItem = driver.findElement(By.xpath("//*[@id=\"Cart\"]/form/table//td/a[text()='EST-1']"));
        return cartItem.isDisplayed();
    }

    public void removeItemFromCart() {
        removeButton = driver.findElement(By.xpath("//a[contains(text(),'Remove')]"));
        removeButton.click();
    }
    public boolean isCartEmpty() {
        cartMessage = driver.findElement(By.xpath("//b[contains(text(),'Your cart is empty')]"));
        return cartMessage.isDisplayed();
    }
    public void updateProductQuantity(String quantity) {
        quantityField = driver.findElement(By.xpath("//*[@id=\"Cart\"]/form/table/tbody/tr[2]/td[5]/input"));
        quantityField.clear();
        quantityField.sendKeys(quantity);
        updateCartButton = driver.findElement(By.name("updateCartQuantities"));
        updateCartButton.click();
    }

    public boolean isQuantityUpdated(String expectedQuantity) {
        WebElement updatedQuantity = driver.findElement(By.xpath("//*[@id=\"Cart\"]/form/table/tbody/tr[2]/td[5]/input"));
        return updatedQuantity.getAttribute("value").equals(expectedQuantity);
    }

    public void proceedToCheckout() {
        WebElement checkoutButton = driver.findElement(By.xpath("//a[contains(text(),'Proceed to Checkout')]"));
        checkoutButton.click();
    }

    public boolean isOnCheckoutPage() {
        return driver.getCurrentUrl().contains("Order.action");
    }
