In Python, opening files using context managers is a recommended approach to ensure proper handling of resources, such as files. The `with` statement is used to create a context manager, which automatically takes care of opening and closing the file. When the code block within the `with` statement finishes executing, the file is automatically closed, even if an exception occurs, ensuring efficient resource management and preventing resource leaks.

```python
# Opening a file using a context manager 
file_path = "example.txt" 
with open(file_path, "r") as file:
	content = file.read()
	print(content) 
# File is automatically closed outside the 'with' block`
```

[[python]]