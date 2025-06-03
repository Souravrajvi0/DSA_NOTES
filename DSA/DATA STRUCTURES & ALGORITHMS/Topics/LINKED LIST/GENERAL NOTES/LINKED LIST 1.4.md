[https://leetcode.com/problems/sort-list/description/](https://leetcode.com/problems/sort-list/description/)

BRUTE FORCE:

ARRAY MEIN SAVE KARLO SARI VALUES AND THEN JUST APPLYING SORTING AND PUT THEM VALUES BACK IN THE LINKED LIST

SC→O(N)

TC→(2N+logN)

OPTMISED :

MERGE SORT

  

  

  

  

  

  

  

  

[https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1)

  

  

  

[https://leetcode.com/problems/intersection-of-two-linked-lists/description/](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

  

  

  

[https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1)

  

  

  

[https://leetcode.com/problems/add-two-numbers/description/](https://leetcode.com/problems/add-two-numbers/description/)

  

  

[https://leetcode.com/problems/swap-nodes-in-pairs/description/](https://leetcode.com/problems/swap-nodes-in-pairs/description/)(revise)

```C++
 ListNode* swapPairs(ListNode* head) {
       if(head==NULL||head->next==NULL)return head;
       ListNode*dummy=head->next;
       ListNode*temp2=head->next;
       ListNode*temp1=head;
       ListNode*prev=NULL;
       while(temp2){
        ListNode*nextpair=temp2->next;

        temp2->next=temp1;
        temp1->next=nextpair;
        if(prev!=NULL){
            prev->next=temp2;
        }

       if (nextpair == NULL || nextpair->next == NULL) {
            break;
        }

       prev=temp1;
       temp1=nextpair;
       temp2=nextpair->next;
     }
        return dummy;
    }
```