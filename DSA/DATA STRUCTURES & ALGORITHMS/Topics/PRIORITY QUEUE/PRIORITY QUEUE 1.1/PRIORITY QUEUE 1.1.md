![image-1726576528097.jpg5405812808927416016.jpg](../../../../../Images/image-1726576528097.jpg5405812808927416016.jpg)

![image-1726576926087.jpg6668937161843849373.jpg](../../../../../Images/image-1726576926087.jpg6668937161843849373.jpg)

→ linked list se bhi koi Jada farak nahi padega

→Balanced Binary Search Tree se farak pad jayega but itna nahi

→

![image-1726578224406.jpg8338970613732067320.jpg](../../../../../Images/image-1726578224406.jpg8338970613732067320.jpg)

![image-1726578712038.jpg7189898424157242581.jpg](../../../../../Images/image-1726578712038.jpg7189898424157242581.jpg)

\#Ye basically bat ho Rahi hai leaf nodes ki!

→ half of the nodes leaves ki trah rehte hain

![B44FD7D8-8ACF-43E9-A193-07D690415537.png](../../../../../Images/B44FD7D8-8ACF-43E9-A193-07D690415537.png)

![5DB60366-046D-46E9-AD53-969B1B130230.png](../../../../../Images/5DB60366-046D-46E9-AD53-969B1B130230.png)

⇒ PARENT AND IMMEDIATE CHILD KI PRORITY HI CHECK HORAHI HAI

⇒BINARY SEARCH TREE WALE CONCEPT YAHAN APPY NAHI HI HONGE

→EVEN THIS WORKS TOO

![A0AB90B4-D0C4-43A7-9001-D19303C64728.png](../../../../../Images/A0AB90B4-D0C4-43A7-9001-D19303C64728.png)

**MIN HEAP**

![432F7391-D484-4BA0-AD00-35E1C34ED754.png](../../../../../Images/432F7391-D484-4BA0-AD00-35E1C34ED754.png)

→ Generally programming k andar max and min heaps ka hi use hota hai, toh wo isliliye define hogya

→ But Uska mtlb ye nahi hai ki heap sirf inhi types ka hoga

→Heap k andar priority kisi mathematical trike se bhi define hoskti hai

→Complete Binary tree ko hum array ka use krke bhi define kar skte hain! kyonki yhan par koi gaping exist nahi krti na isliye!

![EC5264A4-FF76-47BE-86AF-DDABA1198B56.png](../../../../../Images/EC5264A4-FF76-47BE-86AF-DDABA1198B56.png)

![C2282B6A-45E5-4452-AB59-AC46E50A68DA.png](../../../../../Images/C2282B6A-45E5-4452-AB59-AC46E50A68DA.png)

![52861402-4CBB-475F-8EC1-3EAD06228038.png](../../../../../Images/52861402-4CBB-475F-8EC1-3EAD06228038.png)

→ Parent k index se left and right child ka index nikalana kaffi easy hota hai

→ In case agar koi index out of bound or range ae toh mtlb wo element exist nahi karta

→ child se parent nikalne k liye mujhe floor value nikal lo bas!

![1BD074AA-6066-4612-B072-8C9356CFB7A3.png](../../../../../Images/1BD074AA-6066-4612-B072-8C9356CFB7A3.png)

→ SOCHNE KA TRIK YAHAN TREE KA HAI BUT VALUES STORE ARRAY MEIN HO HORAHA HAI

→HEAP KA MENTAL MODEL HAMARA TREE JAISA HAI , BUT ACTUAL MEINW WORK TOH ARRAY MEIN HI HOTA HAI ye ho pata because of this is a complete binary tree!

![3C100303-3CDB-412F-ABFC-756F389377DC.png](../../../../../Images/3C100303-3CDB-412F-ABFC-756F389377DC.png)

→ So when add an element(mtlb push_back kar do) to this heap Structure wise toh binary tree rahega but heap ki property jo hoti hai na vo satisfy nahi kargea!

→Yahan ab ismein maine pushback kiya 15 ko toh uska index 20 hogya!

→Now But usne apni max heap ki property loose kardi hai

→Swapping between parent and children!!!!

![64815CB0-82E2-4508-A7B3-883DFE85CA98.png](../../../../../Images/64815CB0-82E2-4508-A7B3-883DFE85CA98.png)

→MAX SWAP OPERATIONS HONGE log(N) times since height k equal tak

→ pushback toh O(1) mein hi hogya tha

→ upheapify bolte hain jabh hum leaves se root ki traf jate hain and heap ki property satisfy krte krte!

→HIghest priority ka element hamesha sabse upar hoga which means O(1)// root node par betha hoga

![image-1727686886277.jpg4978660290721999053.jpg](../../../../../Images/image-1727686886277.jpg4978660290721999053.jpg)

**→ IMPLEMENTATION**

![5E0F89DE-251A-497E-9ACD-4E9EC280163E.png](../../../../../Images/5E0F89DE-251A-497E-9ACD-4E9EC280163E.png)

![75BFE25B-452F-4376-BA52-B206368F605E.png](../../../../../Images/75BFE25B-452F-4376-BA52-B206368F605E.png)

![63123E7C-3808-487E-A52F-5E91D8BC0052.png](../../../../../Images/63123E7C-3808-487E-A52F-5E91D8BC0052.png)

**→ NOW REMOVAL KO MAIN IMPLEMENT KARUNGA**

![AC5408DD-39D8-4801-8086-5D83B1CCE42D.png](../../../../../Images/AC5408DD-39D8-4801-8086-5D83B1CCE42D.png)

→KISI HEAP KI SARI SUBTREES BHI HEAP HI HOTI HAI!

→ koi element jabh push hoga toh wo kahan push hoga?? well array ki 0th position par hi hoga na bhai!

→ Down heapify

![image-1727689013481.jpg2804775795126613349.jpg](../../../../../Images/image-1727689013481.jpg2804775795126613349.jpg)

![511562ED-D91C-4596-8912-DEB5F6FA4689.png](../../../../../Images/511562ED-D91C-4596-8912-DEB5F6FA4689.png)

But aesa case kab Banega?

Pop operation k time!

![3F54AC1E-60C0-47B0-B44D-001838046E68.png](../../../../../Images/3F54AC1E-60C0-47B0-B44D-001838046E68.png)

→So Kisi Vector k andar sabse last element jo hota hai na wohi! sabse easy hota hai remove karna!

→Toh ek kam karo na last and first ko swap kardo and then last ko pop_back kardo

→ and top se down heappify laga do!

![A890D86F-B7ED-44EC-BD06-6A8AF2FD9543.png](../../../../../Images/A890D86F-B7ED-44EC-BD06-6A8AF2FD9543.png)

![EF8DAAC8-DB43-481C-8B2E-08399737BD5B.png](../../../../../Images/EF8DAAC8-DB43-481C-8B2E-08399737BD5B.png)