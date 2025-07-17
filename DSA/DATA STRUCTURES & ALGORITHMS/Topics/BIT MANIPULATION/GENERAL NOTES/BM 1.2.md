SET BITS KA MTLB HOTA HAI KI KITI BITS 1 HAI

→ IN BUILT FUNCTION HOTA HAI YE

![image 35.png](../../../../../Images/image%2035.png)

→

![image 1 13.png](../../../../../Images/image%201%2013.png)

![image 2 11.png](../../../../../Images/image%202%2011.png)

→X and X+1 mein kuch part same rahega kuch part flipped rahega

→ ye flip start hoga X+1 ki last set bit se

![image 3 9.png](../../../../../Images/image%203%209.png)

  

![image 4 8.png](../../../../../Images/image%204%208.png)

  

Since jabh humne & kiya X , X-1 k bich mein

→ jo flipped wala part vo 0 hua which mean X ki last set bit bhi 0 hui

→ Ye processs karte raho jabh tak pura number 0 na ho

Utni hi iterations lagegnhi jitni set bits hain

**⇒ TO CALCULATE THE NUMBER OF SET BITS**

![image-1726027808352.jpg9083618994850271616.jpg](../../../../../Images/image-1726027808352.jpg9083618994850271616.jpg)

**Counting Set Bits (Brian Kernighan's Algorithm)**

```Plain
	public class CountSetBitsKernighan {
		public static void main(String[] args) {
			int num = 29; // Example number, 11101 in binary, has 4 set bits
			System.out.println("Number of set bits in " + num + ": " + countSetBits(num));
		}

		public static int countSetBits(int num) {
			int count = 0;
			while (num > 0) {
				num &= (num - 1); // Clear the rightmost set bit
				count++;
			}
			return count;
		}
	}
```

![image 5 7.png](../../../../../Images/image%205%207.png)

![image 6 7.png](../../../../../Images/image%206%207.png)

1st approach→ mein kya hota hai ki upar btaya hai

2nd Approach:

Ek kam kar skte given number ki msb k sath and bad mein sare elements 1 one krdete hain pehle!

Wo kaise kar sakte hain??? Well with the use of Or operator

**⇒AGAR KUCH AESA KRNA HO KI 0 HAI TOH 1 KARDO AND 1 HAI TOH BHI 1 KARDO TOH IN THAT CASE OR OPERATOR KI HELP LENA SUITABLE REHTA HAI**

![image 7 6.png](../../../../../Images/image%207%206.png)

![image 8 6.png](../../../../../Images/image%208%206.png)

![image 9 5.png](../../../../../Images/image%209%205.png)

  

  

  

  

  

![image-1726032570912.jpg4394474837001587086.jpg](../../../../../Images/image-1726032570912.jpg4394474837001587086.jpg)

![image-1726032603842.jpg4369316398921132591.jpg](../../../../../Images/image-1726032603842.jpg4369316398921132591.jpg)

  

![image-1726036164335.jpg5986505475427167958.jpg](../../../../../Images/image-1726036164335.jpg5986505475427167958.jpg)

→Sabko one kar diya and uske bad + add karke divide by two kar diya

![image 10 5.png](../../../../../Images/image%2010%205.png)

![image 11 5.png](../../../../../Images/image%2011%205.png)

![image 12 5.png](../../../../../Images/image%2012%205.png)

![image 13 5.png](../../../../../Images/image%2013%205.png)

[https://leetcode.com/problems/minimum-bit-flips-to-convert-number/?envType=daily-question&envId=2024-09-11](https://leetcode.com/problems/minimum-bit-flips-to-convert-number/?envType=daily-question&envId=2024-09-11)

⇒JABHI BHI HUM XOR KRTE HAIN TOH SAME SAME OFF(0) HOJATA HAI DIFFERENT WALE ON(1) HOJATE HAIN. TOH ISSE PATA LAGA JATA KITNI DIFFRENT BITS HAI BY COUNT THE SET BITS OF THE OUTPUT OF XOR.

APPROACH 1-

```C++
int minBitFlips(int start, int goal) {
        int x=start^goal;
        int count=0;
        while(x>0){
            x=x&(x-1);
            count++;
        }
        return count;
    }
```

APPROACH 2-

  

![image 14 5.png](../../../../../Images/image%2014%205.png)

![image 15 5.png](../../../../../Images/image%2015%205.png)

XOR IS COMMUATIVE TOO

  

![image 16 4.png](../../../../../Images/image%2016%204.png)

→Assume tumhe koi number given hai ! Jaise 5 And tumhe And tumhe uski last but check karni hai ki wo set hai ya nahi

→5&1→ 0 bit k alawa sari bits neutralise hojaegi and last bit se pata lagega since 1 ki last bit set hoti hati and answer ki bhi last bit set hai mtlb number ki last bit set hai and otherwise for 0

![image-1726037632380.jpg2066226685002483430.jpg](../../../../../Images/image-1726037632380.jpg2066226685002483430.jpg)

  

```C++
\#include <vector>
\#include <iostream>
using namespace std;

vector<int> findTwoUnique(vector<int>& nums) {
    // Step 1: XOR all the numbers
    int xor_result = 0;
    for (int num : nums) {
        xor_result ^= num;
    }

    // Step 2: Find any set bit in xor_result (e.g., the rightmost set bit)
    int set_bit = xor_result & -xor_result;  // This isolates the rightmost set bit

    // Step 3: Partition the array into two groups and XOR within each group
    int unique1 = 0, unique2 = 0;
    for (int num : nums) {
        if (num & set_bit) {
            unique1 ^= num;  // XOR for numbers with the set bit
        } else {
            unique2 ^= num;  // XOR for numbers without the set bit
        }
    }

    return {unique1, unique2};  // Return the two unique numbers
}

int main() {
    vector<int> nums = {1, 2, 1, 3, 2, 5};
    vector<int> result = findTwoUnique(nums);

    cout << "The two unique numbers are: " << result[0] << " and " << result[1] << endl;
    return 0;
}
```

![image 17 4.png](../../../../../Images/image%2017%204.png)

![image-1726039136710.jpg3261830735214726775.jpg](../../../../../Images/image-1726039136710.jpg3261830735214726775.jpg)

![image 18 4.png](../../../../../Images/image%2018%204.png)

JABH SAREE MAX EK HI SUBARRAY MEIN AA JAYENGE

## **MODULAR ARITHMETIC**

![image 19 3.png](../../../../../Images/image%2019%203.png)

![image 20 3.png](../../../../../Images/image%2020%203.png)

![image 21 3.png](../../../../../Images/image%2021%203.png)

![image 22 3.png](../../../../../Images/image%2022%203.png)

⇒BUT YE NUMBER CHOTE NAHI HAI

⇒But 2 bade numbers multiply honge in that case Range bahar hojaegi int type se

⇒Small Numbers mein koi dikkat nahi hai but Big numbers mein dikkat aegi

**⇒INTEGER BUCKET OVERFLOW**

![image 23 3.png](../../../../../Images/image%2023%203.png)

![image 24 3.png](../../../../../Images/image%2024%203.png)

![image 25 3.png](../../../../../Images/image%2025%203.png)

![image 26 2.png](../../../../../Images/image%2026%202.png)

ALWAYS TRUE

FOR PRODUCT WE CAN USE THIS FORMULA

![image 27 2.png](../../../../../Images/image%2027%202.png)

  

FOR SUBTRACTION

![image 28 2.png](../../../../../Images/image%2028%202.png)

  

![image 29 2.png](../../../../../Images/image%2029%202.png)

![image 30 2.png](../../../../../Images/image%2030%202.png)

![image 31 2.png](../../../../../Images/image%2031%202.png)

![image 32 2.png](../../../../../Images/image%2032%202.png)

This will do the trick