# Infix to Postfix Conversion in Python

## Aim
To convert an arithmetic expression from infix notation to postfix notation using stack operations in Python.

## Procedure
1. Define the set of valid operators and their corresponding precedence levels.
2. Traverse each character in the given infix expression.
3. If the character is an operand, add it directly to the output.
4. If the character is an opening parenthesis `'('`, push it onto the stack.
5. If the character is a closing parenthesis `')'`, pop from the stack to the output until an opening parenthesis is found.
6. If the character is an operator:
    - Pop operators from the stack to the output while the top of the stack has greater or equal precedence.
    - Push the current operator onto the stack.
7. After traversing the expression, pop any remaining operators from the stack to the output.
8. Return the final postfix expression.

## Program

```python
Operators = set(['+', '-', '*', '/', '(', ')', '^','&'])  
Priority = {'+':1, '-':1, '*':2, '/':2, '^':3,'&':0} 

def infixToPostfix(expression): 
    stack = [] 
    output = ''
    for char in expression: 
        if char not in Operators:
            output += char
        elif char == "(":
            stack.append(char)
        elif char == ")":
            while stack and stack[-1] != "(":
                output += stack.pop()
            stack.pop()
        else:
            while stack and stack[-1] != '(' and Priority[char] <= Priority[stack[-1]]:
                output += stack.pop()
            stack.append(char)
    while stack:
        output += stack.pop()
    return output

# Input and output
expression = input()
print("infix notation: ", expression)
print("postfix notation: ", infixToPostfix(expression))
```
## output
![Screenshot 2025-04-20 212510](https://github.com/user-attachments/assets/289fdbac-73a9-43de-b41f-5ca4c9550e2a)

## Result
The program successfully converts an infix expression to its corresponding postfix form using stack operations.
