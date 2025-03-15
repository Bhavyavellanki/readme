package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ProductDetailsPage {
    WebDriver driver;
    WebElement productPrice, addToCartButton;

    public ProductDetailsPage(WebDriver driver) {
        this.driver = driver;
    }

    public String getProductPrice() {
        productPrice = driver.findElement(By.className("price"));
        return productPrice.getText();
    }

    public void addToCart() {
        addToCartButton = driver.findElement(By.id("add-to-cart-button-43"));
        addToCartButton.click();
    }
}
