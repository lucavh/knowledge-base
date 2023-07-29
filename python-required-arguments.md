You must list all your required arguments (those WITHOUT default values) before your optional arguments (those WITH default values).

```python
def grapplingHook(
	direction: float, 
	angle: float, 
	cry: str = ""
) -> None:
    print(f"Direction {direction}, Angle {angle}, Cry {cry}")

grapplingHook(angle=90, direction=43.7)
```

[[python]]