# Exercises

## Tasks 💻

Work on the following tasks as a way to ensure you have understood this chapter's topic.

### 1. Hello Command Line

Create a `Hello` project which you will use to accept a **single** command line argument. The intent of the program is to *prefix* `Hello `  to the command line argument.

Example:

```
dotnet run Tim
Hello Tim
```

Save your script and provide a comments that explains what index you are using and how you are printing the string.

### 2. Calculating Distance

Create a `DistanceTravelled` project which you will use to accept **two** command line arguments. The intent of this program is to use two variable which represent **speed** and **duration**. These two variables can be multiplied to compute the total distance travelled.

\\(distance = speed * duration\\)

Afterwards we can print out the speed, duration and total distance travelled.

You can assume that speed is in km/h and duration is in hours.

Example:

```
dotnet run 50 2
Speed: 50 km/h
Duration: 2 hours
Travelled: 100 km
```

Save your script and describe what functions you use to convert the data into the appropriate types and the operators you used.

### 3. Area of a Triangle

Write a program that will calculate the area of a triangle.

Use the following formula and translate it appropriately: \\(A=\frac{b*h}{2}\\)

Your program will accept the **base** and **height** as arguments. The **area** should be printed to two decimal places.

Use the following example and the values inputted to check your solution.

```
dotnet run 5 3
7.50  
```

### 4. Volume of a Sphere

Create a project called `Volume` and implement a program that will do perform the following.

Write a program that will calculate the volume of a sphere.
The program must allow the user to input the radius of the sphere using command line arguments.

Use the following formula: \\(V = (4/3) * pi * r^3\\)

To access `pi`, you can use `Math.PI`.

Example:

```
The radius inputted of the sphere: 2
Volume is: 33.51032
```

You will need to use a command line argument to retrieve the radius.


## Tasks with test-cases

Please refer to the following code repository for the exercises [Programming1-CS Repository](https://github.com/TAFE-tthom/programming1-cs).

Attempt the following exercises in the **Week02** folder - do note, the structure will be updated to be more relevant to the chapters of the book.

Ensure you run `dotnet build` and `dotnet test` while your shell is in the directory of a particular question. Run `dotnet test` to check to see if your solution works as specified.

