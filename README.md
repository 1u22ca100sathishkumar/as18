# as18
1. Selenium Program – Click "Add Textbox1" and check if button is disabled after 5 seconds

URL: https://www.hyrtutorials.com/p/waits-demo.html

Selenium Java Program
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class WaitDemo {

    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://www.hyrtutorials.com/p/waits-demo.html");

        // Click "Add Textbox1" button
        WebElement addTextbox1Btn = driver.findElement(By.id("btn1"));
        addTextbox1Btn.click();

        // Explicit Wait for 5 seconds until button gets disabled
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));
        wait.until(ExpectedConditions.not(ExpectedConditions.elementToBeClickable(addTextbox1Btn)));

        // Check if button is disabled
        if (!addTextbox1Btn.isEnabled()) {
            System.out.println("Button is disabled after 5 seconds: PASS");
        } else {
            System.out.println("Button is still enabled: FAIL");
        }

        driver.quit();
    }
}

✅ Explanation

WebDriverWait → Waits until a certain condition is met (here: button becomes not clickable).

ExpectedConditions.not(elementToBeClickable()) → Checks if the element is disabled.

isEnabled() → Returns true if the element is enabled, false if disabled.

2. Difference between Wait and Thread.sleep()
Feature	Wait (Explicit / Implicit)	Thread.sleep()
Nature	Dynamic / Conditional	Static / Fixed
Usage	Waits until a specific condition is met or timeout occurs	Pauses execution for a fixed time
Flexibility	Can wait less or more depending on condition	Always waits for specified time, even if not needed
Performance	Efficient	Inefficient if overused
Example	WebDriverWait	Thread.sleep(5000)
