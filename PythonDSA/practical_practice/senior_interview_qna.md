# Comprehensive Python Engineer Interview Practice Questions

## Core Python Concepts

1. **What's the difference between a list, tuple, and set in Python? When would you use each?**
2. **Explain list comprehensions and provide an example of when you'd use them instead of a regular for loop.**
    - they are optimized at the C level in python
    - no need to create temporary lists or vars
    - memory allocation happens once not incrementally thus faster for building lists especially of known sizes
    - Has a generator expression option to make it more memory efficient for larger data sets numbers_gen = (x for x in range(1000000))
    - Avoid nested comprehensions if possible
3. **What are generator expressions and when would you prefer them over list comprehensions?**
    - memory efficent iterators that generate values of demand rather than storying all the values in memory at once. it can be a function with a yield expression or list comprehension format with () braces
    - Use for largedatasets or for streaming data to preserve memory
    - Generators can only be iterated once
    - Values are only computed only when needed - Lazy Evaluation
    - The trade offs are u cant resuse so u have to recreate them  and no random access to elements
    - List comprehension are more better suited for small-med datasets and performance is more important than memory
    - test_gen = (x for x in range(10000))
4. **How do dictionary comprehensions work? Give an example from a banking context.**
    - students = []
    - schools = []
    - dic_comp = { name: school for name, school in zip(students, schools)}
    - dic comprehension as opposed to for loops are atomic operations which is advantageous when u want to avoid race conditions (thread safe), no partial states
5. **What's the difference between `==` and `is` in Python?**
    - One checks for value equality and the other checks that the two refrences point to the same object
6. **Explain the concept of mutability in Python. Which built-in types are mutable and which are immutable?**
    - One type cannot be changed after creation. Immutable objects create new objects when modified
    - immutable objects such as tuples are hashable which means they can be used as dictionary keys
    - A Class object can be made hashable by implemening the __**hash__ and __eq**__ methods as follows
    
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age
        
        # Making the class hashable
        def __hash__(self):
            return hash((self.name, self.age))
        
        def __eq__(self, other):
            return self.name == other.name and self.age == other.age
    ```
    
    - mutable = dict, lists, sets
    - immutable = tuple, strings
    - immutable objects are hashable thus can be used as dictionary keys.
    - Custom objects can be made hashable by implementing __hash__ and __**eq__ methods**
        
        ```python
        class Person:
        	def __init__(self, name, age):
        		self.name = name
        		self.age = age
        		
        	def __hash__(self):
        		return hash((self.name,self.age))
        	
        	def __eq__(self, other):
        		self.name == other.name and self.age == age
        ```
        
7. **How does variable scoping work in Python? Explain global, local, and nonlocal scopes.**
    - Python follows the LEGB rule for variable scope resolution
    - Local (function)
    - Enclosing (inside enclosing functions)
    - Global (at module level)
    - Built-in (Pythons Built in names)
8. **What are decorators in Python and how would you create a custom decorator?**
    - decorator is a way to modify or enhance a function or method without changing its logic directly by wrapping it in another function
    - Functions are Objects in python thus they can be passed as arguments to other functions be returned and assigned to variables
    - Allows reusability while preserving readability and maintainability
    - @ ⇒ def my_func: my_func = my_decorator(my_func)
        
        ```python
        def log_calls(func):
        	@functools.wraps(func) # Preserves original function metadata
        	def wrapper(*args, **kwargs):
        		print(f"{Calling {func.__name__} with args: {args}, kwargs = {kwargs}")
        		result = func(*args, **kwargs)
        		print(f"{func.__name__} returned: {result}")
        		return result
        	return wrapper
        
        @log_calls
        def add(x, y):
        	return x+y
        ```
        
    - Common Use cases
        - logging
        - timing/profiling
        - Caching
        - authorization
        - input validation
9. **Write a function that takes a list of transaction amounts and returns the average, using only built-in Python functions.**
    
    ```python
    transactions = []
    
    def average_transactions(transactions: list) -> float:
    		count = len(transactions)
    		if count == 0:
    			return 0.0
    			
    		return sum(transactions)/count
    ```
    
10. **How would you use `enumerate()` to process a list of transactions with their indices?**
    
    ```python
    transactions = []
    processed = []
    for i, transaction in enumerate(transactions: list) -> list:
    	processed.append((i,transaction))	
    
    ```
    

## **Object-Oriented Programming**

1. **What are the four main principles of OOP and how are they implemented in Python?**
    - Polymorphism - Concrete Classes Implemented from the same abstract classes can have different implementations for the abstract methods or child classes can override parents methods
    - Inheritance - A new class inherits properties from an existing class which promotes code reuse
        - Child class can use parent method or override them or add news ones
        - super() used to call methods from parent class in child class
    - Abstraction - Hiding Complex implementation details and only exposing necessary features or functionality of an object
        - Using the Abstract Base Classes module to define interfaces and abstract methods that sub classes must implement
    - Encapsulation - bundling data and methods that operate on the data together within a single class and controlling access to the internal state of the object, hiding the implementation details
        - _protected
        - __private
2. **Explain method resolution order (MRO) in Python and why it matters for multiple inheritance.**
    - its the sequence for which the python interpreter searches for a method or  attribute  in a class hierachy
    - MRO allows a class to inherit attributes and methods from multiple classes in a consistent fashion ensuring predictability and avoiding ambiguity
3. **What are dunder (double underscore) methods? Give examples of at least 5 common ones and their purposes.**
4. **When would you use class methods versus static methods? Provide examples.**
5. **Implement a `BankAccount` class with methods for deposit, withdrawal, and balance checking, including appropriate error handling.**
6. **What is the `@property` decorator and when would you use it?**
7. **Explain the concept of composition versus inheritance and when you'd choose one over the other.**
8. **How would you implement a custom context manager for database connections?**
9. **What is method overriding in Python? Provide an example.**
10. **Design a class hierarchy for different types of banking products (accounts, loans, credit cards, etc.).**

## **File Handling**

1. **What's the preferred way to open and close files in Python?**
2. **How would you read a large CSV file of banking transactions efficiently without loading the entire file into memory?**
3. **Write code to parse a JSON file containing banking transaction data.**
4. **Compare and contrast the `json` module with the `pickle` module.**
5. **How would you write a function to watch a directory for new files and process them as they appear?**
6. **What's the difference between binary and text mode when opening files?**
7. **Explain how you would handle different character encodings when working with files.**
8. **How would you use the `pathlib` module instead of `os.path` functions?**
9. **Write code to serialize a Python object to JSON, handling non-serializable types.**
10. **How would you implement a file-based logging system for banking transactions?**

## **Error Handling**

1. **What's the difference between exceptions and syntax errors in Python?**
2. **Explain the try/except/else/finally blocks and when you'd use each component.**
3. **How would you create and raise custom exceptions for a banking application?**
4. **What's wrong with catching all exceptions with a bare `except:` clause?**
5. **Design an error handling strategy for a financial data processing pipeline.**
6. **How would you debug a Python application that's failing in production?**
7. **What tools or techniques would you use to trace the origin of an exception?**
8. **How do you handle exceptions in multithreaded or asynchronous code?**
9. **Write code to retry a network operation with exponential backoff.**
10. **How would you implement a graceful degradation strategy for a banking API when dependent services are down?**

## **Memory Management**

1. **Explain Python's memory management model and garbage collection.**
2. **What are the implications of Python's pass-by-reference behavior?**
3. **How would you identify and fix memory leaks in a Python application?**
4. **What is reference counting in Python and what are its limitations?**
5. **How would you optimize memory usage when processing large datasets?**
6. **Explain the concept of weak references and when you might use them.**
7. **What memory profiling tools would you use to analyze a Python application?**
8. **How does the `del` statement work in Python and when should it be used?**
9. **What are circular references and why are they problematic?**
10. **How would you implement a caching mechanism that avoids memory issues?**

## **Language Paradigm**

1. **Describe the multiple programming paradigms that Python supports.**
2. **What functional programming features does Python offer?**
3. **How would you implement a map-reduce pattern in Python?**
4. **What are lambda functions and what are their limitations?**
5. **How would you use the `functools` module for functional programming?**
6. **Compare imperative and declarative programming styles in Python.**
7. **What are pure functions and why are they important?**
8. **How would you implement function composition in Python?**
9. **Explain immutability and its benefits in programming.**
10. **How would you design a banking function that adheres to functional programming principles?**

## **Concurrency & Parallelism**

1. **What's the difference between concurrency and parallelism?**
2. **Explain the Global Interpreter Lock (GIL) and its implications.**
3. **When would you use threading versus multiprocessing in Python?**
4. **How does asyncio work and when would you use it instead of threading?**
5. **Implement a function that processes multiple API requests concurrently.**
6. **What synchronization primitives does Python provide for thread safety?**
7. **How would you implement a producer-consumer pattern for transaction processing?**
8. **What are the challenges in debugging concurrent code?**
9. **How would you test a multithreaded application?**
10. **Design a system to process real-time banking transactions with high throughput requirements.**

## **API Development**

1. **Compare and contrast REST and GraphQL APIs.**
2. **How would you design a RESTful API for a banking system?**
3. **What HTTP status codes would you use for different scenarios in a banking API?**
4. **How would you implement authentication and authorization for an API?**
5. **Design an API endpoint that handles pagination for large result sets.**
6. **What are the security considerations for developing a banking API?**
7. **How would you version your API?**
8. **What tools or frameworks would you use for API documentation?**
9. **How would you implement rate limiting for an API?**
10. **Describe how you'd test an API before deployment.**