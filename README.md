WebDriver driver;
    WebElement productName, cat1,cat2, cartTable;

    public catscategorypage(WebDriver driver) {
        this.driver = driver;
    }

    public void navigateToCatsCategory() {
        driver.get("https://petstore.octoperf.com/actions/Catalog.action?viewCategory=&categoryId=CATS");
    }

    public boolean isCategoryDisplayed() {
        productName = driver.findElement(By.xpath("//h2[text()='Cats']"));
        return productName.isDisplayed();
    }

    public void selectManxCat() {
        cat1 = driver.findElement(By.linkText("FL-DSH-01"));
        cat1.click();
    }

    public void selectPersianCat() {
    	cat2 = driver.findElement(By.linkText("FL-DLH-02"));
        cat2.click();
}
