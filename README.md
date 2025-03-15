 WebDriver driver;
    WebElement smartphoneProduct;

    public ElectronicsPage(WebDriver driver) {
        this.driver = driver;
    }

    public void selectSmartphone() {
        smartphoneProduct = driver.findElement(By.linkText("Smartphone"));
        smartphoneProduct.click();
    }
