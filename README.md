# Mobile-App-Calculator
Mobile App project 
package MobileAppPackage;

import java.net.MalformedURLException;
import java.net.URL;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.remote.DesiredCapabilities;

import io.appium.java_client.AppiumDriver;
import io.appium.java_client.android.AndroidDriver;

public class APKinstall
{
	public static void main(String[] args) throws MalformedURLException, InterruptedException
		// TODO Auto-generated method stub
	{
		 DesiredCapabilities capabilities = new DesiredCapabilities();
	        capabilities.setCapability("platformName", "Android");
	        capabilities.setCapability("appium:deviceName", "Venkatemulator");
	        capabilities.setCapability("appium:automationName", "UiAutomator2");
	        capabilities.setCapability("appium:app", "C:\\Users\\91701\\Downloads\\Calculator_APK.apk");
	        capabilities.setCapability("appium:platformVersion", "13.0");

	        // For Default Android Calculator
	        capabilities.setCapability("appium:appPackage", "com.google.android.calculator");
	        capabilities.setCapability("appium:appActivity", "com.android.calculator2.Calculator");

	        // Start Appium Session
	        @SuppressWarnings("deprecation")
			URL url = new URL("http://127.0.0.1:4723/wd/hub");
	        AppiumDriver driver = new AndroidDriver(url, capabilities);
	        
	        // Wait for the app to load
	        Thread.sleep(3000);

	        // Perform 5 + 2 = 7 using correct element IDs
	        driver.findElement(By.id("com.google.android.calculator:id/digit_5")).click();
	        driver.findElement(By.id("com.google.android.calculator:id/digit_2")).click();
	        driver.findElement(By.id("com.google.android.calculator:id/op_sub")).click();
	        driver.findElement(By.id("com.google.android.calculator:id/digit_9")).click();
	        driver.findElement(By.id("com.google.android.calculator:id/digit_2")).click();
	        driver.findElement(By.id("com.google.android.calculator:id/eq")).click();
	        // Capture and Print Result
	        WebElement result = driver.findElement(By.id("com.google.android.calculator:id/result_final"));
	        System.out.println("Calculation Result: " + ((WebElement) result).getText()); // Should print "7"

	        // Close the App
	      //  driver.quit();
	    }
	}
