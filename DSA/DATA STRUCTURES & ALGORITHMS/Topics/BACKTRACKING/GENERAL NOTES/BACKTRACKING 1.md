
# PROGRAMMING PARADIGMS 

1. Brute Force 
2. DP
3. Greedy
4. DNC

->In Brute Force We explore all the possible outcomes!!! Doesn't Matter Whether it leads to an answer or not!!  
-> Since saari possibilities check karne k liye or ya brute force ko implement karne k liye RECURSION ki zarurat padh hi jati hai!
-> DP is just an optimization on Brute Force and Since we don't calculate the problems that are already been calculated!!!

->NOW THERE'S ANOTHER PARADIGM WE NEED TO LOOK AT WHICH IS CALLED BACKTRACKING


![BACKTRACKING 1-20241103064902266.webp](../../../../../Images/BACKTRACKING%201-20241103064902266.webp)
- **Here we can prune irrelevant Calls! Calls That in any case won't result in any ANSWER.**
- **We traced the path for an answer and then revert it for other possibilities/We revert the changes we made!**

![BACKTRACKING 1-20241103065514328.webp](../../../../../Images/BACKTRACKING%201-20241103065514328.webp)
![BACKTRACKING 1-20241103065650022.webp](../../../../../Images/BACKTRACKING%201-20241103065650022.webp)

APPROACH:
![BACKTRACKING 1-20241103072735528.webp](../../../../../Images/BACKTRACKING%201-20241103072735528.webp)

->TOH HUM EK KAM KARENGE YAHAN PAR A/B/C Mein Se kisi ek ko bhi! Pehla Character Bnne ka mauka denge!
-> Aur jo baki ka part bacha uske permutations added to the first fixed character will give us the right answers not all but some of em!!!!!


-> Getpc Ek function hai wo kya krega ki na TWO STRINGS LEGA AND Fir humein second string mein first String ki saari permutation lakar de dega!!
![1116](../../../../../Images/BACKTRACKING%201-20241103135210557.webp)
![1109](../../../../../Images/BACKTRACKING%201-20241103135242907.webp)

-> Since we're using recursion over here just think about the first layer!! Kyonki baaki ki layers bnana koi badi fight nahi hai!
-> YE FUNCTION KYA BATA RAHA HAI ABC KI SAARTI PERMUATION BATATA HAI AND EK EK KARKE ABC KI SAARI PERMUTATIONS IS EMPTY STRING MEIN AA JAENGI!!!!


-> getpc("bc","a")
BRUTE FORCE CODE!!!
**FOR UNIQUE CHARACTERS** 
```javascript
 void findpc(vector<string>&res,string s,string &r){
      if(s.size()==0){
         res.push_back(r);
         return;
      }
      
      for(int i=0;i<s.size();i++){
          char ch=s[i];
          r=r+ch;
          string n=s;
          n.erase(i,1);
          findpc(res,n,r);
          r.pop_back();
      }
  }
    vector<string> find_permutation(string &s) {
        // Code here there
        vector<string>res;
        string r="";
        findpc(res,s,r);
        return res;
        
    }
```




```javascript
 void getpc(vector<string>&res,const string s, string r){
       if(s.size()==0){
           res.push_back(r);
           return;
       }
       
     for(int i=0;i<s.size();i++){
         char ch=s[i];
         string left=s.substr(0,i);
         string right=s.substr(i+1);
         getpc(res,left+right,r+ch);
       }  
       
   }

   
   
    vector<string> find_permutation(string &s) {
        // Code here there
        vector<string>res;
        string r="";
        getpc(res,s,r);
        return res;
        
    }
```

In this method we're creating too many strings memory will be filled because we're creating too many approaches!!!
In C++, a substring can be extracted from a string using the `substr` function. The `substr` function is a member function of the `std::string` class, and it allows you to create a new string that contains a portion of an existing string.

STRING SUBSTRING METHODS!!!!!


**OPTIMISED APPROACH USING SWAPPING**

Here we're going to use swapping!
![BACKTRACKING 1-20241105084355383.webp](../../../../../Images/BACKTRACKING%201-20241105084355383.webp)

Since initially i is going to be 0 then it means from 0 to n-1 tak then it means pure string k permutations nikalne hai mujhe!!!
uske liye ekbar a ko pehle character bnne ka mauka denge fir b ko pehle character bnne ka mauka denge and then c ko 
**YAHAN PAR SAME STRING MEIN HI MAIN SWAPPING KARUNGA YE BAT DHYAN RAKHNA!!!**
![BACKTRACKING 1-20241105084445799.webp](../../../../../Images/BACKTRACKING%201-20241105084445799.webp)

DRY RUN WITH SWAPPING

![BACKTRACKING 1-20241105091038869.webp](../../../../../Images/BACKTRACKING%201-20241105091038869.webp)


- Toh Issue toh yehi hai ki since we pass string by reference The changes/updates are being shown at every stage/chain of the process/calls since we're swapping here!

Now This results in changing of the string for the other Cases!!!!

Now here the concept of backtracking comes into play!!!

So Backtracking says when on a solution path when we do some changes like Here we did swapping which does affect other answer/paths!!

ABHI K LIYE TOH SWAPPPING KARLO BUT JABH HUM VAPIS JA RE HONGE NA TOH YE SWAPPING WALE CHANGES HUM REVERT KARTE JAENGE!!

**CHANGES SHOULD BE REVERTED BACK SO THE ORIGINAL STATE IS ACHIEVED** 

SO SOLUTION BNATE VAQT IRESPECTIVE OF EITHER WE REACH THE SOLUTION OR DON'T  WE NEED TO REVERT THE STATE TO THE ORIGINAL!!!
BUT WHEN We're returning from recursion I should actually revert these changes!!, So for other paths original state will be considered!!

YEHI HAI BACKTRACKING KA STEP 2

And when we're exploring solutions and we find ourselves in a position where we know the no solution can be found on this path!! THEN WE DON'T HAVE TO GO ON THIS PATH!!!
 THIS IS STEP 1 CALLED THE **PRUNING OF THE SOLUTIONS**

DRY RUN WITH SWAPPING AND RESWAPPINNG
![BACKTRACKING 1-20241105095046292.webp](../../../../../Images/BACKTRACKING%201-20241105095046292.webp)



HERE WE'RE JUST DOING THE BACKTRACKING STEP
```c++
 void getpc(vector<string>&res,string &s,int i){
       
       if(i==s.size()-1){
           res.push_back(s);
           return;
       }
       
       for(int idx=i;idx<s.size();idx++){
           swap(s[i],s[idx]);
           // in C++ IN STRING CHARACTER SWAPPING IS THIS EASY
           getpc(res,s,i+1);
           swap(s[i],s[idx]);
        }
       
    }
   
    vector<string> findPermutation(string &s) {
        // Code here there
        vector<string>res;
        getpc(res,s,0);
        return res;
    }
```

SO THIS CODE WILL FAIL IN CASE OF REPETITION

DRY RUN FOR THE STRING CONTAINING REPEATING CHARACTERS!!!!!!
![BACKTRACKING 1-20241105101648118.webp](../../../../../Images/BACKTRACKING%201-20241105101648118.webp)


Toh Yahan samajhne wali bat ye hai ki jabh maine a k liye kuch set of calls kar di thi toh fir main vapis ek bar a ko place par laake kyon calls lagaoun?? (since ek character do baar gya in case toh unmein se ek ko fix rakh kar and baaki wale ko dusroun k sath permutations nikalne se same hi answer aenge for both the cases!!!)

BAT HAMESHA YAHAN FIRST CHARACTER KI HI HORAHAI HAI 
KISI KO LAYENGE TOH STRING K FIRST CHARACTER KI JAGAH HI LAENGE 

```c++
void getpc(vector<string>&res,string &s,int i){
       
       if(i==s.size()-1){
           res.push_back(s);
           return;
       }
       unordered_set<char>set;
       for(int idx=i;idx<s.size();idx++){
           if(set.count(s[idx]))continue;  // YE HAI PRUNNING KA STEP HAI
           set.insert(s[idx]);
           swap(s[i],s[idx]);
           getpc(res,s,i+1);
           swap(s[i],s[idx]);
        }
       
    }
   
    vector<string> findPermutation(string &s) {
        // Code here there
        vector<string>res;
        getpc(res,s,0);
        return res;
        }
```



BACKTRACKING STEPS
1. PRUNNING
2. REVERSAL OF STATE




#                                                              NQUEEN






#                                                         RAT IN A MAZE








