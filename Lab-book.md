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


## Week 2 - Lab B

### Question 1 The good ```>>``` Streaming Operator

**Question**

Add the following line of code below the #include.
```c++
using namespace std;
```
This allows us to use the namespace std without explicitly adding std:: before any object or function defined in that namespace.

Remove the std:: from the cin and cout and endl.

Your code should still compile and run.

Add a third variable that is a string type. You will need to add #include <string>.

Take a string value from the user after you take the float value (the user can enter something like 23  4.586  Hello into the console window).

Then output the string value to the console after you output the float value.

**Solution**

```c++
#include <iostream>
#include <string>
using namespace std;

int main(int argc, char* argv[])
{
	int i;
	float f;
	string s;
	// take an int and float from the console - separated by a space, e.g. "1 6.7 Hello"
	cin >> i >> f >> s;
	// output the int, float, and string to the console
	cout << "i=" << i << ", f=" << f << ", s=" << s << endl;
}
```

**Output**
```
1 6.7 Hello
i=1, f=6.7, s=Hello
```

<img width="944" height="128" alt="image" src="https://github.com/user-attachments/assets/b9fe0ab6-8282-4b0d-bcdb-d71463771d7d" />

**Reflection**

In this task I have learnt how to use the string datatype from the standard library in c++, I then utilised this string with the streaming operator to collect a string input from the user and output it back to the console.

### Question 2 The bad ```>>``` streaming operator

**Question**

The streaming operator >> can be used on most fundamental types and standard objects like string. However, it can lead to unexpected issues when storing values into an array.
```c++
#include <iostream>
using namespace std;

int main(int argn, char* argv[])
{
   char c[5];
   cin >> c;
   cout << "c=" << c << endl;
}
```
The above code will store characters from the console window into the char array called c.

Place a break point on the cout line of the code. Run the above program. In the console, enter the values 123 before selecting the return key.

In Visual Studio, select from the menu, Debug -> Windows -> Autos. This will allow you to inspect values and memory addresses of variables etc.

Click on the triangle next to the variable c, and you should see the following output: 

<img width="626" height="198" alt="image" src="https://github.com/user-attachments/assets/b6c99896-12c2-445e-aaf8-c4b6e6ebd2d6" />


You can see that this variable can hold 5 chars as we defined it to do. However, we are only using the first three and so we have the end of array character \0 so that the system knows we are not using the whole array. Continue to step threw the rest of the code so that you can see the output etc.

Run the program again, but this time enter the values 123456789 before selecting the return key. Look at the value of c in the Autos window and you may see only the first 5 values but your code has tried to enter all 9 values into our variable. Notice that we cannot see the \0 end of array character - it is there but it is further along in memory from the start of the array so we cannot see it in the Autos window. Continue to step throw your code and you should receive a Run-Time Check Failure that is alerting you of this issue.

In Visual Studio, change the build to Release and then select from the menu, Debug -> Start Without Debugging. The whole 9 values should now be outputted because release will blindly output from the start of the array until it reaches the end array character.

The >> streaming operator is great for storing values into different types, but it should be avoided to store values into an array.

Replace cin >> c with the following code:

cin.get(c, 5);
This code will store up to 4 values followed by the end of array character. Run your code as a normal Debug build and with the Debugger and inspect and document the values and see the output. get() is usually safer for storing multiple characters in an array that the >> operator.

**Solution**

```c++
#include <iostream>
using namespace std;

int main(int argn, char* argv[])
{
	char c[5];
	cin.get(c, 5);
	cout << "c=" << c << endl;
}
```

**Reflection**

<img width="845" height="680" alt="image" src="https://github.com/user-attachments/assets/40e95836-8bcc-42e6-a3aa-646c0722ecde" />

As shown from the above screenshot, the get function was much safer for inputting into a character array than the streaming operator.

This is because the streaming operator ```>>``` will read and place all incoming data into the array with no regard for the array size, this causes a potential overflow or memory issue as the end of array character is not where it is expected to be. This makes the streaming operator unsuitable for use in inputting into an array as it is easy to cause memory issues by providing too much input into the input stream. The streaming operator does, however, excel in assigning different data types on input from the input stream, due to handling things such as parsing and whitespace handling automatically, this makes ```>>``` appropriate for reading specific data fields such as seen in Q1 where different data types were parsed and saved from the input stream, deliminated by the whitespace between them.

The get function, on the other hand, may be more appropriate for inputting into a character array as the function will only read the provided number of characters from the input stream, including whitespace. This prevents the issues raised with the ```>>``` streaming operator as, so long as too many characters are not given as the length the function, the function will automatically stop reading and inputting into the array when the specified number of characters has been reached. This then ensures that there are no array memory issues caused by assigning too many characters into the array.
The Get function may not be as appropriate for different data types as the ```>>``` operator, this is due to it only reading characters from the input stream with no regard for parsing into other datatypes where that may be applicable, for example `56` would be read as two characters with values 53 and 54 respectively, whereas the streaming operator may instead be able read the input as a single number, 56, if it is expecting an integer input.


### Question 3 Assembly Language

**Reflection**

The debugger provides many tools for examining how the CPU executes the code that we write.
The disassembly window provides us with a line by line view of the assembly instructions generated for the written code, including relevant memory addresses, and instructions and allows the debugger to execute these instructions line by line

```
00007FF6138B23A4  mov         dword ptr [start],3
```

for example, this line demonstrates that when the instruction pointer reaches ```...23A4```, it should MOVE a double length word (32 bits) to the address specified by the variable [start], with the value being 3.

```
00007FF6138B23C0  cmp         dword ptr [count],0Ah  
00007FF6138B23C4  jge         main+5Dh (07FF6138B23DDh)
```

These lines tell the CPU to compare the value of the value in the memory address specified by the variable [count] to the constant 0Ah (10). 

The following instruction then tells the CPU to ```jump if greater or equal``` based on the result of the comparison. If the conditon was true (count is greater than or equal to 10), the instruction pointer jumps to the instruction at the specified address ```07FF6138B23DD```


The debugger also provides tools to view the registers in use by the program,

<img width="1831" height="621" alt="image" src="https://github.com/user-attachments/assets/7396c526-991b-4d13-86a1-8a42186568da" />

Here we can see that in these steps, some registers have changed values. 

Firstly, the instruction pointer register, RIP, was changed to ```...23D8```, this is instruction address of the line that the CPU has just finished executing. 
We can also see that the value of the address in RAX has been altered, this is due to the increment instruction telling the cpu to increase the value at the RAX register.
Because of this increment operation, the EFL register is also updated to display flag values for the output of the incrementation, the shown value of ```...0202``` means that this output was a non-zero positive integer.


<img width="1418" height="884" alt="image" src="https://github.com/user-attachments/assets/9eb2f443-f31c-4cdb-8e9c-38e92d8b3298" />


The debugger also allows us to see the data stack for the code we have written, by looking at the value of the stack pointer register (RSP), we can find where our variables are being held on the stack. This, as the above screenshot shows, allows us to read their values and see updates as they are changed as we step through the function. In the above screenshot the value 07 has been highlighted in red, showing that it has been changed, from the locals tab we can see that the ```count``` variable has been updated to be 7, thus we can note that the count variable is being stored at the data address ```...F5BE```.


## Week 3 - Lab C

### Q1. Passing Command Arguments

**Solution**
<img width="1345" height="678" alt="image" src="https://github.com/user-attachments/assets/4a26dc82-ca04-45d1-a23c-25b79809ede0" />

<img width="902" height="63" alt="image" src="https://github.com/user-attachments/assets/98321642-2d8f-4d59-ac63-912523cef87a" />

We can add command line arguments to a c++ program in visual studio by navigating to the project dropdown, clicking the Properties of the project and then navigating to the debugging page. We can then enter any desired command line arguments into the allocated space, deliminated by whitespace. This allows us to pass specific arguments to a program, in this case it is being used to specify file input and output filepaths. From the above screenshot we can see that the filenames have successfully been passed to the program.

### Q2. Copying a Text File

**Question**

Complete the functionality inside of the Copy(char filenamein[], char filenameout[]) function. You need to add code that will try to open a text file given by the filenamein array as the name of the input file. You need to add code to create and output file using the filenameout array as the name of the ouput file. Then you can add code that will take each char from the input file and put it in the output file.

Make sure that you check for the input and output files existence before trying to copy.

Test your code thoroughly, e.g. try providing filenames that do not exist.

**Solution**

```c++
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

/*
* Partially completed program
* The program should copy a text file
*
*/

bool Copy(char filenamein[], char filenameout[])
{
	string line;
	ifstream fileIn(filenamein); //Open input file
	if (fileIn.fail()) { //Check input file was successfully opened.
		cout << "Error Opening File, check file " << filenamein << " exists and has correct permissions." << endl;
		fileIn.close();
		return false;
	}
	ofstream fileOut(filenameout); //Create and check validity of output file
	if (!fileOut.is_open()) {
		fileOut.close();
		fileIn.close();
		cout << "Error creating or opening output file." << endl;
		return false;
	}
	while (getline(fileIn, line)) { // Loop through input file and copy line to output file.
		fileOut << line << endl;
	}
	fileOut.close();
	fileIn.close();
	return true;
}

int main(int argn, char* argv[])
{
	if (argn != 3) {
		cerr << "Usage: " << argv[0] << " <input filename> <output filename>" << endl;
		int keypress; cin >> keypress;
		return -1;
	}

	if (Copy(argv[1], argv[2]))
	{
		cout << "Copy successful" << endl;
	}
	else
	{
		cout << "Copy error" << endl;
	}

	system("PAUSE");
}
```

**Test Input**

<img width="779" height="182" alt="image" src="https://github.com/user-attachments/assets/a99a339c-c915-4420-9fb1-694a5f632cc8" />


<img width="318" height="145" alt="image" src="https://github.com/user-attachments/assets/840474e1-9c3d-4a6a-9b65-2a981021864c" />

Valid input filepath and file to be copied

--

<img width="586" height="92" alt="image" src="https://github.com/user-attachments/assets/16ca649f-8fbf-494c-87f4-ea699333962f" />

Invalid input file path.

**Output**

<img width="275" height="51" alt="image" src="https://github.com/user-attachments/assets/e7320895-46ea-40ee-9db8-72dd67706060" />



<img width="666" height="304" alt="image" src="https://github.com/user-attachments/assets/3604201d-ab7a-4f60-8296-24652784919e" />



<img width="536" height="144" alt="image" src="https://github.com/user-attachments/assets/55cfcb2c-c057-4b71-abf6-d8dc89b615ab" />


--

<img width="794" height="115" alt="image" src="https://github.com/user-attachments/assets/39e7806f-f646-44af-9b67-ddc886b153c5" />


**Reflection**

In this task I have learnt how to read in text file input and copy it into an output file, I have also learnt how to check if a file was successfully opened and the filesystem did not encounter an error such as the target file not existing or an issue with file accesss permissions. This process is similar to how file handling is handled in other languages i have used such as c#, though may require some additional manual checking to ensure that files exist and are valid. I also learnt that the output file stream will automatically create destination files if they do not exist, and overwrite them if they do in the default writing mode. If i wished to append to the file instead, it can be done as so:
```c++
//Default write/overwrite mode
ofstream fileOut(filenameout)
//Append mode
ofstream fileOut(filenameout, ios::app)
```

### Question 3

**Reflection**

<img width="616" height="310" alt="image" src="https://github.com/user-attachments/assets/6a4d9f20-48a3-4478-8c68-2453301596be" />


Using the disassembler discussed in the last lab we can see how functions are called and variables passed into memory. 
```
00007FF7C4712370  mov         dword ptr [rsp+10h],edx  
00007FF7C4712374  mov         dword ptr [rsp+8],ecx
```

First the initial values passed to the function are taken from registers ecx (a) and edx (b) and pushed to locations on the stack using an offset of the stack pointer (rsp).

```
00007FF7C4712378  push        rbp  
00007FF7C4712379  push        rdi
```

The base pointer (rbp) and Destination Index register (rdi) then have their values pushed to the stack, this keeps track of their initial values as these are supposed to non-volatile and should be the same when the program exits the function.

```
00007FF7C471237A  sub         rsp,0E8h
```

232 Bytes (0E8h) are then allocated on the stack starting from the stack pointer (rsp)

```
00007FF7C4712381  lea         rbp,[rsp+20h]
```

The new stack base pointer is then calculated by taking the value 32 bytes above the current stack pointer. The lea command takes this address and saves it into the base pointer register, allowing the function to keep track of its variables.

the remaining lines in the call section are related to the JustMyCode setting in visual studios debugger and are not relevant.

