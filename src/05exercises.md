# Exercises

The list of exercises examines different parts of this chapter. You are required to use the `class` construct within these exercises as well as inheritance where required.

## Tasks

### 1. Traffic Lights

You will need to create a trafficlight simulation but use inheritance to solve this problem. It is encouraged that you **do not** use **if** statements in your solution.

You will have four classes to implement:
* `TrafficLight` which will have the following properties:
  * `NextLight` method which returns a `TrafficLight` object
  * `OutputLight` method which prints out the current colour of the light

* `RedLight`, `GreenLight` and `YellowLight` which must **inherit** from `TrafficLight`
  * When `Red.NextLight` is called, it should return a new `GreenLight`
  * When `Green.NextLight` is called, it should return a new `YellowLight`
  * When `Yellow.NextLight` is called, it should return a new `RedLight`

Use the following snippet to test your implementation.

```cs
TrafficLight light = new RedLight();

for(int i = 0; i < 4; i++)
{
  light.OutputLight();

  light = light.NextLight(); 
}  
```

The program above should output the lights in the following order.

```
Red
Green
Yellow
Red
```

You may change the number of iterations for further testing if you would prefer.

### 2. Point2D

This question has two parts to it.

#### Part 1.

You are to create a class that will store a pair of 2D coordinates. These coordinates are stored as doubles and will denote a point on a 2D plane.

Your Point2D objects must have the following public getter methods:

* `Point2d(double x, double y)`: that accepts 2 double values (x, y)
* `GetX()` : double
* `GetY()` : double
* `GetCoords()` : double[] (x at index 0 and y at index 1)

#### Part 2.

Implement the static method  that will allow you to find a point between two given points. Implement this method to accept two Point2D objects and return a Point2D object. To calculate a point, you can use the following formula:

\\(x = a_x + ((b_x - a_x) * d)\\)

\\(y = a_y + ((b_y - a_y) * d)\\)

\\(P = Point2D(x, y)\\)


Example 1:
```
Point2D a = new Point2D(2.0, 3.5);
Point2D b = new Point2D(1.0, 3.5);
Point2D p = Line.FindPoint(a, b, 0.5); //returns a Point2D with x=1.5, y=3.5
```

Example 2:
```
Point2D a = new Point2D(2.0, 5.5);
Point2D b = new Point2D(2.0, 3.5);
Point2D p = Line.FindPoint(a, b, 0.5);//returns a Point2D with x=2.0, y=4.5
```

Example 3:

```
Point2D a = new Point2D(2.0, 5.5);
Point2D b = new Point2D(2.0, 3.5);
Point2D p = Line.FindPoint(a, b, 1.5); //returns null
```


## Tasks with Test cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-cs>.

Attempt the following exercises in the **Week06** folder.

Ensure you run `dotnet build` and `dotnet test` while your shell is in the directory of a particular question. Run `dotnet test` to check to see if your solution works as specified.

