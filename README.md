 WebDriver driver;
    WebElement enterStore;

    public welcomepage(WebDriver driver) {
        this.driver = driver;
    }

    public void clickEnterStore() {
        enterStore = driver.findElement(By.linkText("Enter the Store"));
        enterStore.click();
    }
