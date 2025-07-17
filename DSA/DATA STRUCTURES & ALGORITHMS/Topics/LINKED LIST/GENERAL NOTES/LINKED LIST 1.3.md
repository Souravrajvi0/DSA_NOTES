  

[https://leetcode.com/problems/palindrome-linked-list/description/](https://leetcode.com/problems/palindrome-linked-list/description/)(REVISE FIRSE CODE LIKHNA EK BAR)

→DIMAG MEIN PEHE YE IDEA AYA HAI KI BHAI MUJHE EK KAM KARNA CHAHIYE KI MIDDLE SE REVERSE KAR DO AND VALUES CHECK KAR LO

→BUT THE SIZE OF THE LINKED LIST HERE PLAYS A PART

→EVEN LENTH AND ODD LENTH PAR ALAG TARIKE SE CHECKING HOGI

  

BRUTE FORCE : USE STACK LOL

![image 41.png](../../../../../Images/image%2041.png)

Pehle bhar do and fir vapis check karlo

→AESE SWALO MEIN JAHAN ORDER ULTA KRNE KI SOCH STACK AS A DATA STRUCTURE KAFFI HELPFUL HOTA HAI

→**Time Complexity: O(2 * N)**

**→Space Complexity: O(N) We use a stack** 

  

BETTER APPROACH

IN CASE OF EVEN LENTH LINKED LIST

WE NEED TO COMPARE EQUAL HALFS

![image 1 18.png](../../../../../Images/image%201%2018.png)

![image 2 16.png](../../../../../Images/image%202%2016.png)

  

NOW FOR ODD

![image 3 14.png](../../../../../Images/image%203%2014.png)

MY CODE:

```C++
bool isPalindrome(ListNode* head) {
if (head == NULL) return false;
if (head->next == NULL) return true;
// Step 1: Find the middle of the list using the fast and slow pointer technique
ListNode* slow = head;
ListNode* fast = head;

while (fast && fast->next) {
    slow = slow->next;
    fast = fast->next->next;
}

// Step 2: Reverse the second half of the list
ListNode* prev = NULL;
ListNode* current;

// If fast is not NULL, it means the list has an odd number of elements.
// Skip the middle element (slow) by starting reversal from slow->next
if (fast == NULL) {
    current = slow;
} else {
    current = slow->next;
}

while (current) {
    ListNode* nextNode = current->next;
    current->next = prev;
    prev = current;
    current = nextNode;
}

// Step 3: Compare the two halves
ListNode* firstHalf = head;
ListNode* secondHalf = prev;  // 'prev' now points to the head of the reversed second half

while (secondHalf) {
    if (firstHalf->val != secondHalf->val) {
        return false;
    }
    firstHalf = firstHalf->next;
    secondHalf = secondHalf->next;
}

return true;
}
```

LOOK AT STRIVER CODE SINCE EVEN MEIN TWO MIDDLE ELEMENTS HOTE HAIN WO PEHLE WALE PAR ROKH LETE HAI BY DOING FAST→NEXT→NEXT ! = NULL (M1 ,M2 HOTE HAIN TWO MIDDLE ELEMENTS AND MAIN HAMESHA M2 PAR RUKTA HUON)

STRIVER CODE →

```C++
bool isPalindrome(Node* head) {
// Check if the linked list is empty// or has only one nodeif (head == NULL || head->next == NULL) {

// It's a palindrome by definitionreturn true;
    }

// Initialize two pointers, slow and fast,// to find the middle of the linked list
    Node* slow = head;
    Node* fast = head;

// Traverse the linked list to find the// middle using slow and fast pointerswhile (fast->next != NULL && fast->next->next != NULL) {

// Move slow pointer one step at a time
        slow = slow->next;

// Move fast pointer two steps at a time
        fast = fast->next->next;
    }

// Reverse the second half of the// linked list starting from the middle
    Node* newHead = reverseLinkedList(slow->next);

// Pointer to the first half
    Node* first = head;

// Pointer to the reversed second half
    Node* second = newHead;
    while (second != NULL) {

// Compare data values of// nodes from both halves

// If values do not match,// the list is not a palindromeif (first->data != second->data) {

// Reverse the second half// back to its original statereverseLinkedList(newHead);

// Not a palindromereturn false;
        }

// Move the first pointer
        first = first->next;

// Move the second pointer
        second = second->next;
    }

// Reverse the second half// back to its original statereverseLinkedList(newHead);

// The linked list is a palindromereturn true;
}
```

Ek Pattern ye dikh raha hai having some certain gap between two pointers of length n and then comparing the values and the other half is mostly modified kisi operation se but Jo end mein do pointers move karte hain unke bich ka difference N rehta hai and end wala NULL hit karta hai and ye hi condition hoti hai loop ko todne ki

  

  

[https://leetcode.com/problems/odd-even-linked-list/](https://leetcode.com/problems/odd-even-linked-list/)(REVISE)

  

**BRUTE FORCE→** DATA REPLACEMENT APPROACH

  

IN THIS WE WILL JUST REPLACE THE DATA IN THE LINKED LIST

KAISE???

FOR ODD INDEXES

WELL FIRST NA TEMP LO HEAD PAR AND THEN USKE BAD TEMP→NEXT→NEXT MOVE KAR DO

FOR EVEN INDEXES

WELL FIRST LO TEMP AT head→next and then isko bhi vaise hi move kar do 1 temp=temp→next→next;

Sath mein ek array rakho and then ussee value copy kardo finally in the linked list

![image 4 12.png](../../../../../Images/image%204%2012.png)

![image 5 10.png](../../../../../Images/image%205%2010.png)

![image 6 10.png](../../../../../Images/image%206%2010.png)

![image 7 9.png](../../../../../Images/image%207%209.png)

![image 8 9.png](../../../../../Images/image%208%209.png)

  

**OPTMISE KARO BHAITYA ISKO AB**

```C++
ListNode* oddEvenList(ListNode* head) {
        if(head==NULL||head->next==NULL)return head;
        ListNode*odd=head;
        ListNode*even=head->next;
        ListNode*evenhead=head->next;
        while(even!=NULL&&even->next!=NULL){
        odd->next=odd->next->next;
        odd=odd->next;
        even->next=even->next->next;
        even=even->next;
        }
        odd->next=evenhead;
        return head;
         }
```

  

[https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

  

BRUTE FORCE → SIZE NIKAL LO AND THEN TRVERSE SIZE-N IN THE FRONT

**YAHAN BUT EK BAT KAFFI ACHE SE SMAJH ATI HAI KI BHAI TO DELETE SOME NODE HUMEIN USKE PICHE WALE KI JARURAT HOTI HAI NAKI USKI IN LINKED LIST**

![image 9 8.png](../../../../../Images/image%209%208.png)

OPTMISED APPROACH

```C++
  ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode*temp1=head;
        ListNode*temp2=head;
        int count=1;
        while(temp1&&count!=n){
            count++;
            temp1=temp1->next;
        }
        ListNode*prev=NULL;
        while(temp1->next!=NULL){
            prev=temp2;
            temp2=temp2->next;
            temp1=temp1->next;
        }
        if(temp1==head&&n==1)return NULL;
        // temp1 is always going to be at the end 
        // temp2 will be at the node which is going to get deleted
        // Since we're always trying to find the node that is behind the temp2 so if temp2 is   // at  the head then prev is going to be null
        if(temp2==head){
            head=head->next;
            return head;
        }
        ListNode*tbd=prev->next;
        prev->next=tbd->next;
        temp2->next=NULL;
        delete(tbd);
        return head;
        
    }
```

**Time Complexity: O(N) since the fast pointer will traverse the entire linked list, where N is the length of the linked list.**

**Space Complexity: O(1), as we have not used any extra space.**

  

  

[https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/)

  
MY CODE →  

```C++
 ListNode* deleteMiddle(ListNode* head) {
        if(head==NULL||head->next==NULL)return NULL;
        ListNode*slow=head;
        ListNode*fast=head;
        ListNode*prev=NULL;
        while(fast&&fast->next){
            prev=slow;
            slow=slow->next;
            fast=fast->next->next;
        }
        if(slow->next==NULL){
            prev->next=NULL;
            return head;
        }
        prev->next=slow->next;
        slow->next=NULL;
        return head;
     }
```

SINCE WE ALWAYS GET SLOW AS THE MIDDLE AND IT IS 1 PLACE AAGE AND WE CAN’T USE IT SINCE WE WE NEED USEE PEHLE WALA ELEMENT TO DELE TE IT

  

![image 10 7.png](../../../../../Images/image%2010%207.png)

EVEN MEIN FAST ALWAYS HITS THE NULL  
ODD MEIN FAST ALWAYS HITS THE LAST ELEMENT  

⇒SO WHAT WE CA DO IS SKIP ON STEP OF THE SLOW SO USSE WO EK STEP PEHLE HI RUKH JAYEGA

⇒while loop se pehle fast ko ek step chla do (fast=fast→next→next)