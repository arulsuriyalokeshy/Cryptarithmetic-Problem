<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name: SURIYA PRAKASH S             </h3>
<h3>Register Number: 212223100055      </h3>
<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>
<h3>Procedure:</h3>
Input and Output
<br>Input:
This algorithm will take three words.
<br> B A S E<br>
    B A L L<br>
           ----------<br>
           G A M E S<br>

Output:
It will show which letter holds which number from 0 – 9.
For this case it is like this.

              B A S E                         2 4 6 1
              B A L L                         2 4 5 5
             ---------                       ---------
            G A M E S                       0 4 9 1 6
Algorithm
For this problem, we will define a node, which contains a letter and its corresponding values.<br>

isValid(nodeList, count, word1, word2, word3)<br>

Input − A list of nodes, the number of elements in the node list and three words.<br>

Output − True if the sum of the value for word1 and word2 is same as word3 value.<br>

Begin<br>
   m := 1<br>
   for each letter i from right to left of word1, do<br>
      ch := word1[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>
      val1 := val1 + (m * nodeList[j].value)<br>
      m := m * 10<br>
   done<br>

   m := 1<br>
   for each letter i from right to left of word2, do<br>
      ch := word2[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val2 := val2 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   m := 1<br>
   for each letter i from right to left of word3, do<br>
      ch := word3[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val3 := val3 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   if val3 = (val1 + val2), then<br>
      return true<br>
   return false<br>
End<br>
## Program:
```
from itertools import permutations
def findDistinctLetters(s):
    t=[]
    for x in s:
        if x not in t:
            t.append(x)
    return ''.join(t)
def assignValues(s,values):
    value={}
    for i in range(len(s)):
        value[s[i]]=values[i]
    return value
def solve_cryptarithmetic(s1,s2,s3):
    s1=s1.strip().lower()
    s2=s2.strip().lower()
    s3=s3.strip().lower()
    distinctLetters=findDistinctLetters(s1+s2+s3)
    n=len(distinctLetters)
    for perm in permutations(range(10),n):
        value=assignValues(distinctLetters,perm)
        s1i,s2i,s3i=0,0,0
        i,j,k=1,1,1
        if value[s1[0]]==0 or value[s2[0]]==0 or value[s3[0]]==0:
            continue
        else:
            revs1=s1[::-1]
            revs2=s2[::-1]
            revs3=s3[::-1]
            for x in revs1:
                s1i+=value[x]*i
                i*=10
            for x in revs2:
                s2i+=value[x]*j
                j*=10
            for x in revs3:
                s3i+=value[x]*k
                k*=10
            if s3i==s1i+s2i:
                break
    return (s1i,s2i,s3i,value)
st1=input()
st2=input()
st3=input()
s1,s2,s3,value=solve_cryptarithmetic(st1,st2,st3)
print("{}--->{}".format(st1,s1))
print("{}--->{}".format(st2,s2))                
print("{}--->{}".format(st3,s3))
print(value)

        
```

<hr>
<h2>Sample Input and Output:</h2>
SEND = 9567<br>
MORE = 1085<br>
<hr>
MONEY = 10652<br>
<hr>
<h2>Result:</h2>
<p> Thus a Cryptarithmetic Problem was solved using Python successfully</p>
