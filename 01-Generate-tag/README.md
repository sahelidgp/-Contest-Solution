# 👩🏻‍💻Generate tag

## [problem link](https://leetcode.com/contest/weekly-contest-454/problems/generate-tag-for-video-caption/description/)◀️

```c++
class Solution {
    private:
    string trim(string & s){
        int i=0;
        int n = s.length();
        while(!isalpha(s[i])  && i<n){
            i++;
        }
        return s.substr(i,s.length());
    }
    public:
    string generateTag(string caption) {
        
        string camel = "#";
        string caption1 = trim(caption);
        int n1 = caption1.size();
        for(int i=0;i<n1;i++){
         
            if(isalpha(caption1[i]))
            { 
                if(i==0 ||  caption1[i-1]!= ' ')camel+= tolower(caption1[i]);
                else camel += toupper(caption1[i]);
            }
            else continue;
            
        }
        if(camel.length()>100)
        camel = camel.substr(0,100);
        return camel;
    }
};
```
# Another approach
```c++
class Solution {
public:
    string generateTag(string caption) {
        string ans = "#";
        bool caps = false;
        for(char &ch: caption){
            if(ch == ' '){
                if(ans.size()>1)
                caps = true;
            }
            else{
                if(caps){
                    ans.push_back(toupper(ch));
                    caps = false;
                }
                else
                    ans.push_back(tolower(ch));
                
            }
        if(ans.size() == 100)break;

        }
          return ans;  
    }
};
```
