# Reflection

## The `Class` class

For each of the type there will be one and only one instance of a `Class` class, regardless of what method you take to access it.

### Ways to access the instance of the `Class` class for a class/type

1. Calling `getClass()` on the reference to an instance of a class/type
2. Calling `Class.forName(String className)` method with a fully qualified name of the class/type - including the package name
3. Using the type literal - `String.class`

### Modifiers

`getModifiers()` on an instance of a `Class` class returns an integer with its bits being the flag for each of the modifiers.

Can perform either bit operations or use static methods in the `Modifier` class:
```java
Class<?> classForBankAccount = bankAccount.getClass();

System.out.println((Modifier.FINAL & classForBankAccount.getModifiers()) > 0);

System.out.println(Modifier.isFinal(classForBankAccount.getModifiers()));
```

Modifiers on members of a class can be utilised in the same context.


## Accessing the members of a class/type

Two categories of methods:
1. Methods that return fields, constructors or methods that are declared only within the class itself - this will return members that are private, protected and protected.

2. Methods that return fields, constructors or methods that are declared within the class itself as well as the inherited class, but these will only return the public members. Keep in mind that the constructors are never inherited therefore in the case of constructors, the only difference between 1 vs 2 will be that 1 returns private, protected and public constructors whereas 2 will return only the public.

Can also call `getDeclaringClass()` to figure out which `Class` the member is declared from.

Also, there are methods to retrieve a single member by passing in name and parameter types.


### Interacting with the members of the class/type

For an instance of a class, without the instance necessarily having to be a reference of that type, you can get or set on the field or invoke a method on that object using the `Field` and `Method` class.

Same applies for `Constructor` to create a new instance. You can also call `newInstance()` on an instance of a `Class` itself to call the default parameterless constructor, rather than having to get to the `Constructor` members for that class.
