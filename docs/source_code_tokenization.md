# Source Code Tokenization

Source Code Tokenization applies BPE to programming languages, balancing standard keyword identification (like `if`, `class`, `return`) with the unique naming of variables and functions.

## Mechanism
1. **Identifier Extraction**: Extracts camelCase, snake_case, and standard programming terms.
2. **Whitespace Preservation**: Custom pre-tokenizers protect indentation spaces (critical for Python blocks).
3. **Merging Constraints**: Prevents syntax boundaries (e.g. operators like `==`, `!=`) from merging with alphanumeric characters.

```mermaid
graph TD
    A[Code: 'def test_func():'] --> B[Regex Splitter]
    B --> C['def', ' ', 'test_func', '(', ')', ':']
    C --> D[BPE Merges inside Identifiers]
    D --> E[Tokens: 'def', ' ', 'test', '_', 'func', '(', ')', ':']
```

## Advantages
- **Syntactic Safety**: Preserves syntax tokens cleanly.
- **Compact Code Representation**: Commonly used framework methods and keywords are mapped to single tokens.

## Limitations
- **Variable Fragility**: Custom variable names may be split into many small tokens, causing code representation to bloat.

[Back to README](../README.md)
