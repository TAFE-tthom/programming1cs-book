# Methods, Static Methods and Inheritance

To clarify from the previous section, we demonstrated a particular kind of **methods**. This kind of **method** was an instance method is has access to the **instance** via `this`.

Inheritance with classes is integrated and bound with methods. It allows for redefinition and crafting more bespoke methods for the type but adhering to a generalised signature and having the ability to reuse logic.

## Static Methods

A method is a stored set of instructions bound to an object. In the case of a static method, the object is the class which it is defined in.

When specifying `static` before the method name, it is specifying that the method is associated with the class, not the instance and therefore is not used as something that operations on instance of that type (not, implicitly at least).

The utility part of question is still up in the air though and it is one where your static method could be an alternative constructor for particular set of input (like creating an object based on a filepath).

Let's examine the following snippet and its relevance.

```cs
class AddressEntry {

  string name;
  string address;
  string phoneNumber;
  string email;
  
  public AddressEntry(string name, string address,
    string phoneNumber, string email)
  {

    this.name = name;
    this.address = address;
    this.phoneNumber = phoneNumber;
    this.email = email;
  }

  static AddressEntry[] FromCSVLine(string line)
  {
    String[] spittedRecords = line.Split(',');
    if(splittedRecords.Length >= 4) {
      return new AddressEntry(
        splittedRecords[0],
        splittedRecords[1],
        splittedRecords[2],
        splittedRecords[3]
      );
    } else {
      return null;
    }
  }

  /// methods associated
} 
```

The snippet provides two kinds of constructions for an `AddressEntry`. Viewing this snippet where it is an `AddressEntry` in an `AddressBook`, we could be loading each entry from a `.csv` file and having some functionality to interpret lines from that file gives us access to utility construction.

### `this` keyword

We have hinted at this topic prior and now lets look into the `this` keyword and how it can help with eliminating ambiguity but also used for passing an object reference within an instance context.

The this keyword allows the programmer to refer to the object while within an instance method context. We cannot use the keyword within a static context.

#### Addressing ambiguity

The `this` keyword within javascript (but other programming languages) has been used to address ambiguity of parameters and fields that have the same name. We will use the following as a case study.

```cs
class Postcard
{

  string sender = '';
  string receiver = '';
  string address = '';
  string contents = '';
  
  public Postcard(string sender,
    string receiver, string address, string contents)
  {
    this.sender = sender;
    this.receiver = receiver;
    this.address = address;
    this.contents = contents;
  }
}
```

Without using the `this` keyword, the parameters within the constructor would need to be renamed. This would impact readability of our code. But using the `this` keyword, we are able to make it clear that `this.<field>` is utilising the field associated with the object.

#### As a reference

As outlined prior, the `this` keyword isn't utilised within a `static` method as it isn't using the instance of the object. So using the `this` keyword as an argument could seem quite unintuitive but something that can be done.

Let's examine the following scenario.

```cs
class Postcard
{

  string sender = '';
  string receiver = '';
  string address = '';
  string contents = '';
  
  public Postcard(string sender,
    string receiver, string address, string contents)
  {
    this.sender = sender;
    this.receiver = receiver;
    this.address = address;
    this.contents = contents;
  }

  public bool Arrived() {
    return this.delivered;
  }

  public static bool HasArrived(Postcard postcard) {
    return postcard.Arrived();
  }
}
```

We can observe how the static method is using an instance method associated with the `postcard` parameter. The logic that checks if a postcard has arrived is in the instance method, but what if we were to switch this around? What if we were to get the instance method to use the static method that checks the state?

```cs
class Postcard
{

  string sender = '';
  string receiver = '';
  string address = '';
  string contents = '';
  
  public Postcard(string sender,
    string receiver, string address, string contents)
  {
    this.sender = sender;
    this.receiver = receiver;
    this.address = address;
    this.contents = contents;
  }

  public bool Arrived()
  {
    return this.delivered;
  }

  public static bool HasArrived(Postcard postcard)
  {
    return postcard.Arrived();
  }
}
```
Bingo! We can use how we have used the `this` keyword has an argument and that the `static` method could use the object given.

## Inheritance

Inheritance is a significant concept of OOP. Allowing reusability and
changes to inherited methods between different types in a hierarchy.

What does inheritance provide us.

* Attribute and method reusability
* Defining sub-type methods
* Overriding Inherited Methods
* Type Information.

As established, we are able to create a type using `class` and with that we can compare against it.

### Extending A Class

As part of creating a sub-type of an existing class we will be using the `:` keyword. This keyword allows us to specify when a class is inheriting from another.

```
class ClassName : ClassItInheritsFrom
```

* `ClassName` - Name of the class/type being created.

* `:` - We are inheriting from the following class. It is seen as an extension of the super/base class. Since it isn't explicit if we are inheriting from a class or interface, the information is derived from the type specified.

* `ClassWeInheritFrom` - The class we are inheriting from, it will have access to the public methods and attributes.

We can use the following as an example here.

```cs
class Dog : Canine
```

Once defined, Dog type can also be used as a Canine type as it is just an extension of such type.

#### Inherited constructors

When a type inherits from another, it will be able to use the existing fields and methods, however it will need to ensure that it can use the existing constructor. Let's look into the scenario where we have two types `User` and `Admin`.

```cs
class User {
  string username = "Anonymous";
  string active = true;
  string email;

  public User(string username, string email)
  {
    this.username = username;
    this.email = email;
  }
}

class Admin : User {

  public Admin(string username, string email) : base(username, email)
  {
    // Additional
  }
}
```

The above snippet demonstrates the `Admin` class inheriting from `User` but using `User`'s  existing constructor via `base`. This call is required for a subtype to ensure the super type's constructor is called.


#### Inherited Methods

Already established, we have access to the super type's methods. However, lets consider what can occur when we redefine or don't.

```cs
class User {
  string username = "Anonymous";
  string active = true;
  string email;

  public User(string username, string email)
  {
    this.username = username;
    this.email = email;
  }

  DeactivateUser(user) {
    if(user.email === this.email) {
      user.active = false;
    }
    console.log("A regular user cannot delete another")
  }

  DeletePost(post) {
    if(post.user.email === this.email) {
      post.deletedByUser = true;
      post.deletedBy = this.username;
    }
  }
}

class Moderator : User {

  constructor(username, email): Base(username, email) {
  }
  
  DeletePost(post) {
    if(post.user.email === this.email) {
      base.DeletePost(post);
    } else {
      post.deletedByModerator = true;
      post.deletedBy = this.username;
    }
  }
  
}

class Admin : User {

  public Admin(string username, string email) : base(username, email)
  {
    // Additional
  }

  DeactivateUser(user) {
    user.active = false;
  }

}
```

The classes above demonstrate variation in the inherited methods and the **overriding** of the original logic as well re-use of it.

* The user can only delete their own posts and cannot deactivate other users, only themselves.

* Moderator can delete posts but it has to be acknowledged it was deleted by them. It will use the `User.DeletePost` logic if it identifies that the post originated from itself.

* Admin can delete posts and deactivate users.

This kind of specialisation of logic while still adhering to the same method signature means any place that uses methods from the `User` type, can also have `Moderator` and `Admin` be used in same place without modification.

## Inheritance vs Composition

While we have introduced inheritance which forms the basis for reusing attributes and methods. It should be noted that it shouldn't be used readily. There is a tendency to run into issues like **weak base class**.

It should be noted that the relationship between two classes can be in the following forms.

* Is-a relationship (Extension, suitable for inheritance)

* Has-a relationship (Contains or is made up of that type, not suitable for inheritance)

We have to be very certain with inheritance that any class that inherits from another is a type of that class. There should be clear reasoning that the types satisfy the relationship.

Some instances where it makes sense:

* Super class is Cat and subclasses are Panther, Lion, Tiger
* Super class is Controller and subclasses are Gamepad, Joystick, Powerglove
* Super class is Media and subclasses are DVD, Book, Image

