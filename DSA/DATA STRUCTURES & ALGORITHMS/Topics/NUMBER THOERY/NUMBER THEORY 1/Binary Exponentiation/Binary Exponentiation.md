WHY THE pow(a,b) sucks!

The key points regarding the power function in C++ and why it may be considered suboptimal, particularly `std::pow`:

### Key Points:

1. **Precision Issues**:
    - `std::pow` operates on floating-point numbers (`double`), leading to potential precision errors, especially with large or small values.
2. **Performance**:
    - The function is computationally intensive due to overhead from handling floating-point arithmetic, making it less efficient for simple power calculations.
3. **Integer Power Calculations**:
    - When calculating powers of integers, `std::pow` converts integers to `double`, which can result in precision loss.
4. **Lack of Specialized Functions**:
    - C++ lacks built-in integer power functions, forcing reliance on `std::pow` even when it's not ideal.
5. **Alternative Integer Power Function**:
    - For integer powers, implementing a custom function using exponentiation by squaring is recommended for efficiency and accuracy.

![402B8D59-C07A-40CF-B7E7-2F3A1A9848C4.png](../../../../../../Images/402B8D59-C07A-40CF-B7E7-2F3A1A9848C4.png)

![948FB851-9B91-421C-A2E9-14E56B0E777C.png](../../../../../../Images/948FB851-9B91-421C-A2E9-14E56B0E777C.png)

KYON KIYA WELL?

Divide between two integers in C++ is always an integer and and because of that problem ati hai!

![image-1727075635988.jpg5374904922214537154.jpg](../../../../../../Images/image-1727075635988.jpg5374904922214537154.jpg)

  

TOH HUM KHUD KA POWER FUNCTION BNAENGE AB

ARE KYA BAT HAI SOURAV SAHI JA RAHE HO!

YAHAN FLOOR VALUE LENE HOTI HAI B/2 ki

![C4FD61DD-63EA-44D8-B413-8FB2B7AA2343.png](../../../../../../Images/C4FD61DD-63EA-44D8-B413-8FB2B7AA2343.png)

This will work!

Tc→ O(log N)

STL KA POWER FUNCTION CHUTIYA HOTA HAI

Ye niche wala code chutiya hai

![79480D1C-72DE-492E-9099-AD05F9BB74B0.png](../../../../../../Images/79480D1C-72DE-492E-9099-AD05F9BB74B0.png)

Isko TC O(N) kyonki subproblems are getting caluclated again and again!

  

---

## MOUDLAR ARITHMETIC WITH BINARY EXPONENTIATION

→Agar Number jada bada hojata hai in that case mujhe Modular Arithmetic ki yahan bhi help leni padegi

  

![image-1727160902998.jpg1975423911624520338.jpg](../../../../../../Images/image-1727160902998.jpg1975423911624520338.jpg)

![image-1727162053518.jpg2020460676638170883.jpg](../../../../../../Images/image-1727162053518.jpg2020460676638170883.jpg)

![image-1727162066288.jpg7115691553341961157.jpg](../../../../../../Images/image-1727162066288.jpg7115691553341961157.jpg)

  

![image-1727162080477.jpg1257593541261118246.jpg](../../../../../../Images/image-1727162080477.jpg1257593541261118246.jpg)

![E8A0CF52-D254-497A-8ED0-6DF36E032AA3.png](../../../../../../Images/E8A0CF52-D254-497A-8ED0-6DF36E032AA3.png)

→const int Mod aese likhne se kaffi fast hojata hai

→

![260BF8FA-1D9C-4A63-ACB9-FFA0DF1CE60D.png](../../../../../../Images/260BF8FA-1D9C-4A63-ACB9-FFA0DF1CE60D.png)

→ SO WHEN THE NUMBER IS BIG WE’RE USING THE Modular Arithmentic in Binary Exponentiation

→AND