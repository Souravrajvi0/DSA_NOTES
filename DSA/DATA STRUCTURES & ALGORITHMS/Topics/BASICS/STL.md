![A3583D5E-3DD0-4EB1-B8EB-48AE2ECDC082.png](../../../../Images/A3583D5E-3DD0-4EB1-B8EB-48AE2ECDC082.png)

![D964970D-EC98-4243-B6B9-5CA7A5EB255F.png](../../../../Images/D964970D-EC98-4243-B6B9-5CA7A5EB255F.png)

→Funtions Jaise Sort!

→Class Jaise Vectors/Unordered_map/ etc. Classes Ko containers bhi bolte hain!

![9EFFA2D4-0BB5-4A17-9B14-43DA83AE3275.png](../../../../Images/9EFFA2D4-0BB5-4A17-9B14-43DA83AE3275.png)

→Jabh Koi 2 Values inseperable ho toh in that case we use pair class

→ Example jaise Mujhe Time Intervals Save karni hoti hai!

→

![FE1AF70F-B368-4391-935F-CD175985A51C.png](../../../../Images/FE1AF70F-B368-4391-935F-CD175985A51C.png)

→ pairs par comparison bhi jojata hai easily meaning ki pehle first elements compare hote hain and then second vale, lexicographically comparison hota hai!// kyonki unpe comparison operator hota hai!

→

![DAE9AEAA-7376-45FF-A21F-261C01509C51.png](../../../../Images/DAE9AEAA-7376-45FF-A21F-261C01509C51.png)

→

![98F62593-074E-4D35-A0F8-DF070D757D05.png](../../../../Images/98F62593-074E-4D35-A0F8-DF070D757D05.png)

→ sort function call kar skte hain pair par!

→ Sort call kar skte hain kisi bhi container par! Whether it’s an array or vector!

  

![16FD1302-917F-4FC4-94BE-DB76423697E6.png](../../../../Images/16FD1302-917F-4FC4-94BE-DB76423697E6.png)

![C3947A0E-5078-47E3-B21C-BDAB8AD1008D.png](../../../../Images/C3947A0E-5078-47E3-B21C-BDAB8AD1008D.png)

![1D65EFB6-D188-4EA5-AA42-53E528258601.png](../../../../Images/1D65EFB6-D188-4EA5-AA42-53E528258601.png)

→Iterators ka use karke hum Koi value kahin bhi dal skte hain!

→ yahan 3 dalne se hum values ko aage khiska denge!

![EFDD00B4-AA51-4B86-ABAC-7630FCAA6F0C.png](../../../../Images/EFDD00B4-AA51-4B86-ABAC-7630FCAA6F0C.png)

THIS IS O(N)

![E4727C55-BE2E-4019-BCAE-B20B5BE83D03.png](../../../../Images/E4727C55-BE2E-4019-BCAE-B20B5BE83D03.png)

Emplace mein curly brackets nahi lagate! But safe nahi hota emplace ko fir avoid hi kar skte hain!

![697CB5CE-25AE-4E39-850E-ADF3B91D4D31.png](../../../../Images/697CB5CE-25AE-4E39-850E-ADF3B91D4D31.png)

→ v.erase() Kinda deletes One element!// Size bhi kam hota hai

→v.clear() deletes the whole array!

→

![C3DADAC9-E478-4330-8800-C9C3D4B631A5.png](../../../../Images/C3DADAC9-E478-4330-8800-C9C3D4B631A5.png)

The `std::sort` function in C++'s Standard Template Library (STL) can **only be applied to random-access iterators**. This means it can be used on containers that support random-access iterators, such as:

- `std::vector`
- `std::array`
- C-style arrays (raw arrays)

// ye bhi dekh na Array and vector continous type hote hain memory k andar I guess uski vajah se we can do it!

However, it **cannot** be directly applied to containers like:

- `std::list`
- `std::set`
- `std::unordered_set`
- `std::map`
- `std::unordered_map`

These containers do not support random-access iterators, as their elements are not stored contiguously in memory, and their iterators do not allow access to elements by index.

For containers like `std::list`, you can use `std::list::sort`, which is a member function specifically designed for sorting lists. For associative containers like `std::set` and `std::map`, they maintain sorted order by their nature, so no sorting is needed.

![CF0F90D3-AD09-422A-BE6E-2B8052925019.png](../../../../Images/CF0F90D3-AD09-422A-BE6E-2B8052925019.png)

![0338D477-4E5D-4EEB-8513-FD13FBC7CF6C.png](../../../../Images/0338D477-4E5D-4EEB-8513-FD13FBC7CF6C.png)

![14E2C323-2A5C-48E9-BD6D-F0D5B07C6EC1.png](../../../../Images/14E2C323-2A5C-48E9-BD6D-F0D5B07C6EC1.png)

→ An ordered set will be sorted at any given point of time which means! Koi insertion / deletion k bad bhi ye map sorted rahega!

→To check if the set contains this element or not we can use contains functions on it!

- `**count**` works in all versions of C++ (starting from C++98) and returns an integer (either 0 or 1).
- `**contains**` is available starting from **C++20** and returns a boolean, making the intention clearer when checking for the presence of an element or key.

![66FA3D79-27D6-40C2-A78F-5DD7C3D462AD.png](../../../../Images/66FA3D79-27D6-40C2-A78F-5DD7C3D462AD.png)

Works!

→mySet.erase(3); // Removes element 3 from the set

![5DD7A94E-263A-419F-9A89-9679ED7C0E40.png](../../../../Images/5DD7A94E-263A-419F-9A89-9679ED7C0E40.png)

→Doesn’t work! We can’t use indexing with it!

→In case we create our own datatype then for us to use set/ map we need < function implemented // kyonki vo set / map hamesha sorted hoga na!

→

![6AA1083D-20EA-4CE3-B24C-DCFE106BA8B5.png](../../../../Images/6AA1083D-20EA-4CE3-B24C-DCFE106BA8B5.png)

• When you use `erase` on a vector, you typically provide an iterator pointing to the element you want to remove  
• Vectors allow random access, meaning you can use arithmetic operations on iterators (like   
`+` or `-`) to navigate through the elements.  
• For sets, you can use either an iterator or a value directly. The   
`erase` function can take an iterator pointing to the element or the value of the element you want to remove.

→ To get iterators in set It’s kinda Hard!

→

![D5D73CA6-1C31-402E-AF77-75E5397F278A.png](../../../../Images/D5D73CA6-1C31-402E-AF77-75E5397F278A.png)

This works

→

![204405AA-395B-4066-82FA-ABBC2F5534D5.png](../../../../Images/204405AA-395B-4066-82FA-ABBC2F5534D5.png)

This won’t , because The + operator is not defined

→

![F095FC7B-854C-4F0F-A409-078B75C48F59.png](../../../../Images/F095FC7B-854C-4F0F-A409-078B75C48F59.png)

This works!

Set iterators can move only one step at a time!

→

![9A5CC8AD-E5F3-44BA-A8AC-3395F1BABCA7.png](../../../../Images/9A5CC8AD-E5F3-44BA-A8AC-3395F1BABCA7.png)

→ A map stores key value pairs on the other hand Set only stores values!

![608C8374-02BE-482B-8455-72D72AB70425.png](../../../../Images/608C8374-02BE-482B-8455-72D72AB70425.png)

→

![C9B0ECC6-8C94-4735-B357-A1A2E21AB63B.png](../../../../Images/C9B0ECC6-8C94-4735-B357-A1A2E21AB63B.png)

![B074810C-09AC-49B7-9F7A-FBE6C162011B.png](../../../../Images/B074810C-09AC-49B7-9F7A-FBE6C162011B.png)

→So an array can’t have more than 1e^5 size and for a global array it’s 1e^7

→Even maps can’t have more than that!

→ So if we have a map of strings assume! Now The TC of inserting and searching will increase!  
If we have a string s of length L now TC will L*LogN  

→ The comparison of Integers happen in O(1)

→

![0C6FA1C6-1630-4B34-8EB6-9F520528AA1C.png](../../../../Images/0C6FA1C6-1630-4B34-8EB6-9F520528AA1C.png)

→ key important hoti hai!

→ sorting bhi key par hoti hai!

→

![795F6D06-383B-407C-99E7-710D4AAEF806.png](../../../../Images/795F6D06-383B-407C-99E7-710D4AAEF806.png)

→ We can also do here it→first this will also work and the values can be modified using these!  
  

![763139F9-DAAD-4BDC-8BA9-0727AFB39C5C.png](../../../../Images/763139F9-DAAD-4BDC-8BA9-0727AFB39C5C.png)

→

![F7A82F77-C83A-4B31-AC20-C38F36BB5F56.png](../../../../Images/F7A82F77-C83A-4B31-AC20-C38F36BB5F56.png)

→So Basic datatypes ko toh change karna hash function ko ata hai but complex datastructures ko nahi ata bro!

→ unordered set nahi banega pair ka! but set par chl jaega easily!

→When one or values have the same Hash It’s called collision!

→ Collision Makes our Code slower! Sometimes Unordered set TC of Insertion or searching can go upto O(N)

→

![4A038E6B-0E49-4A3C-B081-B88CFBA5478C.png](../../../../Images/4A038E6B-0E49-4A3C-B081-B88CFBA5478C.png)

→ In an unoredered map The value Doesn’t matter, So because of that! key par restrictions hai but value jo hai na wo kuch bhi ho skti hai! Mtlb value mein pair ,vector dal skta huon but key main toh basic data type hi dal skte hain!

→

![7FDEDAD4-2781-4E52-8A03-B9CE7C8F9D31.png](../../../../Images/7FDEDAD4-2781-4E52-8A03-B9CE7C8F9D31.png)

This will work

→

![0913042B-0984-4E62-8238-46C1EBEC036B.png](../../../../Images/0913042B-0984-4E62-8238-46C1EBEC036B.png)

Vector can be the value but never be the key!

→

![055AC20E-75FA-4A04-9516-425B77EEC3F0.png](../../../../Images/055AC20E-75FA-4A04-9516-425B77EEC3F0.png)

Works

→Hashability only matters in Unordered map and unordered set!

→

![3CA95E9B-7534-4C39-AA75-80CEFB231592.png](../../../../Images/3CA95E9B-7534-4C39-AA75-80CEFB231592.png)

→

![38C9E28B-971C-4D02-A9DF-C40E055492D9.png](../../../../Images/38C9E28B-971C-4D02-A9DF-C40E055492D9.png)

These are hashable!

→ generally it’s better to use map and set instead of using unoredered set and maps!

![D4B17183-3D40-4251-8FC4-82492C16BB7D.png](../../../../Images/D4B17183-3D40-4251-8FC4-82492C16BB7D.png)

![09E93ECB-FFF3-44C4-A9FA-C17302E2645A.png](../../../../Images/09E93ECB-FFF3-44C4-A9FA-C17302E2645A.png)

→And iterators can be used in any way!

![8A883770-2912-4E38-947D-4B555F41B852.png](../../../../Images/8A883770-2912-4E38-947D-4B555F41B852.png)

Yahan par har v.end() dalne ki jarurat nahi hai!

→ sort(v.begin(),v.begin()+4) sorts[0,4)→ index 4 is exclusive!

→Sort function in default mode sorts in ascending order!

→

![FE3FCB37-70B7-4736-91D2-C0D58290E8ED.png](../../../../Images/FE3FCB37-70B7-4736-91D2-C0D58290E8ED.png)

→

![99ADBB8E-911F-4377-85B9-6F8C85DCF4E9.png](../../../../Images/99ADBB8E-911F-4377-85B9-6F8C85DCF4E9.png)

→Since function return krta hai iterator and we got it converted to the actual value by derefrencing it with *

→

![10FE09E3-91FF-4D62-B13C-FED87012E3C8.png](../../../../Images/10FE09E3-91FF-4D62-B13C-FED87012E3C8.png)

![F2499B38-14F3-4481-9A14-17A801ACFD99.png](../../../../Images/F2499B38-14F3-4481-9A14-17A801ACFD99.png)

![9729DDC3-20A1-4217-8D77-FE5C366FC163.png](../../../../Images/9729DDC3-20A1-4217-8D77-FE5C366FC163.png)

→ Now to find the indices of these elements! What we can do is

→ in a vector we can do this but not in a map!

![5CC9E3BA-7788-47AD-8668-7F1D8A22E9A5.png](../../../../Images/5CC9E3BA-7788-47AD-8668-7F1D8A22E9A5.png)

→ This type of Things can be done where the containers are continuous!

→

![57323C43-A550-44AC-90D9-CC34BE0F7AB7.png](../../../../Images/57323C43-A550-44AC-90D9-CC34BE0F7AB7.png)

→

![C117B6C6-8813-48C4-B77D-CADF1693EA4D.png](../../../../Images/C117B6C6-8813-48C4-B77D-CADF1693EA4D.png)

First occurrence deta hai ye!

→

![9B887C81-F2E5-4EB3-8323-8751FD809147.png](../../../../Images/9B887C81-F2E5-4EB3-8323-8751FD809147.png)