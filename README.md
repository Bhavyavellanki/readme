public static ExtentReports extent;
    public static ThreadLocal<ExtentTest> logger = new ThreadLocal<>();

    static
    {
        extent = new ExtentReports("C:\\Users\\BHAVYA\\Desktop\\Selenium Prac\\Selenium demo\\Mock\\Reports\\UpdatedTestReport.html", true);
    }

    public static void startTest(String testName) 
    {
        logger.set(extent.startTest(testName));
    }

    public static void endTest() 
    {
        extent.endTest(logger.get());
        extent.flush();
    }
    @AfterSuite
    public void closeReport() 
    {
    	
    	extent.close();
    }
