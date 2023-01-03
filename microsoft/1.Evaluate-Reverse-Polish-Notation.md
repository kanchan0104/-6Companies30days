problem: https://leetcode.com/problems/evaluate-reverse-polish-notation/
using stack, whenever we got a number, we will add that into stack, and if we got a operator, then we will pop top two element from stack and do the corrosponging operation

code:
```
class Solution {
public:
    int evalRPN(vector<string>& t) {
        stack <int> s;
        for(int i=0;i<t.size();i++){
            if(t[i]=="+"||t[i]=="-"||t[i]=="*"||t[i]=="/")
            {
                int a1=s.top();
                s.pop();
                int a2=s.top();
                s.pop();
                if(t[i]=="+")
                    s.push(a2+a1);
                if(t[i]=="-")
                    s.push(a2-a1);
                if(t[i]=="*")
                    s.push(a2*a1);
                if(t[i]=="/")
                    s.push(a2/a1);
            }
            else{
                s.push(stoi(t[i]));
            }
        }
        return s.top();
    }
};
```
