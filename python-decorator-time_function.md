The `time_function` Python decorator is a utility that measures and logs the execution time of a function. By decorating a specific function with `@time_function`, you can automatically track the time it takes for the function to run and print or log the elapsed time. This decorator is useful for profiling and optimizing code, as it helps identify performance bottlenecks in functions.

```python
import time

def time_function(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        elapsed_time = end_time - start_time
        print(f"Function '{func.__name__}' took {elapsed_time:.5f} seconds to run.")
        return result
    return wrapper

@time_function
def some_function():
    # Simulate some time-consuming operation
    time.sleep(2)
    print("Function execution complete.")

some_function()
```

[[python]]