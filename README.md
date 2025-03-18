package pageObjects;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class HomeLoanPage {
    WebDriver driver;
    WebDriverWait wait;


    private By loanSlider = By.xpath("//div[@id='loanamountslider']");
    private By interestRateField = By.id("loaninterest");
    private By tenureField = By.id("loanterm");
    
    
    public HomeLoanPage(WebDriver driver) {
        this.driver = driver;
        this.wait =new WebDriverWait(driver,Duration.ofSeconds(10));
    }

    public void setLoanAmount(int amount) {
        WebElement slider = wait.until(ExpectedConditions.elementToBeClickable(loanSlider));
        Actions actions = new Actions(driver);
        actions.dragAndDropBy(slider,-160,0).perform();
    }

    public void enterInterestRate(String rate) {
    	
      WebElement InterestRate=  wait.until(ExpectedConditions.visibilityOfElementLocated(interestRateField));
      InterestRate.sendKeys(Keys.CONTROL+"a");
      InterestRate.sendKeys(Keys.BACK_SPACE);
      InterestRate.sendKeys(rate);
    }

    public void enterLoanTenure(String tenure) {
        WebElement LoanTenure=wait.until(ExpectedConditions.visibilityOfElementLocated(tenureField));
        LoanTenure.sendKeys(Keys.CONTROL+"a");
        LoanTenure.sendKeys(Keys.BACK_SPACE);
        LoanTenure.sendKeys(tenure);
    }

    public String getEMIResult() {
    	String emiamount=driver.findElement(By.id("emiamount")).getText();
    	return emiamount;
    }
    public String getTotalInterest() {
    	String totalInterest=driver.findElement(By.id("emitotalinterest")).getText();
    	return totalInterest;
    }

    public String getTotalPayment() {
        String totalpayment=driver.findElement(By.id("emitotalamount")).getText();
        return totalpayment;
    }
}



package stepdefinitions;




import io.cucumber.java.en.*;
import pageObjects.HomeLoanPage;

import org.junit.Assert;
import org.openqa.selenium.WebDriver;




public class HomeLoanEmiSteps {
    WebDriver driver=Hooks.driver;

        HomeLoanPage homeLoanPage = new HomeLoanPage(driver);
 
    @Given("I navigate to the Home Loan EMI page")
    public void i_navigate_to_home_loan_emi_page() {
    	
      System.out.println("user is on homeloanemipage");
    }

    @When("I set the Home Loan Amount to {string}")
    public void i_set_the_home_loan_amount_to(String amount) {
        homeLoanPage.setLoanAmount(Integer.parseInt(amount));
    }

    @And("I enter the Interest Rate as {string}")
    public void i_enter_the_interest_rate_as(String rate) {
        homeLoanPage.enterInterestRate(rate);
    }

    @And("I enter the Loan Tenure as {string} years")
    public void i_enter_the_loan_tenure_as(String tenure) {
        homeLoanPage.enterLoanTenure(tenure);
    }

    @Then("I verify and display Loan EMI, Total Interest Payable, and Total Payment")
    public void i_verify_and_display_loan_emi_total_interest_payable_and_total_payment() {
        Assert.assertNotNull(homeLoanPage.getEMIResult());
        System.out.println("emi amount is "+homeLoanPage.getEMIResult());
        Assert.assertNotNull(homeLoanPage.getTotalInterest());
        System.out.println("Total Interest is "+homeLoanPage.getTotalInterest());
        Assert.assertNotNull(homeLoanPage.getTotalPayment());
        System.out.println("Total Payment is "+homeLoanPage.getTotalPayment());
    }
}
