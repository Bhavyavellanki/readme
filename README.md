package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ElectronicsPage {
    WebDriver driver;
    WebElement smartphoneProduct;

    public ElectronicsPage(WebDriver driver) {
        this.driver = driver;
    }

    public void selectSmartphone() {
        smartphoneProduct = driver.findElement(By.xpath("//h2[@class='product-title']/a[contains(text(),'Smartphone')]"));
        smartphoneProduct.click();
    }

    public String getPageTitle() {
        return driver.getTitle();
    }
}
