package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;

public class HomePage {
    WebDriver driver;
    WebElement electronicsMenu, cellPhonesSubMenu, shoppingCartLabel, cartQuantity;

    public HomePage(WebDriver driver) {
        this.driver = driver;
    }

    public String getPageTitle() {
        return driver.getTitle();
    }

    public void navigateToElectronicsCellPhones() {
        electronicsMenu = driver.findElement(By.xpath("//ul[contains(@class,'top-menu')]//a[contains(text(),'Electronics')]"));
        cellPhonesSubMenu = driver.findElement(By.xpath("//ul[contains(@class,'top-menu')]//a[contains(text(),'Cell phones')]"));

        Actions actions = new Actions(driver);
        actions.moveToElement(electronicsMenu).perform();
        cellPhonesSubMenu.click();
    }

    public String getShoppingCartQuantity() {
        cartQuantity = driver.findElement(By.xpath("//span[@class='cart-qty']"));
        return cartQuantity.getText();
    }

    public boolean isShoppingCartEmpty() {
        return getShoppingCartQuantity().equals("(0)");
    }
}
