Every thread in your program has a call stack assigned to it. The call stack contains the values of local primitive variables and references to objects on the heap. When your thread is executing code that calls a function or a method, a new Stack frame is created and added to the stack. When the function of method return (with a value or none), the new frame is popped from the Stack.

### Pass by Value

Calling a function pushes a new frame into the stack and primitive values are passed on the function invocation. There primitive values live on the stack, more precisely, on the current frame of the stack and are **copied** to the new frame. 

### Pass by reference

Calling a function pushes a new frame into the stack and object references are passed on the function invocation. These objects live on the heap, therefor their real values are **not copied** to the new frame, instead the reference to the object that lived on the first frame is passed to the new frame.

### Considerations

The stack is a data structure with a max size, reaching this max size causes and overflow, and a call stack overflow will crush your program. Modern runtimes handle call stacks with extremely large max sizes so these cases of stack overflow are rare. 