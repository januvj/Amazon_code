# Amazon_code
Amazon login and add to cart function
public class Launch_browser {
	public static void main(String[] args) throws InterruptedException, AWTException {
		System.setProperty("webdriver.chrome.driver",
				"C:\\Users\\Vijay\\eclipse-workspace\\Testng\\newdriver\\chromedriver.exe");
		WebDriver driver = new ChromeDriver();

		driver.get("https://www.amazon.in/");
		driver.manage().window().maximize();
		WebElement searchbox = driver.findElement(By.id("twotabsearchtextbox"));
		searchbox.sendKeys("iphone 14 plus 128gb purple");
		driver.findElement(By.id("nav-search-submit-button")).click();

		WebElement iphone = driver.findElement(By.xpath("//span[text()='Apple iPhone 14 Plus 128GB (Product) RED']"));
		iphone.click();

		Set<String> win = driver.getWindowHandles();
		Thread.sleep(2000);
		for (String st : win) {
			driver.switchTo().window(st);

		}

		WebElement gb = driver.findElement(By.xpath("(//p[@class ='a-text-left a-size-base'])[2]"));
		gb.click();
		Thread.sleep(2000);
		WebElement colour = driver.findElement(By.xpath("(//img[@class ='imgSwatch'])[2]"));
		colour.click();
		Thread.sleep(2000);

		WebElement click = driver.findElement(By.id("add-to-cart-button"));
		click.click();

		Thread.sleep(4000);
		WebElement cart = driver
				.findElement(By.xpath("(//input[@aria-labelledby='attach-sidesheet-view-cart-button-announce'])[1]"));
		cart.click();
		Thread.sleep(4000);

		WebElement dropdown = driver.findElement(By.xpath("//span[@class='a-button-text a-declarative']"));
		dropdown.click();
		
		Robot r = new Robot();
		r.keyPress(KeyEvent.VK_DOWN);
		r.keyRelease(KeyEvent.VK_DOWN);
		
		r.keyPress(KeyEvent.VK_ENTER);
		r.keyRelease(KeyEvent.VK_ENTER);
		


		WebElement proceed = driver.findElement(By.xpath("//input[@name='proceedToRetailCheckout']"));
		proceed.click();

	}
}
