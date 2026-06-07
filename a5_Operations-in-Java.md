🧮 Operators in Java: The Complete Reference
Because Java is a strongly-typed, compiled language, operators do not just compute values—they strictly evaluate, 
coerce, or reject data types at compile time.

1. Arithmetic Operators
Used to perform standard mathematical calculations.

<img width="773" height="469" alt="Screenshot 2026-06-07 at 7 19 12 AM" src="https://github.com/user-attachments/assets/e380731e-3784-4542-bf55-a86a75a22984" />


⚠️ The Java Division Trap (Integer vs. Floating-Point)
In JavaScript, 5 / 2 evaluates to 2.5. In Java, the data types of the operands determine the result type:

Integer Division: If both numbers are integers (int, long, byte, short), Java truncates the decimal completely.

Floating-point Division: At least one operand must be a float or double to preserve the decimal.

```
int result1 = 5 / 2;     // Evaluates to 2 (Integer division drops the .5)
double result2 = 5.0 / 2; // Evaluates to 2.5 (Floating-point division)
double result3 = 5 / 2.0; // Evaluates to 2.5
```

<img width="793" height="571" alt="Screenshot 2026-06-07 at 7 20 28 AM" src="https://github.com/user-attachments/assets/01938e32-11b1-4dc1-bd44-163067b87876" />


🧠 Prefix vs. Postfix Execution Memory
Prefix (++a): Increments the value before evaluating the expression.

Postfix (a++): Evaluates the expression using the current value before incrementing it in memory.


```
int x = 5;
int y = ++x; // x becomes 6, y becomes 6

int a = 5;
int b = a++; // b gets the current value (5), then a becomes 6
```


3. Assignment & Compound Operators
Used to assign values to variables. Compound operators combine an arithmetic operation with an assignment.

<img width="742" height="383" alt="Screenshot 2026-06-07 at 7 21 26 AM" src="https://github.com/user-attachments/assets/ffc87ce1-8099-4dca-9c92-eb1d3570a06e" />



🛠️ Hidden Java Benefit: Implicit Casting
Compound assignment operators automatically perform implicit type casting if the result type is narrower than the variable type:

```
byte b = 10;
// b = b + 5;  // ❌ COMPILE ERROR: 5 is an int, result becomes an int!
b += 5;        //  Implicitly compiled as b = (byte)(b + 5)
```

<img width="742" height="383" alt="Screenshot 2026-06-07 at 7 21 26 AM" src="https://github.com/user-attachments/assets/fa15c9ae-a748-4189-9286-23d10213613d" />



🚨 CRITICAL WARNING: No === in Java
Java does not have a triple-equals (===) operator because it is statically typed; you cannot compare an int to a boolean anyway.

However, == behaves radically differently for Primitives vs Objects:

When comparing primitives, == checks if their raw stack values are equal.

When comparing objects (like Strings or custom classes), == checks if they point to the exact same memory reference address on the heap, 
not if their content matches.



```
// Primitives
int num1 = 10;
int num2 = 10;
System.out.println(num1 == num2); // true

// Objects (Strings)
String str1 = new String("hello");
String str2 = new String("hello");
System.out.println(str1 == str2);      // ❌ false! (They point to different heap objects)
System.out.println(str1.equals(str2)); //  true! (Always use .equals() for objects)

```


<img width="788" height="588" alt="Screenshot 2026-06-07 at 7 22 04 AM" src="https://github.com/user-attachments/assets/eff82c37-c3d8-4701-bbf3-731cbc4930db" />



⚡ Short-Circuit Evaluation
Java uses short-circuit evaluation for execution optimization:

In an && operation, if the first expression is false, Java won't even evaluate the second expression 
(because the whole statement is guaranteed to fail).

In an || operation, if the first expression is true, Java skips evaluating the second expression.


```
String name = null;
// Short-circuit prevents a NullPointerException! 
// Because name == null is true, the JVM skips checking name.length()
if (name == null || name.length() == 0) {
    System.out.println("Empty string identifier");
}
```


<img width="795" height="585" alt="Screenshot 2026-06-07 at 7 23 55 AM" src="https://github.com/user-attachments/assets/75bdbefc-0457-42e0-9902-de6bcfae02a2" />


<img width="798" height="357" alt="Screenshot 2026-06-07 at 7 24 03 AM" src="https://github.com/user-attachments/assets/460d1f81-aae1-4964-b6d6-a0459dc7ead4" />



```
int flags = 0b0011; // 3 in decimal
int mask  = 0b0101; // 5 in decimal

int andResult = flags & mask; // 0b0001 (1 in decimal)
int leftShift = flags << 1;   // 0b0110 (6 in decimal)
```

<img width="832" height="464" alt="Screenshot 2026-06-07 at 7 24 42 AM" src="https://github.com/user-attachments/assets/7fda00f1-b343-4bf9-ae4c-0de1afdd7224" />


<img width="823" height="709" alt="Screenshot 2026-06-07 at 7 25 01 AM" src="https://github.com/user-attachments/assets/f9498591-1bc6-4b58-bcfe-433583b1c605" />


🔍 Cheat Sheet Summary Matrix for Github Commit
Always watch out for integer division: 5 / 2 = 2.

Never use == for String content verification: Always use .equals().

Logical operations are short-circuited: Keep this in mind when staging assertions that throw exceptions.

Ternary data structures are rigidly matched: Ensure true/false paths return equivalent schemas.










