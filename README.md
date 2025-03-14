public static void captureScreenshot(WebDriver driver, String testName) 
    {
        File srcFile = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
        String destPath = "C:\\Users\\BHAVYA\\Desktop\\Selenium Prac\\Selenium demo\\Mock\\Reports\\Screenshot" + testName + ".png";
        try 
        {
            Files.copy(srcFile, new File(destPath));
            ReportGenerator.logger.get().log(LogStatus.INFO, "Screenshot saved: ");
        } 
        catch (IOException e) 
        {
            e.printStackTrace();  
        }
    }
