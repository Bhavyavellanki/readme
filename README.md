package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ShoppingCartPage {
    WebDriver driver;
    WebElement unitPrice, productName, quantity, checkoutButton, termsOfServiceCheckbox, termsWarningBox, closePopupButton;

    public ShoppingCartPage(WebDriver driver) {
        this.driver = driver;
    }

    public String getUnitPrice() {
        unitPrice = driver.findElement(By.xpath("//span[@class='product-unit-price']"));
        return unitPrice.getText();
    }

    public String getProductName() {
        productName = driver.findElement(By.xpath("//a[@class='product-name']"));
        return productName.getText();
    }

    public String getQuantity() {
        quantity = driver.findElement(By.xpath("//input[contains(@name,'itemquantity')]"));
        return quantity.getAttribute("value");
    }

    public void clickCheckout() {
        checkoutButton = driver.findElement(By.xpath("//button[contains(@id,'checkout')]"));
        checkoutButton.click();
    }

    public boolean isErrorMessageDisplayed() {
        termsWarningBox = driver.findElement(By.xpath("//div[@id='terms-of-service-warning-box']"));
        return termsWarningBox.isDisplayed();
    }

    public void closeWarningPopup() {
        closePopupButton = driver.findElement(By.xpath("//button[@class='ui-button ui-corner-all ui-widget']"));
        closePopupButton.click();
    }

    public void acceptTermsOfService() {
        termsOfServiceCheckbox = driver.findElement(By.xpath("//input[@id='termsofservice']"));
        termsOfServiceCheckbox.click();
    }
}
