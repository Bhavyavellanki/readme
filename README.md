import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import java.util.List;

public class JPetStoreAutomation {
    public static void main(String[] args) {
        // Set the path for the ChromeDriver
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        
        // Initialize WebDriver
        WebDriver driver = new ChromeDriver();
        
        try {
            // Step 1: Open the URL
            driver.get("https://petstore.octoperf.com/");
            
            // Step 2: Verify the welcome text
            WebElement welcomeText = driver.findElement(By.xpath("//h2[text()='Welcome to JPetStore 6']"));
            if (welcomeText.isDisplayed()) {
                System.out.println("Welcome text is present.");
            }
            
            // Step 3: Click on 'Enter the store' link
            driver.findElement(By.linkText("Enter the Store")).click();
            
            // Step 4: Verify navigation to the welcome page
            if (driver.getTitle().contains("JPetStore")) {
                System.out.println("Successfully navigated to the welcome page.");
            }
            
            // Step 5: Count the number of links on the page
            List<WebElement> links = driver.findElements(By.tagName("a"));
            System.out.println("Number of links on the page: " + links.size());
            
            // Step 6: Click on 'Dogs' link
            driver.findElement(By.xpath("//a[contains(text(),'Dogs')]")) .click();
            
            // Step 7: Verify the number of rows and columns in the table
            List<WebElement> rows = driver.findElements(By.xpath("//table/tbody/tr"));
            List<WebElement> cols = driver.findElements(By.xpath("//table/tbody/tr[1]/td"));
            System.out.println("Number of rows: " + rows.size());
            System.out.println("Number of columns: " + cols.size());
            
            // Step 8: Store the product ID of "Poodle"
            WebElement poodleIdElement = driver.findElement(By.xpath("//td[contains(text(),'Poodle')]/preceding-sibling::td[1]"));
            String poodleId = poodleIdElement.getText();
            System.out.println("Poodle Product ID: " + poodleId);
            
            // Step 9: Click on "K9-PO-02"
            driver.findElement(By.xpath("//a[contains(text(),'K9-PO-02')]")).click();
            
            // Step 10: Ensure the same product ID appears in the new page
            WebElement productIdVerify = driver.findElement(By.xpath("//td[contains(text(),'K9-PO-02')]"));
            if (productIdVerify.isDisplayed()) {
                System.out.println("Product ID matches");
            }
            
            // Step 11: Verify the price is $18.50
            WebElement priceElement = driver.findElement(By.xpath("//td[contains(text(),'$18.50')]"));
            if (priceElement.isDisplayed()) {
                System.out.println("Price is correctly displayed as $18.50");
            }
            
            // Step 12: Click on 'Add to Cart' button
            driver.findElement(By.xpath("//a[contains(text(),'Add to Cart')]")).click();
            
            // Step 13: Ensure the default quantity is 1
            WebElement quantityElement = driver.findElement(By.xpath("//input[@name='EST-16' and @value='1']"));
            if (quantityElement.isDisplayed()) {
                System.out.println("Default quantity is 1.");
            }
        } finally {
            // Close the browser
            driver.quit();
        }
    }
} 

public static void main(String[] args) {
    
    int num = 3553, reversedNum = 0, remainder;
    
    // store the number to originalNum
    int originalNum = num;
    
    // get the reverse of originalNum
    // store it in variable
    while (num != 0) {
      remainder = num % 10;
      reversedNum = reversedNum * 10 + remainder;
      num /= 10;
    }
    
    // check if reversedNum and originalNum are equal
    if (originalNum == reversedNum) {
      System.out.println(originalNum + " is Palindrome.");
    }
    else {
      System.out.println(originalNum + " is not Palindrome.");
    }
  }
}
