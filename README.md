# gitLearning
okumayı unutma
do not forget read me
remember read me
package org.example;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Main {
    public static void main(String[] args) throws InterruptedException {

        WebDriver driver = new ChromeDriver();
        driver.get("https://www.cheapflights.com");
        driver.manage().window().maximize();

        try {
            WebElement kalkis = driver.findElement(By.xpath("//div[@class='zEiP-formField zEiP-origin']"));
            kalkis.click();Thread.sleep(2000);
            WebElement kalkisIlGir = driver.findElement(By.xpath("//input[@type='text']"));
            for (int i=0; i<12; i++){
                kalkisIlGir.sendKeys(Keys.BACK_SPACE);//Thread.sleep(2000);
            }
            kalkisIlGir.sendKeys("Antalya",Keys.ENTER);Thread.sleep(2000);

            WebElement varis = driver.findElement(By.xpath("//div[@class='zEiP-formField zEiP-destination']"));
            varis.click();Thread.sleep(2000);
            WebElement varisIlGir = driver.findElement(By.xpath("//input[@type='text']"));
            varisIlGir.sendKeys("Adana",Keys.ENTER);Thread.sleep(2000);

            WebElement gidisTakvim = driver.findElement(By.xpath("//div[@class='cQtq-input cQtq-mod-responsive']"));
            gidisTakvim.click();Thread.sleep(2000);
            WebElement gidisTarihi = driver.findElement(By.xpath("//div[@aria-label='Monday December 25, 2023']"));
            WebElement donusTarihi = driver.findElement(By.xpath("//div[@aria-label='Wednesday January 24, 2024']"));
            gidisTarihi.click();Thread.sleep(2000);
            donusTarihi.click();Thread.sleep(2000);

            WebElement cabinClass = driver.findElement(By.xpath("//div[@class='zEiP-formField zEiP-traveler']"));
            cabinClass.click();Thread.sleep(2000);
            driver.findElement(By.xpath("//label[@class='Q9qx-label Q9qx-checked']")).click();Thread.sleep(2000);
            driver.findElement(By.xpath("/html/body/div[3]/div/div[2]/div[1]/div[5]/div/button[2]")).click();Thread.sleep(2000);
        }
        finally {
            driver.quit();
        }



        System.out.println("Hello world!");
    }
}

//burdan aşağısı cucumber feature dosyası
Feature: Login Feature
  In this test I am testing login

  Scenario: Valid username and valid password test
    Given User is on login page
    When User enters valid user
    And User enters valid user password
    And User click login button
    Then User should login to system

  Scenario: Valid username and invalid password test
    Given User is on login page
    When User enters valid user
    And User enters invalid user password
    And User click login button
    Then User should not login to system

  Scenario: Invalid username and valid password test
    Given User is on login page
    When User enters invalid user
    And User enters valid user password
    And User click login button
    Then User should not login to system

  Scenario: Invalid username and invalid password test
    Given User is on login page
    When User enters invalid user
    And User enters invalid user password
    And User click login button
    Then User should not login to system
