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

### Q3. Types

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

### Q4. Floating point precision

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

### Q5. C#/C++ Iteration Comparison (for loop)

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

### Q6. C#/C++ Iteration Comparison (for loop)

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

### Q1. The good ```>>``` Streaming Operator

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

### Q2. The bad ```>>``` streaming operator

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


### Q3. Assembly Language

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


The debugger also allows us to see the data stack for the code we have written, by looking at the value of the stack pointer register (RSP), we can find where our variables are being held on the stack. This, as the above screenshot shows, allows us to read their values and see updates as they are changed as we step through the function. In the above screenshot the value 07 has been highlighted in red, showing that it has been changed, from the locals tab we can see that the ```count``` variable has been updated to be 7, thus we can note that the count variable is being stored near the data address ```...F5BE``` with an offset of 22 bytes.


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

### Q3. Assembly and Method calls

**Reflection**

<img width="522" height="263" alt="image" src="https://github.com/user-attachments/assets/6d7c7049-adf6-4da1-a59f-75a1c2a4f7c5" />



Using the disassembler discussed in the last lab we can see how functions are called and variables passed into memory. 
```
00DF2510  push        ebp  
00DF2511  mov         ebp,esp
```

The initial value of the stack base pointer, ebp is pushed to the stack, this preserves its original value as the calling function expects this value to be non-volatile and should remain the same when this function returns.

The value of the stack pointer is then moved to the base pointer, this sets our new base pointer and keeps track of the function memory frame.

```
00DF2513  sub         esp,0C0h
```

192 bytes are subtracted from the stack pointer, this defines our function frame size and makes room for local variables.

```
00DF2519  push        ebx  
00DF251A  push        esi  
00DF251B  push        edi
```

Initial values of ebx, esi and edi are pushed to the stack.

```
00DF251C  mov         edi,ebp  
00DF251E  xor         ecx,ecx  
00DF2520  mov         eax,0CCCCCCCCh  
00DF2525  rep stos    dword ptr es:[edi]
```

This defines a loop used by the debugger to fill the function frame with junk data, overwriting any previous data that may be present in the frame from previous operations, providing a clearer view of how memory is being stored and accessed in the stack at runtime.

the remaining lines in the call section are related to the JustMyCode setting in visual studios debugger and are not relevant.


<img width="1292" height="633" alt="image" src="https://github.com/user-attachments/assets/477e99fa-05d0-48fb-8b0b-f7259a975528" />


Using the register view, we can see the value at EAX here is ```00000014```


<img width="1916" height="615" alt="image" src="https://github.com/user-attachments/assets/60488a2a-0bbb-4fbd-82f6-8fb2f253c45f" />


Stepping through we can see that the value of EAX was pushed to the stack and now resides at address with value ```...F817 with an offset of 52 bytes (0x34h)```, so it is stored at `F84B`

Variables A and B are 32 bit integers, this can be seen from the memory stack trace such as 

```
0x00DDFD73  77 c0 d0 1f 61 19 33 6f 77 23 10 df 00 23 10 df 00 00 10 19 01 23 10 df 00 23 10 df 00 9c fd dd 00 d5 17 12 61 c0 d0 1f 61 77 f0 df 00 77 f0 df 00 0a 00 00 00 14 00 00 00  wÀÐ.a.3ow#.ß.#.ß.....#.ß.#.ß.œýÝ.Õ..aÀÐ.awðß.wðß.........
```

In this line we can see that B and A have been pushed to the stack as 4 bytes, with a (value of 10) represented as ```0a 00 00 00``` and the value of b (20) represented as  ```14 00 00 00``` just below it. Values on the stack are reversed, this is called little endian and stores the least significant byte at the lowest memory address. The actual memory addresses of these values would be ```0x00DDFD73``` plus their offset within the row, for the case of A: ```0x00DDFD73 + 49 (0x31h)```, hence A resides at ```0x00DDFDA4```, with B residing 4 bytes after that at ```0x00DDFDA8```


```c++
#include <iostream>
using namespace std;

int mymax(int a, int b)
{
	if (a > b)
		return a;
	else
		return b;
}

void threeArgs(char ch, __int64 lng, float flt) {
	cout << "ch= " << ch << ", long= " << lng << ", float= " << flt << endl;
	return;
}

int main(int, char**) {

	int a = 10;
	int b = 20;

	char ch = 'a';
	__int64 lng = 1200;
	float flt = 4.3;

	threeArgs(ch, lng, flt);

	int max = mymax(a, b);

	cout << "a=" << a << ", b=" << b << endl;
	cout << "max=" << max << endl;

	return 0;
}
```
<img width="952" height="144" alt="image" src="https://github.com/user-attachments/assets/c71f9f2f-4938-44d0-ba3d-53a9b97a0890" />


<img width="1882" height="544" alt="image" src="https://github.com/user-attachments/assets/ffee824d-02a9-4046-a2ed-c2af467cad16" />

4 byte float has been saved onto the stack with the value of ```9a 99 89 40```  (again note values are reversed on the stack (little endian)) to achieve this the compiler first pushes a dummy ecx value before overwriting it with the value from the xmm0 register.

<img width="1919" height="671" alt="image" src="https://github.com/user-attachments/assets/eb89b45d-8cd9-4bb1-983e-de208c920919" />

The 64 bit integer used has been stored on the stack as ```b0, 04, 00, 00, 00, 00, 00, 00``` (04b0h), this is achieved with the instructions

```
000D217C  mov         eax,dword ptr [ebp-2Ch]  
000D217F  push        eax  
000D2180  mov         ecx,dword ptr [lng]  
000D2183  push        ecx
```
this first moves the high bytes of the long into the stack using the eax register, before pushing the lower bytes into the stack using the ecx register.

<img width="1869" height="671" alt="image" src="https://github.com/user-attachments/assets/2f4ed7fb-6188-4bce-af26-db97e6ab2526" />

Finally the char has been pushed to the stack with the instructions 

```
000D2184  movzx       edx,byte ptr [ch]  
000D2188  push        edx
```

these, as expected, move the byte value at the variable address [ch] into the edx register then push it onto the stack, as seen in the above screenshot it resides just next to the long previously pushed.

## Week 4 - Lab D

### Q1. Linker Errors

**Question**
Describe what is required in the .h and .cpp files of a class so that you can define a constructor or method

**Reflection**
In C++ to define a method or constructor in a class we must utilise two files, the header file (```.h```) and the source file (```.cpp```).

```c++

#pragma once

class Grid
{
public:
	Grid();
	~Grid();

	void LoadGrid(const char filename[]);
	void SaveGrid(const char filename[]);

private:
	int m_grid[9][9];
};
```
In the header file (example above), we define the access level of members of the class, in this case we have four public methods and one private multi-dimensional array defining a 9x9 grid (```m_grid[9][9]```).
Our four public methods:
- ```Grid()```, this is the constructor, called when an instance of the class is instaniated.
- ```~Grid()```, this is the deconstructor, called when an instance of the class is destroyed.
- ```void LoadGrid(const char filename[])``` this is a method to be implemented which will take a filename as an array of characters, this method will load in data from the datastore at the designated path to our grid
- ```void SaveGrid(const char filename[])``` this is a method to be implemented which will take a filename as an array of characters, this method will save data to an external file at the designated path

```c++
#include "Grid.h"

Grid::Grid()
{
}

Grid::~Grid()
{
}
```

In the .cpp file (as shown above) we define the body and implementation of the methods declared in the header, we must also include the line 
```c++
#include Grid.h
```
in order to ensure that method signatures and definitions match what has been declared in the header file.

C++ uses header files in order to tell the compiler what a function does (and its relevant signature) without each file needing to know its direct implementation, this is good for encapsulation as well as cutting down on code reuse.

### Q2. Reading into Grid Class

**Question**
Implement the Grid::LoadGrid(const char filename[]) method in Grid.cpp. This method should follow the following pseudo code.

Create an input file stream from filename
for each y value from 0 to 8 inclusive
{
   for each x value from 0 to 8 inclusive
   {
      store next value from the input file stream into grid at x,y
   }
}
Close input file stream
You will need to include the fstream library in your Grid.cpp file.

After you have implemented this, step through this method to make sure that it correctly reads and stores the values of the grid file into m_grid

Add you code for method Grid::LoadGrid and describe how you implemented it

**Solution**

_Grid.h_
```c++

#pragma once

class Grid
{
public:
	Grid();
	~Grid();

	void LoadGrid(const char filename[]);
	void SaveGrid(const char filename[]);

private:
 	//Initialise member variables
	int m_grid[9][9] = {} //Initialises to 0s
	int gridYSize = 0;
	int gridXSize = 0;
};


```

_Grid.cpp_
```c++
#include "Grid.h"
#include <iostream>
#include <fstream>
using namespace std;

/*References
W3Schools (2026) C++ Array Size [Source code]. https://www.w3schools.com/cpp/cpp_arrays_size.asp [Accessed 25 Feb 2026].
*/

/// <summary>
/// Grid constructor, calculates Grid Y and Grid X size using the sizeof m_grid
/// </summary>
Grid::Grid()
{
	gridYSize = sizeof(m_grid) / sizeof(m_grid[0]);
	gridXSize = sizeof(m_grid[0]) / sizeof(m_grid[0][0]);
}

Grid::~Grid()
{
}

//Create an input file stream from filename
//for each y value from 0 to 8 inclusive
//{
//   for each x value from 0 to 8 inclusive
//   {
//      store next value from the input file stream into grid at x,y
//   }
//}
//Close input file stream

/// <summary>
///
/// </summary>
/// <param name="filename"></param>
void Grid::LoadGrid(const char filename[]) 
{
	ifstream inputStream(filename); //Create input file stream
	if (inputStream.fail())
	{ //Check input file was successfully opened.
		cout << "Error Opening File, check file " << filename << " exists and has correct permissions." << endl;
		inputStream.close();
		return;
	}

	for (int y = 0; y < gridYSize; y++) //for each y value (every row in the grid)
	{
		if (inputStream.fail()) { break; } //Failed input, we can just break out of loop
		for (int x = 0; x < gridXSize; x++) // for each x value (every column in the grid)
		{
			int value;
			if (!(inputStream >> value)) //Read next value from file, if this fails ran out of integers in the file, or encountered a non-integer value.
			{
				cout << "Error: Input file was too small or reader encountered a non-integer value" << endl;
				break;
			}
			m_grid[y][x] = value; //Set value in the grid to the read value
		}
	}
	//Close input file stream
	inputStream.close();
}
```

**Test Data**

_Grid1.txt_
```
1 2 3 4 5 6 7 8 9
2 3 4 5 6 7 8 9 1
3 4 5 6 7 8 9 1 2
4 5 6 7 8 9 1 2 3
5 6 7 8 9 1 2 3 4
6 7 8 9 1 2 3 4 5
7 8 9 1 2 3 4 5 6
8 9 1 2 3 4 5 6 7
9 1 2 3 4 5 6 7 8
```

**Output**

<img width="912" height="182" alt="image" src="https://github.com/user-attachments/assets/69491309-d6e9-4309-9d7f-9621250a55a4" />

**Reflection**

In this task I have used the skills I learnt in the previous lab (Lab C) to read values from a file at a specified filepath and put them into the 2d array defined in the Grid class.

To achieve this i followed the provided pseudocode with some additions to make my code slightly more robust.  

I first learnt how to calculate the length and rank of an array. Unlike in C# and other languages I have previously used, defining an array as ```m_grid[9][9]``` simply reserves space in memory contiguously (example the value at `m_grid[0][8]` would be stored next to the value at `m_grid[1][0]`).

<img width="1914" height="798" alt="image" src="https://github.com/user-attachments/assets/d9a2fe90-a492-4bbf-bcb5-42b8874bcbab" />

As seen from this capture of the memory when we have already stepped through the row and one column of the input, data for the array is being stored contiguously on the stack, with the expected values (highlighted in yellow) ``` 01 00 00 00 02 00 00 00 03 00 00 00 04 00 00 00 05 00 00 00 06 00 00 00 07 00 00 00 08 00 00 00 09 00 00 00``` occupying memory next to eachother, next to where ```9``` is stored in memory we can see the start of the second row, highlighted in red, ```02 00 00 00 03 00 00 00```.
From this I can see that the array is 81 contiguous 4 byte integers, c++ accesses each of these integers by adding the offset from the start of the array multiplied by the size of the datatype, in this case the memory location of the array begins at ```0x000000415E6FF444 + 44bytes (0x2C) -> 0x000000415E6FF470``` and each element of the array can be retrieved through
```base address + ((y * number of columns) + x) * size of data```
Because data is stored contiguously, we could also find the same addresses by accessing the memory through
```base address + (z * size of data)``` where `z` is any number 0> = z > (number of rows * number of columns)

Using a concrete example, lets look for m_grid[1,1] which should be the `03 00 00 00` that was just read from the file.
```
using m_grid[y][x]
m_grid[1][1]
0x000000415E6FF470
 
((y * number of columns) + x) -> ((1 * 9) + 1) = 10

10 * size of data -> 10 * 4 = 40 bytes (0x28h)

so:
0x000000415E6FF470 + 0x28h = 0x000000415E6FF498

using m_grid[z]
1,1 is the element at the 10th position (0indexed)
m_grid[10]
0x000000415E6FF470 + (10 * size of data) -> 0x000000415E6FF470 + (10 * 4)

so:
0x000000415E6FF470 + 0x28h = 0x000000415E6FF498

As we can see, both methods resolve to the same calculation and find the same memory address
```

These can then be verified using the screenshot to see that ```03 00 00 00``` was indeed stored at ```0x000000415E6FF498``` (29 bytes after ```0x000000415E6FF47B```)

Also highlighted in the screenshot are the calculated GridYSize and GridXSize variables being stored in memory, as shown they both have a value of ```09 00 00 00```

All this to say that, unlike other languages I have used, arrays declared like ```int[9][9]``` in c++ are low level objects, they are not contained within wrapper classes or objects that allow you to easily access properties such as length, rank, and do not have any built in methods.

My code for the grid loading also includes some validation to ensure that the file was opened properly, exiting early if the input stream fails to open. This code snippet was taken from my work in the previous lab and notifies the user if the filepath was incorrect or the file was otherwise unable to be opened.

Finally, in double nested loop we use the size fields set in our constructor define the amount of times we should enter the loop, ensuring that we will read a value from the input file for each integer in the input array. In this loop I ensure that the data being read is valid, and the end of file has not been reached using the block 

```c++
	int value;
	if (!(inputStream >> value)) //Read next value from file, if this fails ran out of integers in the file, or encountered a non-integer value.
	{
		cout << "Error: Input file was too small or reader encountered a non-integer value" << endl;
		break;
	}
	m_grid[y][x] = value; //Set value in the grid to the read value
```

This loop interior defines an integer that the inputStream will read into, the stream then reads into the integer. Afterwards, the fail state of the inputStream is evaluated, if it has failed it means that we have reached the EoF or the input stream encountered something it could not parse as an integer, in either of these cases the user is told of an error and the loop exits early.

If the loop did not exit early, the grid position of [y][x] is filled with the value read from the stream.


Because of how the ifstream ``>>`` works, we can populate the grid with any arrangement of numbers in the grid file so long as there are enough to populate the grid. Because ``>>`` ignores whitespace, line breaks, and tabs we can read a valid grid from input such as
_Grid2.txt_
```
1 2 3 4 5 6 7 8 9 2 3 4 5 6 7 8 9 1 3 4 5 6 7 8 9 1 2 4 5 6 7 8 9 1 2 3 5 6 7 8 9 1 2 3 4 6 7 8 9 1 2 3 4 5 7 8 9 1 2 3 4 5 6 8 9 1 2 3 4 5 6 7 9 1 2 3 4 5 6 7 8
```
Grid2 stores the same information as Grid1 but with all data on the same line
<img width="937" height="677" alt="image" src="https://github.com/user-attachments/assets/25685475-44de-4b27-bb8c-8a1752d5838a" />

As seen, the output is the same as with _Grid1.txt_

### Q3. Saving the Grid

**Question**

Implement the SaveGrid(const char filename[]) method. This method will save the values of m_grid in a similar format to that of the Grid1.txt file. Please use another name for the output file so that your Grid1.txt file is not overwritten.

**Solution**
```c++
void Grid::SaveGrid(const char filename[]) 
{
	ofstream outputStream(filename, ios::out); //Open in write/overwrite mode
	if (!outputStream.is_open()) //Check file was able to be opened
	{
		outputStream.close();
		cout << "Error creating or opening output file." << endl;
		return;
	}

	for (int y = 0; y < gridYSize; y++) 
	{
		for (int x = 0; x < gridXSize; x++) 
		{
			outputStream << m_grid[y][x]; //Write value to file
			if (x == gridXSize - 1) //If last value on the row
			{
				outputStream << endl; //insert end of line
			}
			else
			{
				outputStream << ' '; //else add whitespace
			}
		}
	}

	outputStream.close();
}
```
**Test Data**

m_grid[9][9] with values
```
1 2 3 4 5 6 7 8 9
2 3 4 5 6 7 8 9 1
3 4 5 6 7 8 9 1 2
4 5 6 7 8 9 1 2 3
5 6 7 8 9 1 2 3 4
6 7 8 9 1 2 3 4 5
7 8 9 1 2 3 4 5 6
8 9 1 2 3 4 5 6 7
9 1 2 3 4 5 6 7 8
```

**Output**

<img width="285" height="257" alt="image" src="https://github.com/user-attachments/assets/dbd29b5c-0815-4c2a-b09c-4b547d3927dc" />


**Reflection**

To implement the SaveGrid method I used the methods I first opened a file output stream, 
```c++
ofstream outputStream(filename, ios::out); //Open in write/overwrite mode
```
The Out file stream was opened in write/overwrite mode (File writing modes discussed and explored in the previous lab), this ensured that only the data that had specifically been written into the fileStream by the program would be in the output file.

```c++
	if (!outputStream.is_open()) //Check file was able to be opened
	{
		outputStream.close();
		cout << "Error creating or opening output file." << endl;
		return;
	}
```

Taking another lesson from the previous lab, I included the check to ensure that the output file was successfully created and opened, telling the user if an error had occured and the file could not be opened.

```c++
	for (int y = 0; y < gridYSize; y++) 
	{
		for (int x = 0; x < gridXSize; x++) 
		{
			outputStream << m_grid[y][x]; //Write value to file
			if (x == gridXSize - 1) //If last value on the row
			{
				outputStream << endl; //insert end of line
			}
			else
			{
				outputStream << ' '; //else add whitespace
			}
		}
	}
```

Finally I loop through the grid using the previously discussed grid size fields, at each iteration of the loop I write the value in the grid at that position to the file then determine if this is the last value in this row and insert an endline, otherwise i deliminate between values with whitespace. This check is ultimately inconsequential and I could have just as easily done 

```c++
	for (int y = 0; y < gridYSize; y++) 
	{
		for (int x = 0; x < gridXSize; x++) 
		{
			outputStream << m_grid[y][x] << ' ';
		}
		outputStream << endl;
	}
```

This however would add an extra whitespace character at the end of each line which I preferred to not include, this may matter for file handling that is more character sensative to format or whitespace, such as when reading char by char.


### Q4. Pointers - Basics

**Question**

The program initializes two integer variables a and b, with the values 10 and 20 respectively. A pointer p is initialized to point at a.

Compile and run the program.

Add a line of code, at the position indicated by the comment, to assign the value of 100 to a, by using only the pointer p.

Run the code to check the output.

Now set a breakpoint at the line

int a = 10;
Run the code to the breakpoint, then single-step through the code whilst looking at the variables in the Local window.

Notice how a and b are initialized with values 10 and 20, and that pointer p is assigned a hexadecimal value. This value is the memory location of a.

Open a Memory window. Copy the value of p into the address field of the Memory window and confirm that you are looking at variable a in memory.

**Solution**

```c++
void functionA() {
	int a = 10;
	int b = 20;
	int *p = &a;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;

	*p = 100; //Change A through the pointer

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
}
```

**Output**

<img width="110" height="94" alt="image" src="https://github.com/user-attachments/assets/b45288b4-d232-4f43-8b79-ee3f37530d55" />

**Reflection**

In this task I have initialised an integer pointer with the value of variable a's memory address, I then used this pointer to change the value at the memory address it is pointing at, in this case this changed the value of variable a.

```c++
*p = 100;
```

<img width="1897" height="788" alt="image" src="https://github.com/user-attachments/assets/a5c21e55-8808-482c-9fa8-4d4cef0793c0" />


Here we can see the memory addresses that have been stored in the pointers,
We can see that the value of `a` has been stored at address ```0x000000019e0ff554``` and the value of `b` has been stored at ```0x000000019e0ff574```

<img width="1417" height="122" alt="image" src="https://github.com/user-attachments/assets/1448d2bf-123b-4219-9456-7b475caf83f7" />

Taking a closer look at the memory stack, we can see that `a` (highlighted in pink and stored with value `0a 00 00 00`) is on the row starting with ```0x000000019E0FF530``` and has an offset of `36 bytes (0x24h)`, giving it an address of ```0x000000019E0FF554```, this matches exactly to what our pointer said as expected. 

We can also see that this holds true for `b` (highlighted in orange, and stored with value `14 00 00 00`) which is on the row starting with ```0x000000019E0FF567``` and has an offset of `13 bytes (0x0Dh)` giving it an address of ```0x000000019E0FF574```, again matching exactly to the expected value from the pointer.

We can also see the pointers themselves on the stack, with `*p` being highlighted in yellow and `*q` being highlighted in red.
I can see that these pointers are being stored in 8 bytes on this 64bit build

`*p` has a value of `54 f5 0f 9e 01 00 00 00`, which when flipped to account for little endian encoding yields `00 00 00 01 9e 0f f5 54` -> `0x000000019E0FF554` which is of course our memory address of `a`!
The same is true for `*q` which has a value of `74 f5 0f 9e 01 00 00 00`, flipped becomes `00 00 00 01 9e 0f f5 74` -> `0x000000019E0FF574` the memory address of `b`

<img width="1421" height="453" alt="image" src="https://github.com/user-attachments/assets/3e6aebbe-0c67-4c6f-a1ca-db83470dfe68" />

As we move through the program, the value of `a` is changed through the pointer `*p`, this has been shown in memory above, with the value of `a` being changed to `64 00 00 00` (0x64h) which is 100 in decmial as stated in the program.


### Q5. Pointers - False assumptions

**Question**

Comment out the call to functionA and uncomment the call to functionB.
```c++
void functionB() {
   int a = 10;
   int b = 20;
   int c = 30;
   int *p = &b;

   cout << "a= " << a << endl;
   cout << "b= " << b << endl;
   cout << "c= " << c << endl;

   *p = 100;

   cout << "a= " << a << endl;
   cout << "b= " << b << endl;
   cout << "c= " << c << endl;
}
```
Compile and run the program.

Observe the result.

Now we’ll attempt to do a quick "hack" and advance the pointer 4 bytes in memory from the location of variable b to the location of variable c

After line
```c++
*p = 100;
```
Add
```c++
p++;
*p = 200;
```
Compile and run the program.

Is this what you expected?

Set a breakpoint and single-step through the code whilst observing the Locals window.

The pointer does get advanced by 4 bytes, but the memory location is invalid. Just because we list variables a, b, and c sequentially in our programme, does not guarantee that the compiler places them contiguously in memory.

If you want to do this sort of pointer arithmetic then you need to guarantee the memory layout. Arrays are a way to achieve this. We’ll look at these later in the module.

For now, just be careful using pointer arithmetic. This time we were lucky and the C++ run time checking detected the error for us. You cannot rely on the run time finding more complex errors.


**Solution**

```c++

void functionB() {
	int a = 10;
	int b = 20;
	int c = 30;
	int *p = &b;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;

	*p = 100;
	p++;
	*p = 200;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;
}
```

**Output**

<img width="638" height="275" alt="image" src="https://github.com/user-attachments/assets/74403796-caf4-48cd-9fd8-9e3847eca742" />

**Reflection**

As shown from the output, when executing this method an exception is thrown due to the memory around the variable `b` being corrupted, lets take a look at this happening on the stack.

<img width="1420" height="286" alt="image" src="https://github.com/user-attachments/assets/4e6d0e78-6ea1-4472-a0fb-dba7a23c0ccc" />

`a`, `b`, and `c` on the stack, as we can see unlike the array data that was discussed in Q2, the variables here are not contiguous in memory, there is a gap of "junk" data between each of the variables, this junk data is there to ensure that the stack and variables within the stack have proper alignment, for instance each function must be aligned to 16byte intervals and the induvidual integer variables would then be aligned to 4 byte intervals. Despite `a`,`b`, and `c` being the same size, they are not stored contiguously on the stack in order to ensure proper alignment of other variables when accounting for other data that will be stored in the stack memory during runtime.

<img width="1422" height="20" alt="image" src="https://github.com/user-attachments/assets/e05f7e16-dd40-4127-ab48-8dc14b3a0b36" />

`*p` can be seen on the stack with value of `34 fb 4f 87 33 00 00 00` corresponding to memory address `00000033874FFB34`, lets monitor its value as we step through.

<img width="544" height="467" alt="image" src="https://github.com/user-attachments/assets/d510be09-f916-4934-b74d-ecd346e27a2e" />

variable `b` was succesfully updated using the pointer `*p`.

<img width="923" height="394" alt="image" src="https://github.com/user-attachments/assets/ece074e7-69db-4401-acd5-9adc7b11eb68" />

<img width="1408" height="35" alt="image" src="https://github.com/user-attachments/assets/f848aae2-a48a-4dc9-9892-235318327e02" />

`*p` has had its value updated to `38 fb 4f 87 33 00 00 00`, corresponding to memory address `00000033874FFB38`, taking a look at this address in memory, we can see that it is currently filled with junk data, highlighted in blue in the second image.


<img width="1415" height="478" alt="image" src="https://github.com/user-attachments/assets/5c23247f-07cf-4e84-a6bc-e3dde04daed4" />

As we can see, with `*p` pointing at memory that is currently being used for alignment when we update the value at the address that `*p` is pointing at we will be updating/overwriting invalid memory, as shown above where the value at address `00000033874FFB38` has been updated to `c8 00 00 00` (0xc8h / 200d).

<img width="1417" height="556" alt="image" src="https://github.com/user-attachments/assets/3d6ae28d-f2e1-4c55-b0d4-9b7f608971d1" />

As we step out of the function we can see that the stack corruption error around variable `b` has confirmed our findings.

### Q6. Pointers - The crash

**Question** 
Comment out the call to functionB and uncomment the call to functionC.

Compile and run the program.

The program crashes, why?

Set a breakpoint at line
```c++
unsigned int a = 0x00ff00ff;
```
Single-step through the code and determine the reason for the crash.

The Windows operating system attempts to prevent applications from damaging other applications. This error message is from Windows telling you that your code has attempted to access a memory location outside of its permitted memory footprint.


**Solution**

void functionC() {
	unsigned int a = 0x00ff00ff;
	unsigned int *p = (unsigned int *)a;

	*p = 999;
}

**Output**

<img width="739" height="292" alt="image" src="https://github.com/user-attachments/assets/1480a848-ce1b-4efe-a7b2-18915ba2077a" />

**Reflection**

When the above code is executed it causes a write access violation crash.
The reasoning for this is straightforward when we take a look at the ```functionC```

```c++
void functionC() {
	unsigned int a = 0x00ff00ff;
	unsigned int *p = (unsigned int *)a;

	*p = 999;
}
```

<img width="467" height="321" alt="image" src="https://github.com/user-attachments/assets/3b697cac-4775-40a0-b9a3-57d1fbde3344" />

<img width="1399" height="511" alt="image" src="https://github.com/user-attachments/assets/c9e43023-22db-493f-a5a3-a02e7faaf584" />

As we step through the function we can see that when the pointer `*p` is being intialised it is given not the memory address of `a` but instead the value of `a` Cast to an unsigned int pointer. This causes the program to assign `0x00ff00ff` to `*p` as a memory location. As such, when we assign a value through `*p`, the program attempts to write at memory address `0x00ff00ff` as this is what is referenced by the pointer `*p`. This is outside of the permitted memory footprint and causes the access violation crash.

### Q7. Pointers - Pointers to pointers

**Question**

<img width="2151" height="680" alt="image" src="https://github.com/user-attachments/assets/13fba8f8-2965-4d17-aa78-351fb0610e7c" />

Add code, at the position identified by the comment, to implement the above pointer chain.

You will need to declare two new pointers p and q.

Then add the code to change the value of x by using only pointer p.

Compile and run the program. Checking your solution with the debugger and disassembler.

**Solution**

```c++
void functionD() {
	double x = 3.14;

	cout << "x= " << x << endl;

	double *q = &x; //Declare double pointer *q with address at &x
	double **p = &q; //Declare double pointer pointer **p with address at &q

	**p = 6.28; //Update the value of at the address referenced by **p, follows chain p -> q -> x

	cout << "x= " << x << endl;
}
```
**Output**

<img width="1023" height="68" alt="image" src="https://github.com/user-attachments/assets/7049411c-2b74-4b49-a7e0-963bd7d7ed50" />


**Reflection**

<img width="614" height="126" alt="image" src="https://github.com/user-attachments/assets/12b8760c-d10c-4ced-90f2-604f6052b8fe" />


Taking a look at the assembly we can see that when `*q` is assigned, the following instructions are executed:
```
00C368B5  lea         eax,[x]  
00C368B8  mov         dword ptr [q],eax
```

This gets the _memory address_ (`lea` (Load Effective Address) instruction) of the variable `[x]` and loads it into the `eax` register, the next instruction then moves a double length word (`dword`) to the memory address of `[q]` with the value assigned from the register `eax`

Similarly, when `**p` is assigned, the following instructions are executed:

```
00C368BB  lea         eax,[q]  
00C368BE  mov         dword ptr [p],eax
```

the `lea` instruction is used again to load the address of variable `[q]` into the `eax` register, the next instruction moves the address from the `eax` register and assigns it to the memory address of `[p]`

So now [q] has a value of [x]'s memory address, and [p] has a value of [q]'s memory address

<img width="1395" height="743" alt="image" src="https://github.com/user-attachments/assets/22969030-c4fe-48c4-bcd5-172b4a165b84" />

The 4 byte pointers `*q` and `**p` have been highlighted in orange and red respectively.

The value of the 8 byte variable `x` has been highlighted in green.

From this memory view we can see that `*q` has a value of `c4 fc af 00`, reversing for Little Endian Encoding yields `00 af fc c4` -> `0x00AFFC4`.

Variable `x` is on the row begging with `0x00AFFCC0` and has an offset of 4, so `x` resides at the memory address `0x00AFFCC4` which is what we see from the pointer *q. `x` currently has a value of `1f 85 eb 51 b8 1e 09 40` -> `0x40091eb851eb851f` which roughly corresponds to a value of `3.14`

Finally we can see `**p` has a value of `b8 fc af 00` which becomes `00 af fc b8` -> `0x00AFFCB8.`
`*q` resides at address of `0x00AFFC87` plus an offset of 49 bytes (0x31h) so `*q` resides at address `0x00AFFCB8` 

<img width="778" height="99" alt="image" src="https://github.com/user-attachments/assets/7522157e-1bdd-4b17-b330-08b545ba9efc" />

Inspecting the assembly logic for setting the value of `**p` we can see how the compiler assigns to the variable `x`.
```
00C368C1  mov         eax,dword ptr [p]  
00C368C4  mov         ecx,dword ptr [eax]  
00C368C6  movsd       xmm0,mmword ptr [__real@40191eb851eb851f (0C39BE8h)]  
00C368CE  movsd       mmword ptr [ecx],xmm0
```

The first instruction moves the value at the variable `p` to the `eax` register, 
The second instruction then takes the value stored at the address in `eax` register and move it to the `ecx` register, (`[eax]` means to get the value at this address)

The third and fourth instructions move a double floating point value (the constant 6.14) to the xmm0 register before then moving it to the value of the `[ecx]` register. 



The value of `**p` is the memory address of `q`, so when this is loaded into the eax register, the next instruction then loads the value at the memory address of `*q` into the `ecx` register, this means loading the address of `x` into the `ecx` register as `*q` points to `x`. Finally the value of xmm0 is moved to the value at `ecx` which is the memory location of `x`, updating `x`

<img width="1395" height="23" alt="image" src="https://github.com/user-attachments/assets/ed1412b0-e462-4a8e-8239-80cc97ab148d" />

### Q8. Pointers - Pointer chains (optional)

**Question**

<img width="2215" height="1483" alt="image" src="https://github.com/user-attachments/assets/7788d2be-04f8-47e2-8de4-2601e463a29d" />

Implement the above pointer chain

**Solution**

```c++
	void* pointer1;
	void* pointer2 = &pointer1;
	void* pointer3 = &pointer2;
	void* pointer4 = &pointer3;

	pointer1 = &pointer4;

	cout << "Pointer 1: " << &pointer1 << " - Points at: " << pointer1 << endl;
	cout << "Pointer 2: " << &pointer2 << " - Points at: " << pointer2 << endl;
	cout << "Pointer 3: " << &pointer3 << " - Points at: " << pointer3 << endl;
	cout << "Pointer 4: " << &pointer4 << " - Points at: " << pointer4 << endl;

	cout << endl;

	void* currentPointer = pointer1;

	for (int i = 0; i < 8; i++) 
	{
		cout << "Current Pointer: " << currentPointer;
		//*(void**) 
		//(void**) cast the address inside of currentPointer as a pointer to a void*
		//*(void**) get the value of the cast void** (a void*)
		currentPointer = *(void**)currentPointer;
		cout << " - Next Pointer: " << currentPointer << endl;
	}
```

**Output**

<img width="676" height="270" alt="image" src="https://github.com/user-attachments/assets/bca266fa-90c0-4e80-aba0-622682fd041e" />


## Week 5 - Lab E

### Q1. Operators in Grid

**Question**

Extend your code from Q2 and Q3 in Lab D.

Add the following functionality to your program:

The ability to write the Grid to an ostream using the auxiliary `operator<<`
The ability to read in the values from an istream into the Grid using the auxiliary `operator>>`



**Solution**

_grid.h_
```c++
#pragma once
#include <iostream>

class Grid
{
public:
	Grid();
	~Grid();

	void LoadGrid(const char filename[]);
	void SaveGrid(const char filename[]);

	friend std::ostream& operator<<(std::ostream&, const Grid&);
	friend std::istream& operator>>(std::istream&, Grid& g);

private:
	//Initialise member variables
	int m_grid[9][9] = {}; //Initialises to 0s
	int gridYSize = 0;
	int gridXSize = 0;
};

std::ostream& operator<<(std::ostream& stream, const Grid& g);
std::istream& operator>>(std::istream& stream, Grid& g);
```

_grid.cpp_
```c++

#include "Grid.h"
#include <iostream>
#include <fstream>
using namespace std;

/*References
W3Schools (2026) C++ Array Size [Source code]. https://www.w3schools.com/cpp/cpp_arrays_size.asp [Accessed 25 Feb 2026].
*/

/// <summary>
/// Grid constructor, calculates Grid Y and Grid X size using the sizeof m_grid
/// </summary>
Grid::Grid()
{
	gridYSize = sizeof(m_grid) / sizeof(m_grid[0]);
	gridXSize = sizeof(m_grid[0]) / sizeof(m_grid[0][0]);
}

Grid::~Grid()
{
}

//Create an input file stream from filename
//for each y value from 0 to 8 inclusive
//{
//   for each x value from 0 to 8 inclusive
//   {
//      store next value from the input file stream into grid at x,y
//   }
//}
//Close input file stream


void Grid::LoadGrid(const char filename[])
{
	ifstream inputStream(filename); //Create input file stream
	if (inputStream.fail())
	{ //Check input file was successfully opened.
		cout << "Error Opening File, check file " << filename << " exists and has correct permissions." << endl;
		inputStream.close();
		return;
	}

	//'this' is a pointer to the Grid object, deference it and pass to the method
	inputStream >> *this;

	//Close input file stream
	inputStream.close();
}

void Grid::SaveGrid(const char filename[])
{
	ofstream outputStream(filename, ios::out); //Open in write/overwrite mode
	if (!outputStream.is_open()) //Check file was able to be opened
	{
		outputStream.close();
		cout << "Error creating or opening output file." << endl;
		return;
	}

	outputStream << *this;

	outputStream.close();
}


std::ostream& operator<<(std::ostream& stream, const Grid& g)
{
	for (int y = 0; y < g.gridYSize; y++)
	{
		for (int x = 0; x < g.gridXSize; x++) 
		{
			stream << g.m_grid[y][x]; //Write value to file
			if (x == g.gridXSize - 1) //If last value on the row
			{
				stream << '\n'; //insert end of line
			}
			else
			{
				stream << ' '; //else add whitespace
			}
		}
	}
	return stream;
}


std::istream& operator>>(std::istream& stream, Grid& g)
{
	for (int y = 0; y < g.gridYSize; y++) //for each y value (every row in the grid)
	{
		for (int x = 0; x < g.gridXSize; x++) // for each x value (every column in the grid)
		{
			int value;
			if (!(stream >> value)) //Read next value from file, if this fails ran out of integers in the file, or encountered a non-integer value.
			{
				return stream;
			}
			g.m_grid[y][x] = value; //Set value in the grid to the read value
		}
	}
	return stream;
}
```

**Test Data**

```c++
#include <iostream>
#include "Grid.h"
using namespace std;

int main(int argn, char* argv[])
{
	Grid grid;
	grid.LoadGrid("Grid1.txt");
	grid.SaveGrid("OutGrid.txt");


	cout << grid;
}
```

_grid1.txt_
```
1 2 3 4 5 6 7 8 9
2 3 4 5 6 7 8 9 1
3 4 5 6 7 8 9 1 2
4 5 6 7 8 9 1 2 3
5 6 7 8 9 1 2 3 4
6 7 8 9 1 2 3 4 5
7 8 9 1 2 3 4 5 6
8 9 1 2 3 4 5 6 7
9 1 2 3 4 5 6 7 8
```


**Output**
<img width="1089" height="331" alt="image" src="https://github.com/user-attachments/assets/29a7c163-1552-46a4-8c87-d562537d8a8d" />


<img width="583" height="321" alt="image" src="https://github.com/user-attachments/assets/365d8c94-87e0-4b6d-91f4-02816f94b3e7" />


**Reflection**

In this task I have extended my work from the previous lab to include reading and writing the grid into a stream with the auxillary `<< and >>` operators. To do this I assigned the operator overload functions as `friends` of the grid class, this allowed them to access private or protected data variables (like `m_grid`) of the grid class. While I could have exposed the grid with a public getter, I believed using the friend modifier to be pertinent as the stream read and write operations should happen as quickly as possible and the read/write operations will be making many calls to the getter, which may negatively impact performance. The Grid was passed by reference to the stream operators as we do not want to copy it in memory when calling these operators, the output stream operator also uses a constant for the grid as it should never change when writing to the ostream.

After defining the overloaded operators as friends and then outside of the class in the headerfile, in the source file I added the operator functionality.

Using my work from Lab-D, I moved the read and write loop functionality into the new operator functions switching each filestream for the paramater provided `stream`, this allows these operators to be used in any stream type that implements the istream or ostream functionality, such as writing to the console, or to a file.

Finally, I updated the methods that read and write the grid to a file, swapping the loops for the newly implemented operator overloads, since these methods will be called from within the object itself, pass to the stream by dereferencing the fundamental `this` pointer, passing a reference to the current grid object to the stream operators.


```c++
...
	//'this' is a pointer to the Grid object, deference it and pass to the method
	inputStream >> *this;
...


	outputStream << *this;

```

### Q2. Fractions

**Question**

Open the Fractions project

Implement the Fraction class that you have seen in lectures. Use the header file example that was presented in lectures to define your class, methods, member variables etc.

Methods will include:

Constructors
Add Fraction (see equation 1 for help)
Subtract Fraction
Multiply by int
Multiply with Fraction (optional)
Divide by int (optional)
Divide by Fraction (optional)
Inspector (getter) for the Numerator
Inspector (getter) for the Denominator
Mutator (setter) for the Numerator
Mutator (setter) for the Denominator
Write
Read

**Solution**

_Fraction.h_
```c++
#pragma once
#include<iostream>

class Fraction
{
public:
	// default constructor
	Fraction();
	// specific constructor
	Fraction(int num, int den);
	// arithmetic facilitators
	Fraction Add(const Fraction& rhs) const;
	Fraction Subtract(const Fraction& rhs) const;
	Fraction Multiply(int scale) const;
	Fraction Divide(int scale) const;
	Fraction Multiply(const Fraction& rhs) const;
	Fraction Divide(const Fraction& rhs) const;
	// getters/inspectors
	int Num() const;
	int Den() const;
	// setters/mutators
	void Num(int num);
	void Den(int den);
	// stream facilitators
	void Write(std::ostream& sout) const;
	void Read(std::istream& sin);

private:
	// data members
	int m_num;
	int m_den;
};

```


_Fraction.cpp_
```c++
#include "Fraction.h"

/// <summary>
/// Default Fraction Constructor, Initialises to 0/1
/// </summary>
Fraction::Fraction() : Fraction(0, 1)
{
}
/// <summary>
/// Create a fraction with provided params
/// </summary>
/// <param name="num">Fraction Numerator</param>
/// <param name="den">Fraction Denominator</param>
Fraction::Fraction(int num, int den)
{
	Num(num);
	Den(den);
}
/// <summary>
/// Add the provided fraction to the this fraction
/// </summary>
/// <param name="rhs">Fraction object to add</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Add(const Fraction& rhs) const
{
	return Fraction((m_num * rhs.Den() + rhs.Num() * m_den), (m_den * rhs.Den()));
}
/// <summary>
/// Subtract the provided fraction from this fraction
/// </summary>
/// <param name="rhs">Fraction to subtract</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Subtract(const Fraction& rhs) const
{
	return Fraction((m_num * rhs.Den() - rhs.Num() * m_den), (m_den * rhs.Den()));
}
/// <summary>
/// Multiply the current fraction by a provided scale
/// </summary>
/// <param name="scale">Scale to Multiply fraction by</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Multiply(int scale) const
{
	return Fraction(m_num * scale, m_den);
}
/// <summary>
/// Divide the current fraction by a provided scale
/// </summary>
/// <param name="scale">Scale to divide fraction by</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Divide(int scale) const
{
	return Fraction(m_num, m_den * scale);
}
/// <summary>
/// Multiply the current fraction by a provided fraction
/// </summary>
/// <param name="rhs">Multiplier fraction</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Multiply(const Fraction& rhs) const 
{
	return Fraction((m_num * rhs.Num()), m_den * rhs.Den());
}
/// <summary>
/// Divide the current fraction by a provided fraction
/// </summary>
/// <param name="rhs">Divisor Fraction</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Divide(const Fraction& rhs) const
{
	return Fraction(m_num * rhs.Den(), m_den * rhs.Num());
}

int Fraction::Num() const
{
	return m_num;
}

int Fraction::Den() const
{
	return m_den;
}

void Fraction::Num(int num)
{
	m_num = num;
}

void Fraction::Den(int den)
{
	if (den == 0) 
	{
		throw std::invalid_argument("Denominator cannot be set to 0!");
	}
	m_den = den;
}

void Fraction::Write(std::ostream& sout) const
{
	sout << Num() << "/" << Den();
}
/// <summary>
/// Read a fraction from a stream in format "Num/Den"
/// </summary>
/// <param name="sin">stream input</param>
void Fraction::Read(std::istream& sin)
{
	int num;
	int den;
	char divSymbol;

	sin >> num;
	sin >> divSymbol;
	sin >> den;
	//stream fail, no divisor, denominator is 0
	if (!sin || divSymbol != '/' || den == 0)
	{
		sin.setstate(std::ios::failbit); //Stream read fail, do nothing to the fraction
		return;
	}

	m_num = num;
	m_den = den; //don't use mutator as we have already verified den != 0 and it can throw an error
}

```

**Test Data**

```c++
#include "Fraction.h"
#include <iostream>
using namespace std;

int main(int args, char** argv)
{
    Fraction f1(1, 2);        // 1/2
    Fraction f2(3, 4);        // 3/4
    Fraction result;

    result = f1.Add(f2);      // 1/2 + 3/4 = 10/8
    cout << "1/2 + 3/4 = ";
    result.Write(cout);
    cout << endl;

    result = f2.Subtract(f1); // 3/4 - 1/2 = 2/8
    cout << "3/4 - 1/2 = ";
    result.Write(cout);
    cout << endl;

    result = f2.Multiply(3);  // 3/4 * 3 = 9/4
    cout << "3/4 * 3 = ";
    result.Write(cout);
    cout << endl;

    result = f2.Multiply(f1); // 3/4 * 1/2 = 3/8
    cout << "3/4 * 1/2 = ";
    result.Write(cout);
    cout << endl;

    result = f2.Divide(3); // 3/4 / 3 = 1/4
    cout << "3/4 / 3 = ";
    result.Write(cout);
    cout << endl;

    result = f2.Divide(f1); // 3/4 / 1/2 = 6/4
    cout << "3/4 / 1/2 = ";
    result.Write(cout);
    cout << endl;

    Fraction f3;
    f3.Read(cin);             // input format is "1/2" for a fraction with numerator 1 and denominator 2
    cout << "Read = ";
    f3.Write(cout);
    cout << endl;

    system("pause");
}
```

**Output**

```
1/2 + 3/4 = 10/8
3/4 - 1/2 = 2/8
3/4 * 3 = 9/4
3/4 * 1/2 = 3/8
3/4 / 3 = 3/12
3/4 / 1/2 = 6/4
7/12
Read = 7/12
```
<img width="357" height="189" alt="image" src="https://github.com/user-attachments/assets/b4b919ac-60f7-4127-bacf-6965b6a84db4" />

**Reflection**

In this task I have implemented the Fraction class, this includes creating the header file, declaring the members of the class, and then the source file, defining the class members. I also implemented the optional methods, such as multiplying and dividing two fractions. Most of the implementation of these fractions were very simple, with method definitions often being single return statements with any arithmetic that has needed to be done in place of the parameters of the constructor.

The fractions class uses two constructors, a default constructor of ```Fraction()```  which calls the parameter constructor 
```c++
Fraction(int num, int den)
```
This constructor then uses the mutators to assign values to the private members `m_num` and `m_den`. Any validation on these takes place in these mutators, such as ensuring that the denominator is not 0.

For the read function chosen uses the input `"Num/Den"`. To convert this into a valid Fraction the method takes 3 reads in from the stream, the first assigns to the numerator, the second ensures that there is a `/` placed between the numerator and denominator, the final input reads the denominator.

Once the method has taken the 3 reads from the stream the validity of the reads is checked, 

``` c++
	if (!sin || divSymbol != '/' || den == 0)
	{
		sin.setstate(std::ios::failbit); //Invalid input, do nothing to the fraction
		return;
	}
```

First the fail flag for the stream is read, if the stream has read unsuccessfully the internal block is instantly entered, preventing any issue with accessing the variables when they may be unitialised.
If the stream did not fail, the validity of the input is checked, first to see if the divisor symbol was included, and then the value of the denominator is verified to ensure it is not equal to 0.

We check the denominator here instead of letting the mutator do it as c++ convention is to not throw errors from a stream read/write and to instead set the failbit on the stream.


### Q3. - Operators in Fraction

**Question**

Add the following functionality to your Fraction class:

The ability to add two Fractions together using the class member operator operator+
The ability to subtract one Fraction from another fraction using the class member operator operator-
The ability to multiply a Fraction with an int using the class member operator operator*
The ability to multiply an int with a Fraction using the auxiliary operator operator*

**Solution**
_Fraction.h_
```c++
#pragma once
#include<iostream>

class Fraction
{
public:
	// default constructor

	Fraction();
	//Convert int to Frac

	Fraction(int);
	// specific constructor

	Fraction(int num, int den);
	// arithmetic facilitators
	Fraction Add(const Fraction& rhs) const;
	Fraction Subtract(const Fraction& rhs) const;
	Fraction Multiply(const Fraction& rhs) const;
	Fraction Divide(const Fraction& rhs) const;

	Fraction Multiply(int scale) const;
	Fraction Divide(int scale) const;
	// getters/inspectors
	int Num() const;
	int Den() const;
	// setters/mutators
	void Num(int num);
	void Den(int den);
	// stream facilitators
	std::ostream& Write(std::ostream& sout) const;
	std::istream& Read(std::istream& sin);

	// Mutating Operator Overload
	inline Fraction& operator+= (const Fraction& rhs) { *this = Add(rhs); return *this; }
	inline Fraction& operator+= (const int& rhs) { *this = Add(rhs); return *this; }

	inline Fraction& operator-= (const Fraction& rhs) { *this = Subtract(rhs); return *this; }
	inline Fraction& operator-= (const int& rhs) { *this = Subtract(rhs); return *this; }

	inline Fraction& operator*= (const Fraction& rhs) { *this = Multiply(rhs); return *this; }
	inline Fraction& operator*= (const int& rhs) { *this = Multiply(rhs); return *this; }

	inline Fraction& operator/= (const int& rhs) { *this = Divide(rhs); return *this; }
	inline Fraction& operator/= (const Fraction& rhs) { *this = Divide(rhs); return *this; }

private:
	// data members
	int m_num;
	int m_den;
};

//Auxillaries & Operator Overloads

//Frac OP Frac
inline Fraction operator+ (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) /= (rhs); }
//Frac OP int
inline Fraction operator+ (const Fraction& lhs, const int& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const Fraction& lhs, const int& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const Fraction& lhs, const int& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const Fraction& lhs, const int& rhs) { return Fraction(lhs) /= (rhs); }
//int OP Frac
inline Fraction operator+ (const int& lhs, const Fraction& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const int& lhs, const Fraction& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const int& lhs, const Fraction& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const int& lhs, const Fraction& rhs) { return Fraction(lhs) /= (rhs); }

//Stream Read/Write
inline std::ostream& operator<< (std::ostream& stream, const Fraction& rhs) { return rhs.Write(stream); }
inline std::istream& operator>> (std::istream& stream, Fraction& rhs) { return rhs.Read(stream); }
```

_Fraction.cpp_
```c++
#include "Fraction.h"

/// <summary>
/// Default Fraction Constructor, Initialises to 0/1
/// </summary>
Fraction::Fraction() : Fraction(0, 1)
{
}

/// <summary>
/// Create a fraction from an integer
/// </summary>
/// <param name="num">Integer to convert to fraction</param>
Fraction::Fraction(int num) : Fraction(num, 1)
{
}

/// <summary>
/// Create a fraction with provided params
/// </summary>
/// <param name="num">Fraction Numerator</param>
/// <param name="den">Fraction Denominator</param>
Fraction::Fraction(int num, int den)
{
	Num(num);
	Den(den);
}
/// <summary>
/// Add the provided fraction to the this fraction
/// </summary>
/// <param name="rhs">Fraction object to add</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Add(const Fraction& rhs) const
{
	return Fraction((m_num * rhs.Den() + rhs.Num() * m_den), (m_den * rhs.Den()));
}
/// <summary>
/// Subtract the provided fraction from this fraction
/// </summary>
/// <param name="rhs">Fraction to subtract</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Subtract(const Fraction& rhs) const
{
	return Fraction((m_num * rhs.Den() - rhs.Num() * m_den), (m_den * rhs.Den()));
}

/// <summary>
/// Multiply the current fraction by a provided fraction
/// </summary>
/// <param name="rhs">Multiplier fraction</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Multiply(const Fraction& rhs) const
{
	return Fraction((m_num * rhs.Num()), m_den * rhs.Den());
}
/// <summary>
/// Divide the current fraction by a provided fraction
/// </summary>
/// <param name="rhs">Divisor Fraction</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Divide(const Fraction& rhs) const
{
	return Fraction(m_num * rhs.Den(), m_den * rhs.Num());
}

/// <summary>
/// Multiply the current fraction by a provided scale
/// </summary>
/// <param name="scale">Scale to Multiply fraction by</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Multiply(int scale) const
{
	return Fraction(m_num * scale, m_den);
}
/// <summary>
/// Divide the current fraction by a provided scale
/// </summary>
/// <param name="scale">Scale to divide fraction by</param>
/// <returns>New Fraction with total value</returns>
Fraction Fraction::Divide(int scale) const
{
	return Fraction(m_num, m_den * scale);
}


int Fraction::Num() const
{
	return m_num;
}

int Fraction::Den() const
{
	return m_den;
}

void Fraction::Num(int num)
{
	m_num = num;
}

void Fraction::Den(int den)
{
	if (den == 0) 
	{
		throw std::invalid_argument("Denominator cannot be set to 0!");
	}
	m_den = den;
}

std::ostream& Fraction::Write(std::ostream& sout) const
{
	sout << Num() << "/" << Den();
	return sout;
}
/// <summary>
/// Read a fraction from a stream in format "Num/Den"
/// </summary>
/// <param name="sin">stream input</param>
std::istream& Fraction::Read(std::istream& sin)
{
	int num;
	int den;
	char divSymbol;

	sin >> num;
	sin >> divSymbol;
	sin >> den;
	//stream fail, no divisor symbol, denominator is 0
	if (!sin || divSymbol != '/' || den == 0)
	{
		sin.setstate(std::ios::failbit); //Stream read fail, do nothing to the fraction
		return sin;
	}

	m_num = num;
	m_den = den; //don't use mutator as we have already verified den != 0 and it can throw an error

	return sin;
}



```
**Test Data**
```c++
    cout << "overload tests\n" << endl;

    Fraction f5(2, 6);
    Fraction f6(4, 5);

    result = f1 + f2;     // 1/2 + 3/4 = 10/8
    cout << "1/2 + 3/4 = " << result << endl;

    result = f1 + 3;   //1/2 + 3 = 7/2
    cout << "1/2 + 3 = " << result << endl;

    result = 3 + f1;    //1/2 + 3 = 7/2
    cout << "3 + 1/2 = " << result << endl;

    f5 += f6;   //2/6 + 4/5 = 34/30
    cout << "2/6 += 4/5, f5 = " << f5 << endl;
    f5 = Fraction(2, 6);

    result = f2 - f1;     // 3/4 - 1/2 = 2/8
    cout << "3/4 - 1/2 = " << result << endl;

    result = f1 - 1;    // 1/2 - 1 = -1/2
    cout << "1/2 - 1 = " << result << endl;

    result = 2 - f2;    // 2 - 3/4 = 5/4
    cout << "2 - 3/4 = " << result << endl;

    result = f1 * f2;   //1/2 * 3/4 = 3/8
    cout << "1/2 * 3/4 = " << result << endl;

    result = f2 * 3;      // 3/4 * 3 = 9/4
    cout << "3/4 * 3 = " << result << endl;

    result = 3 * f2;      // 3/4 * 3 = 9/4
    cout << "3 * 3/4 = " << result << endl;

    result = f1 / f2;   // 1/2 / 3/4 = 4/6
    cout << "1/2 / 3/4 = " << result << endl;

    result = f1 / 2;    // 1/2 / 2 = 1/4
    cout << "1/2 / 2 = " << result << endl;

    result = 3 / f1;    // 3 / 1/2 = 6/1
    cout << "3 / 1/2 = " << result << endl;

    Fraction f4;
    cin >> f4;            // input format is up to you, e.g. "1/2" to represent 1/2
    cout << "Read = " << f4 << endl;

    system("pause");
```

**Output**

<img width="346" height="357" alt="image" src="https://github.com/user-attachments/assets/699116ba-1331-4b76-8f76-4421a7d760bb" />


**Reflection**

In this task I have implemented operator overloads such as seen in Q1. To implement these overloads i used the functions that I had defined in Q2 for using mathematical operators on Fractions.
```
Guidelines: Method or Auxiliary Function?
1. Virtual functions must be member methods
2. Both operator>> and operator<< must be auxiliary functions
3. If data conversion is required on the left hand side of the operator, must
use an auxiliary function
4. If operator overloading, then the preference is to use an inline auxiliary
function
5. Otherwise use a member method
```

Following these guidelines from the Lecture ```500083 ZM Week 5``` I implemented the operator overloads as inline auxiliary functions.
I ensured the consistency of operators by implementing `+, -, *, /` in terms of `+=, -=, *=, /=*`. 

```c++
	inline Fraction& operator+= (const Fraction& rhs) { *this = Add(rhs); return *this; }
```
To do this I declared the compound assignment operators in the class as member methods, this is required as these methods mutate the object that they were called on. The overloads require the use of the `this` pointer, the pointer is dereferenced and has value updated to the return value of the Add method before returning a reference to the object at `*this` which we have just updated.

I have implemented the overloads to work with integers as well as other fractions and ensured that there is parity between the operations, for instance ```Fraction(1,2) + 2``` and ```2 + Fraction(1,2)``` are both valid.


```c++
//Frac OP Frac
inline Fraction operator+ (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const Fraction& lhs, const Fraction& rhs) { return Fraction(lhs) /= (rhs); }
//Frac OP int
inline Fraction operator+ (const Fraction& lhs, const int& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const Fraction& lhs, const int& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const Fraction& lhs, const int& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const Fraction& lhs, const int& rhs) { return Fraction(lhs) /= (rhs); }
//int OP Frac
inline Fraction operator+ (const int& lhs, const Fraction& rhs) { return Fraction(lhs) += (rhs); }
inline Fraction operator- (const int& lhs, const Fraction& rhs) { return Fraction(lhs) -= (rhs); }
inline Fraction operator* (const int& lhs, const Fraction& rhs) { return Fraction(lhs) *= (rhs); }
inline Fraction operator/ (const int& lhs, const Fraction& rhs) { return Fraction(lhs) /= (rhs); }
```

To do this i provide overloads for each situation involving the datatypes. 
When ```Frac OP int``` is called, the operator overload itself is overloaded (to the method taking an integer instead of a fraction) and the arithmetic facilitator for that operation with a whole number is called 

When ```int OP Frac``` is called, the integer is converted to a fraction and before being passed to the appropriate member method.


### Q4. Parameters

**Question**

Copy your code for pass-by-value and pass-by-ref into your lab book. Reflect on the difference between them

**Solution**
```c++
//By value

void myswap(int lhs, int rhs) {
	int temp = lhs;
	lhs = rhs;
	rhs = temp;
}

//By reference
void myswap(int& lhs, int& rhs) {
	int temp = lhs;
	lhs = rhs;
	rhs = temp;
}

//By address
void myswap(int* lhs, int* rhs) {
	int temp = lhs;
	lhs = rhs;
	rhs = temp;
}


**Reflection**
Pass by value

<img width="1400" height="801" alt="image" src="https://github.com/user-attachments/assets/4c8abb57-0d26-4393-88ee-4fda5f5d89a6" />

Value of a and b are pushed onto the stack (highlighted in pink), the method `swap(a, b)` is then called which pushes the return address to the stack (`0x00e126a4h`, highlighted in orange).
the base pointer is then pushed to the stack (highlighted in blue, `0x007afe6ch`) as the calling function expects this value to be the same when the function returns.

<img width="1392" height="859" alt="image" src="https://github.com/user-attachments/assets/c614c8ee-0c1e-49cd-9b28-7dd0fe8ad3b5" />

ESP is then pushed to the base pointer so it can be used to keep track of the methods variables. `0xCCh` (204 bytes) is then subtracted from the stack pointer to define the local variable space. 

