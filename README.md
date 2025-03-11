import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import io.github.bonigarcia.wdm.WebDriverManager;

public class ContextMenuTest {
    public static void main(String[] args) {
        // Setup ChromeDriver automatically using WebDriverManager
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();

        try {
            // Test Step 1: Navigate to URL
            driver.get("https://swisnl.github.io/jQuery-contextMenu/demo.html");
            driver.manage().window().maximize();
            System.out.println("Step 1: Navigated to URL.");

            // Test Step 2: Validate page title
            String expectedTitle = "jQuery contextMenu";
            String actualTitle = driver.getTitle();
            if (actualTitle.contains(expectedTitle)) {
                System.out.println("Validation 1: Page title is valid - " + actualTitle);
            } else {
                System.out.println("Validation 1: Page title validation failed - " + actualTitle);
            }

            // Locate the button element
            WebElement button = driver.findElement(By.cssSelector(".context-menu-one.btn.btn-neutral"));

            // Initialize Actions class
            Actions actions = new Actions(driver);

            // Test Step 3: Perform double-click on the button
            actions.doubleClick(button).perform();
            System.out.println("Step 3: Double-click action performed.");

            // Validation for double-click (this site doesn't show any UI change for double-click, so we check action performed)
            System.out.println("Validation 2: Double-click action performed successfully (no visible UI change).");

            // Test Step 4: Perform right-click (context click)
            actions.contextClick(button).perform();
            System.out.println("Step 4: Right-click (context click) action performed.");

            // Validation for context click by checking if the context menu is displayed
            WebElement contextMenu = driver.findElement(By.cssSelector(".context-menu-list"));
            if (contextMenu.isDisplayed()) {
                System.out.println("Validation 3: Context menu displayed successfully after right-click.");
            } else {
                System.out.println("Validation 3: Context menu did not display after right-click.");
            }

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Close the browser
            driver.quit();
            System.out.println("Test execution completed and browser closed.");
        }
    }
}
