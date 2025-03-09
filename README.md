package jpetstoreUtility;

import java.io.File;
import java.io.IOException;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.testng.ITestResult;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.AfterSuite;
import org.testng.annotations.BeforeSuite;
import com.google.common.io.Files;
import com.relevantcodes.extentreports.ExtentReports;
import com.relevantcodes.extentreports.ExtentTest;
import com.relevantcodes.extentreports.LogStatus;

public class screenshottestReport extends jpetstorelog4j {
	public static ExtentReports extent;
	public static ExtentTest test; 
	public static WebDriver driver;
	@AfterMethod
	public void getResult(ITestResult result) throws IOException
	{
	if(result.getStatus() == ITestResult.FAILURE)
	{
	test.log(LogStatus.FAIL, "Test is failed");
	  File scrFile = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
	  Files.copy(scrFile, new File("C:\\Users\\Administrator\\Desktop\\Selenium\\Selenium demo\\jpetstore\\Screenshots\\failed" + result.getName() + ".jpeg"));
	}
	else if(result.getStatus() == ITestResult.SUCCESS)
	{
	test.log(LogStatus.PASS, "Test is pass");
	}
	}
	@BeforeSuite
	public void beforeSuite() 
	{
	extent = new ExtentReports ("C:\\Users\\Administrator\\Desktop\\Selenium\\Selenium demo\\jpetstore\\TestResults\\testreport.html", true);
	}
	@AfterSuite
	public void afterSuite() 
	{
	extent.flush();
	} 
}
package jpetstoreUtility;

import org.apache.log4j.Logger;

public class jpetstorelog4j {
static Logger log = Logger.getLogger(jpetstorelog4j.class.getName()); 


	public  void writeLog(String msg)

	{

		log.info(msg);

	}

}
