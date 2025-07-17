### 1. **Bitwise Operators**:

- **Operate on the individual bits** of integer values (binary representation of numbers).
- Work with **integers**.
- Compare corresponding bits of two operands (e.g., 0101 & 0011).

### Common Bitwise Operators:

- `&` (Bitwise AND)
- `|` (Bitwise OR)
- `^` (Bitwise XOR)
- `~` (Bitwise NOT)
- `<<` (Left Shift)
- `>>` (Right Shift)

### 2. **Logical Operators**:

- **Operate on entire boolean values** (`true`/`false`).
- Used with **boolean expressions** (conditions) and return a boolean result.
- Used in conditions (like `if` statements) and typically compare the truthiness of expressions.

### Common Logical Operators:

- `&&` (Logical AND)
- `||` (Logical OR)
- `!` (Logical NOT)

YE DEKHA YAHAN KI YE 2 BAR LIKHE GAYE HAIN!

### Key Differences:

1. **Operands**:
    - **Bitwise**: Work with integers (binary values).
    - **Logical**: Work with boolean values (`true`/`false`).
2. **Behavior**:
    - **Bitwise**: Perform operations on **individual bits** of the operands.
    - **Logical**: Perform operations on **entire expressions** and treat them as `true` or `false`.
3. **Short-Circuiting** (Logical only):
    - **Logical AND (**`**&&**`**) and OR (**`**||**`**)** can short-circuit. This means if the result is determined from the first operand, the second one won't be evaluated.
    - **Bitwise operators** do not short-circuit. They always evaluate both operands completely.

**HOW IS BITWISE OPERATORS APPLIED??**

Vo na incoming input k bit by bit par lagta hai and on the other hand logical operator incoming input value ki truthy/falsy par lagta hai

Example 3||6⇒ 1; 3|6⇒7

  

```C++
bool a = true;
bool b = false;
if (a || b) {
// Since a is true, b is never evaluated.
}
```

![image 34.png](../../../../../Images/image%2034.png)

YAHAN PAR EK HI CHARACTER HOTA HAI DHYAN RAKHNA

![image 1 12.png](../../../../../Images/image%201%2012.png)

**1. Bitwise AND (&)**

This operator performs a bitwise AND operation on two numbers. For each corresponding bit position, the resulting bit is 1 only if both operands have a 1 in that position.

**(e.g., 10 (1010) & 7 (0111) = 2 (0010))**

```Plain
 public class BitwiseAND {
 	public static void main(String[] args) {
 		int a = 5;  // 0101 in binary
 		int b = 3;  // 0011 in binary
 		int result = a & b; // 0001 in binary

 		System.out.println("Bitwise AND:");
 		System.out.println(a + " & " + b + " = " + result);
 	}
 }
```

**2. Bitwise OR (|)(PIPE OPERATOR BOLTE HAIN ISKO)**

The OR operator performs a bitwise OR operation. The resulting bit is 1 if at least one of the corresponding bits in the operands is 1.

**(e.g., 10 (1010) | 7 (0111) = 15 (1111))**

```Plain
 public class BitwiseOR {
 	public static void main(String[] args) {
 		int a = 5;  // 0101 in binary
 		int b = 3;  // 0011 in binary
 		int result = a | b; // 0111 in binary

 		System.out.println("Bitwise OR:");
 		System.out.println(a + " | " + b + " = " + result);
 	}
 }
```

**3. Bitwise XOR (^)**

The XOR operator performs a bitwise exclusive OR operation. The resulting bit is 1 if the corresponding bits in the operands are different.

**(e.g., 10 (1010) ^ 7 (0111) = 13 (1101))**

SAME SAME→ 0 AND DIFFERENT RESULTS IN 0

```Plain
  public class BitwiseXOR {
  	public static void main(String[] args) {
  		int a = 5;  // 0101 in binary
  		int b = 3;  // 0011 in binary
  		int result = a ^ b; // 0110 in binary

  		System.out.println("Bitwise XOR:");
  		System.out.println(a + " ^ " + b + " = " + result);
  	}
  }
```

**4. Bitwise NOT (~)**

The NOT operator performs a bitwise NOT operation on a single number. It flips all the bits.

**(e.g., ~5 (0101) = 6 (1010))**

```Plain
  public class BitwiseNOT {
  	public static void main(String[] args) {
  		int a = 5;  // 0101 in binary
  		int result = ~a; // 1010 in binary (in 32-bit, it's -6 due to two's complement representation)

  		System.out.println("Bitwise NOT:");
  		System.out.println("~" + a + " = " + result);
  	}
  }
```

![image 2 10.png](../../../../../Images/image%202%2010.png)

### **Shift Operators**

**1. Bitwise Left Shift (<<)**

- This operator shifts the bits of a number a specified number of positions to the left. Zeros are padded on the right. This is equivalent to multiplying the number by 2 raised to the power of the number of shifts.
- x<< n is equivalent to x * 2^N
- **Mnemonic**: "Left Shift, Multiply and Grow!" Since Pass mein aaraha hai na 


**(e.g., 5 (0101) << 2 = 20 (10100))**

```Plain
  public class BitwiseLeftShift {
  	public static void main(String[] args) {
  		int a = 5;  // 0101 in binary
  		int result = a << 1; // 1010 in binary

  		System.out.println("Bitwise Left Shift:");
  		System.out.println(a + " << 1 = " + result);
  	}
  }
```

![image 3 8.png](../../../../../Images/image%203%208.png)

**2. Right Shift (>>)**

- This operator shifts the bits of a number a specified number of positions to the right. The behavior for signed integers and unsigned integers differs. This is equivalent to Dividing the number by 2 raised to the power of the number of shifts.
- x >> n is equivalent to x /2^N
- **Mnemonic**: "Right Shift, Divide and Conquer!" Since dur jara hai na
    
    ```Plain
      public class BitwiseRightShift {
      	public static void main(String[] args) {
      		int a = 5;  // 0101 in binary
      		int result = a >> 1; // 0010 in binary
    
      		System.out.println("Bitwise Right Shift:");
      		System.out.println(a + " >> 1 = " + result);
      	}
      }
    ```
    

**Unsigned Right Shift (>>>)** Fills the vacated bits with zeros.


**(e.g., 5 (0101) >> 1 = 2 (0010))**

```Plain
  	public class BitwiseUnsignedRightShift {
  			public static void main(String[] args) {
  				int a = -5;  // 11111111111111111111111111111011 in binary (32-bit representation)
  				int result = a >>> 1; // 01111111111111111111111111111101 in binary

  				System.out.println("Bitwise Unsigned Right Shift:");
  				System.out.println(a + " >>> 1 = " + result);
  			}
  		}
```

![image 4 7.png](../../../../../Images/image%204%207.png)

---

_Complement is probably the most least used bitwise operator._

---

In binary form of any number every

- even number ends with `0`
- odd number ends with `1`
- power of 2 has only `1` bit. For ex - `16 = 10000`
- Divide by 2 operation is similar to right shift by 1.

→ (`14 / 2 = 7` is same as `14(1110) >> 1` = `0111`. Here `0111` == `7`)

- Power Operation
    
    - Power of 2 `(1 << x)`
    - LEFT SHIFT IS LIKE MULTIPLY x<< n is equivalent to x * 2^N
    
    **Example:**
    
    - `1 << 3` shifts `1` three positions to the left:
        - Binary representation: `00000001` becomes `00001000`, which is `8` in decimal.
        - So, 1<<3=23=8.
            
            1<<3=23=81 << 3 = 2^3 = 8
            
- Xor Operation
    - a ^ b = c, c ^ a = b, c ^ b = a

![image 5 6.png](../../../../../Images/image%205%206.png)

![image 6 6.png](../../../../../Images/image%206%206.png)

![image 7 5.png](../../../../../Images/image%207%205.png)

![image 8 5.png](../../../../../Images/image%208%205.png)

**MOST SIGNIFICANT SABSE PEHLE ATI HAI NA BHAI! AND LEAST SIGNIFICANT SABSE BAD MEIN ATI HAI NA BHAI!**

![image 9 4.png](../../../../../Images/image%209%204.png)

![image 10 4.png](../../../../../Images/image%2010%204.png)

![image 11 4.png](../../../../../Images/image%2011%204.png)

→Jo last bit hoti hai wo least significant bit hoti hai, so use 0th bit bolte hain and fir left mein chlo agli wali 1st bit fir then 2nd bit and so on

→ In case we get an array or string which obviously comes with indexes

![image 12 4.png](../../../../../Images/image%2012%204.png)

## ⇒ FROM BINARY TO DECIMAL WE CAN DO THIS

⇒Index → bit position→ Character Kya Hoga 0 ya 1 hamesha
YAHAN PE ARRAY K LIYE BAT HORAH HAI

![image 13 4.png](../../../../../Images/image%2013%204.png)

→

![image 14 4.png](../../../../../Images/image%2014%204.png)

**Now how to find this-? 2^(n-index-1)**

![image 15 4.png](../../../../../Images/image%2015%204.png)

![image 16 3.png](../../../../../Images/image%2016%203.png)

![image 17 3.png](../../../../../Images/image%2017%203.png)

BINARY OF ANY 2 is to power number

![image 18 3.png](../../../../../Images/image%2018%203.png)

![image 19 2.png](../../../../../Images/image%2019%202.png)

![image 20 2.png](../../../../../Images/image%2020%202.png)

‘0’ ki ascii value = 48 and ‘1’ ki ⇒ 49 so that’s how num is being answered

---

## ⇒DECIMAL TO BINARY

![image 21 2.png](../../../../../Images/image%2021%202.png)

![image 22 2.png](../../../../../Images/image%2022%202.png)

SHORTHANDS
 JLDI SE UPAR ULTA TYPE KA INDEXING KARDO AND JAHAN JAHAN ONE WAHAN PAR index ki power se two se mulyiply karke summation lelo!
![image 23 2.png](../../../../../Images/image%2023%202.png)

![image 24 2.png](../../../../../Images/image%2024%202.png)

![image 25 2.png](../../../../../Images/image%2025%202.png)