package pageObjects;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class CarLoanPage {
    WebDriver driver;
    WebDriverWait wait;

    private By carLoanTab = By.xpath("//a[contains(text(),'Car Loan')]");
    private By loanAmountInput = By.id("loanamount");
    private By interestRateField = By.id("loaninterest");
    private By tenureInput = By.xpath("//div[@id='loantermslider']//span");

    public CarLoanPage(WebDriver driver) {
        this.driver = driver;
        this.wait = new WebDriverWait(driver, Duration.ofSeconds(10));
    }

    public void navigateToCarLoanPage() {
        wait.until(ExpectedConditions.elementToBeClickable(carLoanTab)).click();
    }

    public void enterLoanAmount(String amount) {
        WebElement loanAmount = wait.until(ExpectedConditions.visibilityOfElementLocated(loanAmountInput));
        loanAmount.sendKeys(Keys.CONTROL+"a");
        loanAmount.sendKeys(Keys.BACK_SPACE);
        loanAmount.sendKeys(amount);
    }

    public void enterInterestRate(String rate) {
    	
        WebElement InterestRate=  wait.until(ExpectedConditions.visibilityOfElementLocated(interestRateField));
        InterestRate.sendKeys(Keys.CONTROL+"a");
        InterestRate.sendKeys(Keys.BACK_SPACE);
        InterestRate.sendKeys(rate);
      }


    public void entertenureinput(String xOffset) {
        WebElement slider = wait.until(ExpectedConditions.elementToBeClickable(tenureInput));
        Actions actions = new Actions(driver);
        actions.dragAndDropBy(slider,90,0).perform();
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



import org.openqa.selenium.WebDriver;
import org.testng.Assert;

import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;
import pageObjects.CarLoanPage;

public class CarLoanEmiSteps {
	WebDriver driver=Hooks.driver;
	CarLoanPage carloanpage=new CarLoanPage(driver);
	@Given("I navigate to the Car Loan EMI page")
	public void i_navigate_to_the_Car_Loan_EMI_page() {
carloanpage.navigateToCarLoanPage();
	}
	
	@When("I enter Car Loan Amount as {string}")
	public void i_enter_Car_Loan_Amount_as(String amount) {
		 carloanpage.enterLoanAmount(amount);
	}
	
	@When("I enter Interest Rate as {string}")
	public void i_enter_Interest_Rate_as(String amount) {
		 carloanpage.enterInterestRate(amount);
	}

	@When("I set the Loan Tenure to {string} years using drag and drop")
	public void i_set_the_Loan_Tenure_to_years_using_drag_and_drop(String tenure) {
		 carloanpage.entertenureinput(tenure);
	}
	 @Then("I check and display Loan EMI, Total Interest Payable, and Total Payment")
	    public void iCheckAndDisplayLoanEMITotalInterestPayableAndTotalPayment() {
	        Assert.assertNotNull(carloanpage.getEMIResult());
	        System.out.println("emi amount is "+carloanpage.getEMIResult());
	        Assert.assertNotNull(carloanpage.getTotalInterest());
	        System.out.println("Total Interest is "+carloanpage.getTotalInterest());
	        Assert.assertNotNull(carloanpage.getTotalPayment());
	        System.out.println("Total Payment is "+carloanpage.getTotalPayment());
	    }
}



package pageObjects;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class PersonalLoanPage {
    WebDriver driver;
    WebDriverWait wait;

    private By personalLoanTab = By.xpath("//a[contains(text(),'Personal Loan')]");
    private By loanAmountInput = By.id("loanamount");
    private By interestRateSlider = By.xpath("//div[@id='loaninterestslider']//span");
    private By tenureInput = By.id("loanterm");

    public PersonalLoanPage(WebDriver driver) {
        this.driver = driver;
        this.wait = new WebDriverWait(driver, Duration.ofSeconds(10));
    }

    public void navigateToPersonalLoanPage() {
        wait.until(ExpectedConditions.elementToBeClickable(personalLoanTab)).click();
    }

    public void enterLoanAmount(String amount) {
        WebElement loanAmount = wait.until(ExpectedConditions.visibilityOfElementLocated(loanAmountInput));
        loanAmount.sendKeys(Keys.CONTROL+"a");
        loanAmount.sendKeys(Keys.BACK_SPACE);
        loanAmount.sendKeys(amount);
    }

    public void setInterestRate(String xOffset) {
        WebElement slider = wait.until(ExpectedConditions.elementToBeClickable(interestRateSlider));
        Actions actions = new Actions(driver);
        actions.dragAndDropBy(slider,125,0).perform();
    }

    public void enterLoanTenure(String tenure) {
        WebElement tenureField = wait.until(ExpectedConditions.visibilityOfElementLocated(tenureInput));
        tenureField.sendKeys(Keys.CONTROL+"a");
        tenureField.sendKeys(Keys.BACK_SPACE);
        tenureField.sendKeys(tenure);
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

import org.openqa.selenium.WebDriver;
import org.testng.Assert;

import pageObjects.PersonalLoanPage;

public class PersonalLoanEmiSteps {
    WebDriver driver = Hooks.driver;
    PersonalLoanPage personalLoanPage = new PersonalLoanPage(driver);

    @Given("I navigate to the Personal Loan EMI page")
    public void iNavigateToPersonalLoanEmiPage() {
        personalLoanPage.navigateToPersonalLoanPage();
    }

    @When("I enter Personal Loan Amount as {string}")
    public void iEnterPersonalLoanAmountAs(String amount) {
        personalLoanPage.enterLoanAmount(amount);
    }
    
    @When("I set the Interest Rate to {string} using drag and drop")
    public void i_set_the_Interest_Rate_to_using_drag_and_drop(String xOffset) {
    	  personalLoanPage.setInterestRate(xOffset);
    }
    @And("I set the Loan Tenure as {string} years")
    public void iSetTheLoanTenureAsYears(String time) {
        personalLoanPage.enterLoanTenure(time);
    }

    @Then("I validate and display Loan EMI, Total Interest Payable, and Total Payment")
    public void iValidateAndDisplayLoanEMITotalInterestPayableAndTotalPayment() {
        Assert.assertNotNull(personalLoanPage.getEMIResult());
        System.out.println("emi amount is "+personalLoanPage.getEMIResult());
        Assert.assertNotNull(personalLoanPage.getTotalInterest());
        System.out.println("Total Interest is "+personalLoanPage.getTotalInterest());
        Assert.assertNotNull(personalLoanPage.getTotalPayment());
        System.out.println("Total Payment is "+personalLoanPage.getTotalPayment());
    }
}




package stepdefinitions;

import io.cucumber.java.After;
import io.cucumber.java.Before;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import java.time.Duration;

public class Hooks {
    public static WebDriver driver;

    @Before
    public void setUp() {
       
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.get("https://emicalculator.net/");
    }

    @After
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}
