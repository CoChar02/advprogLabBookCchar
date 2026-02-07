# 500083 Lab Book

## Week 1 - Lab A

28 Jan 2026

### Q1. Hello World

**Question:**

Locate the Solution Explorer within Visual Studio and select the HelloWorld project.

Right click on this project and select Build. This should compile and link the project.

Now run the HelloWorld program.

Change between Debug and Release mode. Compile again and rerun the program.

**Solution:**

```c++
#include <iostream>

int main(int, char**) {
   std::cout << "Hello World" << std::endl;
   return 0;
}
```

**Test data:**

*Delete if not required.*

**Sample output:**

*Delete if not required.*

**Reflection:**

*Reflect on what you have learnt from this exercise.*

*Did you make any mistakes?*

*In what way has your knowledge improved?*

**Questions:**

*Is there anything you would like to ask?*

### Q2. Creating a new project
**Question**
Create a new Empty C++ Console project called Temperature by using the project application wizard. This is done by right clicking on the 500083-Lab-A solution in the Solution Explorer Window and selecting Add » New Project.

NB: Be careful to select a C++, Empty Project

Create a new cpp file within the temperature project by right clicking on the Temperature project in the Solution Explorer Window and select Add » Add New Item.

Write a program to input a Fahrenheit measurement, convert it and output a Celsius value. The conversion formula is

celsius = 5/9 * (fahrenheit-32)
NB: You may want to select the Temperature project as the default project; to do this right click on the Temperature project and select Set as Startup Project.

Also what happens if you dividing two integers?

**Solution**
```c++
#include <iostream>

int main()
{
    std::cout << "Fahrenheit to Celcius Calculator\nInput Fahrenheit temperature to convert: ";
    int fahrenheit;
    std::cin >> fahrenheit;
    double coefficient = (double)5 / 9;
    int offset = 32;
    double celcius = coefficient * (double)(fahrenheit - offset);
    std::cout << fahrenheit << " fahrenheit in celcius is: " << celcius << std::endl;
    
    return 0;
}
```
**Test Data**

42 Fahrenheit in Celcius is 5.5555...

**Sample Output**
```
Fahrenheit to Celcius Calculator
Input Fahrenheit temperature to convert: 42
42 fahrenheit in celcius is: 5.55556
```
<img width="1094" height="240" alt="image" src="https://github.com/user-attachments/assets/4b47b594-48f7-4bf8-a79f-7a205fc8eaa4" />

**Reflections**

I now understand how to code a simple program in C++ including taking user input, outputting variables to the console, and simple type casting.
When dividing two integers, you are returned with a truncated result of the input divison, for a relevant example 5/9 returns 0 when divided as integers, I made this mistake initially when writing the above piece of code, this then led to me including the type conversion to make the 5 into a double, allowing for the coefficient to be correctly calculated.

### Q3 Types

**Question**

Using the “Hello World” program as a starting point, write a program that prints out the size in bytes of each of the fundamental data types in C++.

Hint: Make use of the sizeof() operator, that returns the size of any data type.

Remember to include both the signed and unsigned versions of each data type.

**Solution**

```c++
#include <iostream>
using namespace std;

int main (int argc, char **argv) {

	cout << "Hello World" << endl;
	cout << "Size Of bool: " << sizeof(bool) << endl << endl;
	//Integers
	cout << "Size Of signed int: " << sizeof(int) << endl;
	cout << "Size Of unsigned int: " << sizeof(unsigned int) << endl << endl;
	
	cout << "Size Of signed short: " << sizeof(short) << endl;
	cout << "Size Of unsigned short: " << sizeof(unsigned short) << endl <<endl;

	cout << "Size Of signed long: " << sizeof(long) << endl;
	cout << "Size Of unsigned long: " << sizeof(unsigned long) << endl << endl;

	cout << "Size Of signed int32_t: " << sizeof(__int32) << endl;
	cout << "Size Of unsigned int32_t: " << sizeof(unsigned __int32) << endl << endl;

	cout << "Size Of signed int64_t: " << sizeof(__int64) << endl;
	cout << "Size Of unsigned int64_t: " << sizeof(unsigned __int64) << endl << endl;

	//Character types
	cout << "Size Of char: " << sizeof(char) << endl;

	cout << "Size Of char16_t: " << sizeof(char16_t) << endl;

	cout << "Size Of char32_t: " << sizeof(char32_t) << endl << endl;

	//Floating Point
	cout << "Size Of signed float: " << sizeof(float) << endl;
	cout << "Size Of unsigned float: " << sizeof(unsigned float) << endl << endl;

	cout << "Size Of signed double: " << sizeof(double) << endl;
	cout << "Size Of unsigned double: " << sizeof(unsigned double) << endl << endl;

	cout << "Size Of signed long double: " << sizeof(long double) << endl;
	cout << "Size Of unsigned long double: " << sizeof(unsigned long double) << endl << endl;


	return 0;
}

```
**Sample Output**

```
Hello World
Size Of bool: 1

Size Of signed int: 4
Size Of unsigned int: 4

Size Of signed short: 2
Size Of unsigned short: 2

Size Of signed long: 4
Size Of unsigned long: 4

Size Of signed int32_t: 4
Size Of unsigned int32_t: 4

Size Of signed int64_t: 8
Size Of unsigned int64_t: 8

Size Of char: 1
Size Of char16_t: 2
Size Of char32_t: 4

Size Of signed float: 4
Size Of unsigned float: 4

Size Of signed double: 8
Size Of unsigned double: 4

Size Of signed long double: 8
Size Of unsigned long double: 8
```

<img width="427" height="572" alt="image" src="https://github.com/user-attachments/assets/c420642a-faab-46fa-8d0a-0744d8a2db0e" />


**Reflections**

From my tests I can see the size of each of the fundamental data types in C++, in bytes. Through doing this I have learnt how the sizes of each datatype compare to eachother, for instance a short is expectedly shorter than an integer. I was able to make some interesting observations.

Signed and Unsigned data types are of the same length, this makes intuitve sense as the datatypes are represented the same way but unsigned datatypes omit the sign bit for a wider range of possible values.

I was also able to clearly see that all sizeofs matched up to expected byte lengths with two notable exceptions:

- sizeof unsigned double was equal to 4 instead of the expected 8. Through this I found out that the unsigned operator cannot be applied to floating point data types, and that the visual studio compiler was likely converting the 'unsigned double' into a standard unsigned int.
- Another anomaly i noticed was that the long datatype also had a size of 4 bytes, this was the same length as the standard integer. I found that this is likely due to how Microsoft and Visual Studio define the long datatype, where the c++ standard defines longs to be at least 32 bits, Microsoft have set both ints and longs to both be 32 bits, hence in my tests they evaluated to the same size. If i wished for a longer number I could instead use long long or the fixed length datatypes such as int64_t

### Question 4 Floating point precision

**Question**

In the lectures we discussed the precision of floating point numbers within C++, and how due to this precision the equality operator was unreliable.

Write a simple program that includes the lines:
```c++
double x = 10.0;
double y = 10.0;
if (x == y)
      cout << “X and Y are identical” << endl;
```
Did the program execute as expected?

Now try y = 20.0  / 2.0 and execute the program again.
Then try a more complex calculation for y e.g.
```c++
const double x = 100000.123456789;
const double a = 200000.123456789;
double y = (x + a) / x;
double z = 1.0 + (a / x);
if (y == z) 
   cout << “y and z are identical” << endl;
```
Now try different values for x and a

Printing out the values of x, y and z, may be useful in helping you form an opinion of what is happening.

Once you’re confident you understand the logic, investigate:

double z = x / y;
How small does y have to be before you get a “divide by zero” error? Does the value of x affect the result?

**Solution**

```c++
#include <iostream>
#include <iomanip>
#include <limits>
using namespace std;

int main()
{
    const double x = 100000.123456789;
    const double a = 200000.123456789;
    double y = (x + a) / x;
    double z = 1.0 + (a / x);
    //Output values
    cout << "x: " << x << " a: " << a << " y: " << y << " z: " << z << endl;
    //Output with precision
    cout << setprecision(17) << "x: " << x << " a: " << a << " y: " << y << " z: " << z << endl;
    if (y == z)
        cout << "y and z are identical" << endl;

    double absolute_minimum = numeric_limits<double>::denorm_min();
    cout << endl << setprecision(17) << "Minimum value of double: " << absolute_minimum << endl;
    //Anything lower than the denorm min results in a divide by 0

    double numerator = 1;
    double denominator = absolute_minimum/10;

    if (denominator == 0) {
        cout << "Divide by 0!" << endl;
    }
    double output = numerator / denominator;

    cout << endl << setprecision(15) << output;
    return 0;
}
```

**Output**
```
x: 100000 a: 200000 y: 3 z: 3
x: 100000.12345678901 a: 200000.12345678901 y: 2.999998765433634 z: 2.9999987654336344

Minimum value of double: 4.9406564584124654e-324
Divide by 0!

inf
```

<img width="850" height="129" alt="image" src="https://github.com/user-attachments/assets/11c84ae7-e66a-4cdc-a744-000a4a8674ba" />

**Reflections**

The First part of this task taught me to be careful with exact comparisons on floating point numbers. As my output shows, despite z and y being the same mathematically, computationally they can differ due to floating point errors. This is likely due to precision being lost when the large numbers are added together before divison occurs. As shown in the output where y is less accurate than z. In this case, z and y are only exactly equal when no precision is lost in the intermediary steps of either operation, for example when x is 100000.12345678901 and a is 300000.12345678901.

The second part of this task explored the minimum possible value for a double. I used the limits library to find the absolute minimum value of a double, noting that anything under this absolute minimum value would be evaluated as 0.0 instead. I noticed that instead of the program throwing a division by 0 error, the output would instead equate to 'inf'. This also happened when X was sufficiently large and Y sufficiently small comparative to eachother, this 'inf' would then occur when the result of the division was too large to properly represent in the double.

### Q5 C#/C++ Iteration Comparison (for loop)

**Question**

In the lectures we have looked at constructs and iterators.

Below is some C# code that calculates the factorial of a number (see https://www.mathsisfun.com/numbers/factorial.html for details of a factorial).
```c#
static void Main(string[] args)
{
   int factorialNumber = 5;
   int factorialTotal = 1;

   for(int n = 2; n <= factorialNumber; ++n)
   {
      factorialTotal *= n;
   }

   System.Console.WriteLine(factorialTotal);
}
```
Port the above C# code in to C++ using the provided Main.cpp file.

**Solution**

```c++
#include <iostream>
using namespace std;

int main (int argc, char **argv) {

	int factorialNumber = 5;
	int factorialTotal = 1;

	for (int n = 2; n <= factorialNumber; ++n) {
		factorialTotal *= n;
	}

	cout << factorialTotal << endl;
	return 0;
}
```

**Reflections**

I had no need to change syntax between the two implementations save for the console output, this leads me to understand that for loop synatax is exactly the same between c++ and c#

### Q6 C#/C++ Iteration Comparison (for loop)

**Question**
Using a while loop (or do-while loop), calculate the average value of values provided by the user from the console (cin). You should calculate the average after the user either enters a negative number or the user enters a non-number value (e.g. a letter).

The following C++ code will get an int value from the user.
```c++
cout << "Please enter an int value, then press Enter" << endl;
int n = 0;
cin >> n;
```

**Solution**

```c++
#include <iostream>
using namespace std;

int main(int argc, char* argv[])
{
	int input;
	int total = 0;
	int count = 0;
	//While input stream is valid (user inputs a number)
	while ((cin)) {
		cout << "Input a number:";
		cin >> input;
		if (input < 0 || !cin) { //Check if it was negative or not an integer
			break;
		}
		total += input;
		count++;

		cin.ignore(numeric_limits<streamsize>::max(), '\n');
	}
	//Calculate average
	cout << "Average = " << double(total) / count << endl;
}
```

**Test Input**

1,1,1,1,2,d
2,3,3,-1

**Output**
```
Input a number:1
Input a number:1
Input a number:1
Input a number:1
Input a number:2
Input a number:d
Average = 1.2
```

<img width="399" height="135" alt="image" src="https://github.com/user-attachments/assets/881b0c42-0f82-4275-87b6-0def54f9d6ed" />

```
Input a number:2
Input a number:3
Input a number:3
Input a number:-1
Input a number:Average = 2.66667
```

<img width="366" height="101" alt="image" src="https://github.com/user-attachments/assets/32eb5cc1-9849-482c-8431-714e65b5d305" />

**Reflection**

I have learnt that while loop syntax is the same as in C#, this led me to be immediately familiar with the loop syntax. This task also taught me how to read when the input stream is valid versus when it fails and allow me to construct a loop around this function. My function will exit the while loop when the user inputs either a negative integer or an input that fails to convert to an integer. While this was simple to code, I noticed that the program encounters a bug when entering input such as decimal numbers or even input such as 2b, the input stream will read the integer as valid then fail on the next iteration. This led me to include the line 
```c++
cin.ignore(numeric_limits<streamsize>::max(), '\n');
```
which clears the input stream after each iteration of the loop, this makes my program parse input such as 2b and 5.3 as valid inputs by truncating everything after the initial integer, by ignoring the rest of the stream we ensure that the bug does not occur on the next iteration of the loop when 'cin >> input' reads the input stream again.



