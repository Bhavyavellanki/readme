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
  public class log4j {
	protected static Logger log = Logger.getLogger(log4j.class.getName()); 


	public  void writeLog(String msg)

	{

		log.info(msg);

	}
