Reflection is a feature in Java and some other languages that provides a way to get information about classes, their definitions and objects during run time.
Reflection allows us to get metadata that otherwise we could not have gotten using the languages normal means. 
### Features

1. Getting information about class methods and fields at runtime - get a list of all existing methods and fields inside a class (with names), the type of arguments they accept, etc.. 
2. Creating new instances of a class even calling private constructors.
3. Getting and setting object fields directly regardless of their access modifiers.
### Uses

1. Reflection allows the runtime manipulation of application behavior.
2. It helps debugging and testing programs by directly accessing fields, methods and constructors.
3. It allows API users to call a method by name in advance. i.e. run a method by name from a string argument.