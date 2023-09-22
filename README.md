# Yoink
A Python library that when attached to a running process, can scan the loaded modules for any that expose function signatures that may enable the bypass or extraction of login credentials.

This works by introspecting modules via getmembers(...) and then scanning the internal __code__ object
