# Files and IO


Interacting with files will mean being able to read and write to storage mediums. If we are intending to use data stored in a file, we have to understand how that data is stored and what will be an appropriate tool for the job.

What kind of data is stored in the following files?

* HelloWorld.cs
* Cat.jpg
* Program.exe
* TODO.txt

## IO Classes with C#

Within the C# standard library we have access to a large range of I/O classes. You have already been using the `Console.ReadLine` for reading content from standard input. However we are able to interact with a variety of sources.

C# will represent files using `File` from `System.IO`, however this is mostly retrieving metadata from the file and that the class contains many `static` methods to create and open files. 

When we want to read data, we will use `StreamReader` type to achieve this.

When writing, we want to construct a `StreamWriter` type.

Do note, there is a distinction between the different readers and writers as well as formatters. As established we have two types of data we may want to handle.

* Binary Data
* Text Data

Picking an appropriate one will make writing the code easier.

### Reading Text Data

We will use `StreamReader` and open the using its constructor.

```cs
  StreamReader reader = new StreamReader("TODO.txt");

  // Read the stream as a string.
  string text = reader.ReadToEnd();

  reader.Close();
```

The above snippet demonstrates the creation of a new reader object and reading the contents. However, we may want to read the file **line-by-line**.

```cs
  
  StreamReader reader = new StreamReader("TODO.txt");

  // Read the stream as a string.

  string line = '';

  while((line = reader.ReadLine()) != null)
  {
    Console.WriteLine(line);
  }

  reader.Close();
```

We can observe how `ReadLine` could return a `null` value, if the contents of the file have been exhausted.

## Writing Text Data

`StreamWriter` allows for printing formatted representations of objects to a text-output stream.

```cs
StreamWriter writer = new StreamWriter("NewTODO.txt");

writer.WriteLine(1.0);
writer.WriteLine("Get Milk");
writer.WriteLine("Sleep...");

writer.Close();
```

One thing you may have noticed is that `ReadLine` and `WriteLine` are the same methods used in `Console`. This is because they are leverage the same types behind the scenes.

Do note, make sure you `Close` your IO streams, otherwise it is likely that contents will not be flushed.
