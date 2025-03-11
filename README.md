WebElement element=driver.findElement(By.xpath("//span[text()='right click me']"));
Actions action=new Actions (driver);
ction.contextClick(element).perform();
WebElement element2=driver.findElement(By.xpath("//a[text()='jQuery Context Menu Demo Gallery']"));
action.doubleClick(element2).perform();
WebElement menu=driver.findElement(By.cssSelector(".context-menu-list"));
if(menu.isDisplayed()) {
System.out.println("Menu is displayed");
}
else {
System.out.println("menu is not displayed");
}
driver.quit();
