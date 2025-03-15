package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class HomePage {
    WebDriver driver;
    WebElement electronicsMenu, cellPhonesSubMenu, shoppingCartLabel;

    public HomePage(WebDriver driver) {
        this.driver = driver;
    }

    public String getPageTitle() {
        return driver.getTitle();
    }

    public void navigateToElectronicsCellPhones() {
        electronicsMenu = driver.findElement(By.linkText("Electronics"));
        electronicsMenu.click();
        cellPhonesSubMenu = driver.findElement(By.linkText("Cell phones"));
        cellPhonesSubMenu.click();
    }

    public boolean isShoppingCartEmpty() {
        shoppingCartLabel = driver.findElement(By.xpath("//span[contains(text(),'Shopping cart')]"));
        return shoppingCartLabel.getText().contains("Shopping cart (0)");
    }
}
