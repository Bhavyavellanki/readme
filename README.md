package pageobjects;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class checkoutpage {
	WebDriver driver;
	WebElement cartlink,checkout,fname,lname,pin,continueButton,finish,confmessage;

    public checkoutpage(WebDriver driver) {
        this.driver = driver;
    }
    public void goToCart() {
    	cartlink = driver.findElement(By.className("shopping_cart_link"));
    	cartlink.click();    
    }
    public void clickCheckout() {
    	 checkout = driver.findElement(By.id("checkout"));
    	 checkout.click();
    }
    public void enterCheckoutDetails(String firstName, String lastName, String postalCode) {
    	fname = driver.findElement(By.id("first-name"));
    	fname.sendKeys(firstName);
	    lname=driver.findElement(By.id("last-name"));
	    lname.sendKeys(lastName);
	    pin = driver.findElement(By.id("postal-code"));
	    pin.sendKeys(postalCode);
    }
    public void completePurchase() {
    	continueButton = driver.findElement(By.id("continue"));
	    continueButton.click();
    	finish = driver.findElement(By.id("finish"));
    	finish.click();
    }
    public String getConfirmationMessage() {
    	confmessage = driver.findElement(By.className("complete-header"));
    	return confmessage.getText();
    }
}


