package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ShoppingCartPage {
    WebDriver driver;
    WebElement shoppingCartLabel, checkoutButton, errorMessage, closePopupButton, termsOfServiceCheckbox;

    public ShoppingCartPage(WebDriver driver) {
        this.driver = driver;
    }

    public boolean verifyCartUpdated() {
        shoppingCartLabel = driver.findElement(By.xpath("(//span[@class='cart-label'])[1]"));
        return shoppingCartLabel.getText().contains("Shopping cart (1)");
    }

    public void goToCart() {
        shoppingCartLabel.click();
    }

    public void clickCheckout() {
        checkoutButton = driver.findElement(By.id("checkout"));
        checkoutButton.click();
    }

    public boolean isErrorMessageDisplayed() {
        errorMessage = driver.findElement(By.xpath("//p[text()='Please accept the terms of service before the next step.']"));
        return errorMessage.isDisplayed();
    }

    public void closeWarningPopup() {
        closePopupButton = driver.findElement(By.xpath("//button[@title='close']//span[1]"));
        closePopupButton.click();
    }

    public void acceptTermsOfService() {
        termsOfServiceCheckbox = driver.findElement(By.id("termsofservice"));
        termsOfServiceCheckbox.click();
    }
}
