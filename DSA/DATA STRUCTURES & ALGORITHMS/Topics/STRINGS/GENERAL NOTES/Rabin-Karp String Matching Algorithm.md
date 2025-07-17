Let's Start with a problem then

Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

**Example 1:**

**Input:** haystack = "sadbutsad", needle = "sad"
**Output:** 0
**Explanation:** "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.

**Example 2:**

**Input:** haystack = "leetcode", needle = "leeto"
**Output:** -1
**Explanation:** "leeto" did not occur in "leetcode", so we return -1.

**Constraints:**

- `1 <= haystack.length, needle.length <= 104`
- `haystack` and `needle` consist of only lowercase English characters.


```c++
  int strStr(string haystack, string needle) {
        size_t pos=haystack.find(needle);
        if(pos != string::npos){
            return int(pos);
        }
        return -1;
    }
```

Time Complexity: O()
Space Complexity: O()


**Basically Searching a pattern in a String!**

![Rabin-Karp String Matching Algorithm-20250109100325263.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109100325263.webp)


**So Problems like where We have to search Some string in other string! The first Thing to come in my mind should be!**
- Brute Force
- KMP
- Rabin Carp
- Tries

![Rabin-Karp String Matching Algorithm-20250109100443137.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109100443137.webp)

![Rabin-Karp String Matching Algorithm-20250109100529554.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109100529554.webp)


So In the worst Case it is going to be O(N * M)

In each case we're going to compare two string strings right which has a complexity of O(s.size());
So It's a headache for me right?? How about we just compare two numbers that's an operation of O(1)

STRING -> CONVERTED 

![Rabin-Karp String Matching Algorithm-20250109101310689.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101310689.webp)

FOR NEXT ITERATION WE CAN USE SLIDING WINDOW RIGHT!!

![Rabin-Karp String Matching Algorithm-20250109101453408.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101453408.webp)

![Rabin-Karp String Matching Algorithm-20250109101609492.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101609492.webp)

BUT THERE IS A PROBLEM WITH THIS APPROACH! WHICH IS THAT!

WE CAN COME ACROSS **SPURIOUS HITS!!**

![Rabin-Karp String Matching Algorithm-20250109101815026.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101815026.webp)

![Rabin-Karp String Matching Algorithm-20250109101848230.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101848230.webp)

![Rabin-Karp String Matching Algorithm-20250109101912699.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109101912699.webp)

ORDER ALSO MATTERS SO HASHING SHOULD NOT BE THE RIGHT APPROACH TO SOLVE THIS PROBLEM!

![Rabin-Karp String Matching Algorithm-20250109103228510.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109103228510.webp)


![Rabin-Karp String Matching Algorithm-20250109103251649.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109103251649.webp)

![Rabin-Karp String Matching Algorithm-20250109103342652.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109103342652.webp)

But Then n can be so large??

![Rabin-Karp String Matching Algorithm-20250109103407718.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109103407718.webp)

Since we did find that number can be very large we can take MOD with a prime number ! But then the Values can collide once again!

![Rabin-Karp String Matching Algorithm-20250109103500408.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109103500408.webp)

![Rabin-Karp String Matching Algorithm-20250109104528814.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109104528814.webp)


![Rabin-Karp String Matching Algorithm-20250109104552861.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109104552861.webp)

Dono hi cases mein m=3 ka use karke hash create kiya!

NEXT HASH???

WE'LL USE SLIDING WINDOW HERE AS WELL!

THIS IS FOR NEW HASH 
 ![Rabin-Karp String Matching Algorithm-20250109105400063.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109105400063.webp)

![Rabin-Karp String Matching Algorithm-20250109105542754.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109105542754.webp)

![Rabin-Karp String Matching Algorithm-20250109105610856.webp](../../../../../Images/Rabin-Karp%20String%20Matching%20Algorithm-20250109105610856.webp)

