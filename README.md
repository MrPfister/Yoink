# Yoink
A Python library that when attached to a running process, can scan the loaded modules for any that expose function signatures that may enable the bypass or extraction of login credentials.

## Implementation notes
Yoink works by recursively introspecting modules via getmembers(...) and then scanning over the internal __code__ object of derived members objects subclassed from the Callable type. There are some checks as some Callable classes within Python do not contain code; usefully when implemented outside the standard def approach.

This is a brute force approach and technical example of how easy it is to bypass login functionality.

For example, if a module implemented:

```python
def valid_user(username: str, password: str) -> bool:
  ...Do logic
  return False
```

Yoink can detect this function is performing a security operation by its __code__ co_varnames signature and wrap it, thus potentially bypassing security checks .
