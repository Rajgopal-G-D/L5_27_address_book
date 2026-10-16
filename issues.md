# Lab 5: Static Code Analysis — Issues and Fixes

| Issue | Type | Original Line(s) | Description | Fix Approach |
|---|---|---:|---|---|
| Weak MD5 hashing | Security — High | 19 | MD5 is considered unsuitable for security-sensitive hashing. | Replaced MD5 with SHA-256. The six-character ID remains unsuitable as a secure token. |
| Unsafe pickle deserialization | Security — Medium | 67 | Loading an untrusted pickle file may execute arbitrary code. | Replaced pickle serialization and deserialization with JSON. |
| Hardcoded password-like constant | Security — Low | 6 | The `SYNC_PASSWORD` constant is embedded in the source code and is unused. | Removed the unused constant. |
| Unnecessary pickle import | Security — Low | 3 | The pickle module introduces a risky deserialization mechanism in this application. | Removed the import after switching to JSON. |
| Broad exception handling | Code quality | 34 | `except Exception` can catch unrelated programming errors. | Changed the handler to `except KeyError`. |
| Non-standard naming conventions | Code style | 10–65 | CamelCase function and parameter names violate conventional Python `snake_case` naming. | Renamed functions and parameters consistently. |
| Missing docstrings | Code quality | Multiple | Functions and the module lack explanatory docstrings. | Added module and function docstrings. |
| Missing text encoding | Code quality | 54 | Opening a text file without an explicit encoding may behave differently across environments. | Specified UTF-8 for text file operations. |
| Inefficient directory iteration | Code quality | 49 | Iterating over `range(len(names))` is less readable than direct enumeration. | Replaced it with `enumerate()`. |
| Whitespace and line-length violations | Code style | 23, 47, 84–85 | Several lines violate Flake8 formatting rules. | Corrected whitespace, blank lines, and long lines. |

Note: Line numbers refer to the original source and may change after modifications. Final verification was performed by rerunning Pylint, Bandit, and Flake8.
