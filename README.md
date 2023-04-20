## <pre> IT 314 - Software Engineering </pre> 
### Lab 8 : Unit Testing with JUnit
### Student Name : Harshkumar Metekl
### Student ID: 202001154

<h3 align="center" >
  <b>Lab 8 : Unit Testing with JUnit</b>
</h3>
<br/>
1. I created a new Java project in eclipse with name <b>Lab8</b> and created a package inside it with name <b>mypackage</b>

![1](https://user-images.githubusercontent.com/86399274/233324381-6e797841-b9d9-47dd-b7f8-68a998158092.png)

2.I then created a class with name <b>Boa</b> and then added the given code inside it.

![2](https://user-images.githubusercontent.com/86399274/233324479-bca275ec-e5bb-430f-89c8-5172aebf64ae.png)

3.Then I created a JUnit test file for the Boa Class with name <b>BoaTest</b>
```
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {
  @Test
  public void testIsHealthy() {
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());
    
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());
  }
  @Test
  public void testFitsInCage() {
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    Assert.assertFalse(smallBoa.fitsInCage(1));
    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    Assert.assertFalse(largeBoa.fitsInCage(10));
  }
}
```
![3_old](https://user-images.githubusercontent.com/86399274/233329626-67aa2e9f-152e-43a2-a15a-093fbe006ac9.png)



4.Then I modified the setUp method to initialize the variables.
```
public class BoaTest {
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    // write test methods here
}
```

5.Then I also implemented tests for the given two functions <b>testIsHealthy()</b> and <b>testFitsInCage()</b>.
![image](https://user-images.githubusercontent.com/86399274/233329827-e7370911-24ed-41ec-ac0f-d8efdef46bc6.png)

For testing thee fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6.Then I ran the Junit test file and all the tests are passed.There are no red bars in the output.
![image](https://user-images.githubusercontent.com/86399274/233329939-105c45be-7d78-44c1-b7d7-89a122f862bf.png)

It can be seen that 2 out of 2 test cases have been passed. 

7.Then I added a new method to the Boa class with name <b>lenghtInInches()</b> to get the length in inches.
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;
    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }
    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }
    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }
    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
![image](https://user-images.githubusercontent.com/86399274/233330562-330e761b-0328-4ac9-b73a-9edddf1b5fda.png)

As the length of the Boa is given in feet, to convert it into inches, I had multiplied length with 12 and returned the value.

8.Then I wrote another test case for this new method and ran the 3 test cases together. 
![image](https://user-images.githubusercontent.com/86399274/233330805-3d50672f-c814-44a7-be8b-a00e50bff12b.png)


Thus, test cases have been written for the given Boa class and all the three methods have been tested with required Junit test cases.
### Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
    private Boa jen;
    private Boa ken;
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
This new test case checks that the lengthInInches() method returns the expected value when called on each of the Boa objects created in the setUp() method. It uses the assertEquals() method to compare the expected value to the actual value returned by the lengthInInches() method. The @Test annotation indicates that this is a test method that should be run by JUnit.
</br>
