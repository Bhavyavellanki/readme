package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ProductDetailsPage {
    WebDriver driver;
    WebElement productPrice, addToCartButton, shoppingCartLink, cartQuantity, productName;

    public ProductDetailsPage(WebDriver driver) {
        this.driver = driver;
    }

    public String getProductPrice() {
        productPrice = driver.findElement(By.xpath("//span[@itemprop='price' and contains(@class, 'price-value')]"));
        return productPrice.getText();
    }

    public void addToCart() {
        addToCartButton = driver.findElement(By.xpath("//input[contains(@id,'add-to-cart-button')]"));
        addToCartButton.click();
    }

    public String getCartQuantity() {
        cartQuantity = driver.findElement(By.xpath("//span[@class='cart-qty']"));
        return cartQuantity.getText();
    }

    public void goToCart() {
        shoppingCartLink = driver.findElement(By.xpath("//span[@class='cart-label' and contains(text(),'Shopping cart')]"));
        shoppingCartLink.click();
    }

    public String getProductName() {
        productName = driver.findElement(By.xpath("//h1[@itemprop='name']"));
        return productName.getText();
    }
}
