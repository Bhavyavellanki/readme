import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.testng.Assert;

public class ContextMenuTest {
    public static void main(String[] args) {
        // Set up WebDriver (Ensure you have chromedriver.exe in your system path)
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();

        try {
            // Step 1: Navigate to the URL
            driver.get("https://swisnl.github.io/jQuery-contextMenu/demo.html");

            // Step 2: Validate page title
            String pageTitle = driver.getTitle();
            Assert.assertTrue(pageTitle.contains("jQuery contextMenu"), "Page title verification failed!");

            // Step 3: Perform double-click on the demo gallery
            WebElement demoElement = driver.findElement(By.xpath("//span[text()='right click me']"));
            Actions actions = new Actions(driver);
            actions.doubleClick(demoElement).perform();

            // Validation 2: Check if double-click action performed successfully
            // (This depends on the behavior after double-click, modify as needed)
            System.out.println("Double click action performed successfully");

            // Step 4: Perform right-click (context click)
            actions.contextClick(demoElement).perform();

            // Validation 3: Check if context click action worked
            WebElement contextMenu = driver.findElement(By.cssSelector(".context-menu-list"));
            Assert.assertTrue(contextMenu.isDisplayed(), "Context menu did not appear!");

            System.out.println("Right-click action performed successfully");

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Close the browser
            driver.quit();
        }
    }
}
