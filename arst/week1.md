Algorithm
--------------------------------------------------------------------------------
771.宝石与石头
给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。
J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。
示例 1:
输入: J = "aA", S = "aAAbbbb"
输出: 3

示例 2:
输入: J = "z", S = "ZZ"
输出: 0

注意:
S 和 J 最多含有50个字母。
 J 中的字符不重复。

解题思路
 很简单，把J和S字符变为char 数组，J变的 char 数组放入Set中，然后和S变的数组 比较 contains()
如果返回 true 就+1；
class Solution {
    public int numJewelsInStones(String J, String S) {
        if( J == null || S == null){
            return 0;
        }
        char [] js = J.toCharArray();
        char [] ss = S.toCharArray();
        Set<Character> set = new HashSet<Character>();
        for(char c : js){
            set.add(c);
        }
        int count = 0;
        for(char s : ss){
            if(set.contains(s)){
                ++count;
            }
        }
        return count;
    }
}



709.转换成小写字母
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。
 
示例 1：
输入: "Hello"
输出: "hello"

示例 2：
输入: "here"
输出: "here"

示例 3：
输入: "LOVELY"
输出: "lovely"


解题思路：
 虽然String 中有方法可以直接转换为小写。这题估计是想考查ACSII 码。总之转换大小写就是满足这个公式'x' = 'x' + 'a' - 'A'。
class Solution {
    public String toLowerCase(String str) {
        char [] chs = str.toCharArray();
        for(int i =0 ;i < chs.length; i++){
            if(chs[i] >= 'A' && chs[i] <='Z'){
                chs[i] += 'a' - 'A';
            }
        }
        
        return new String(chs);
    }
}




Review
--------------------------------------------------------------------------------
Redis集群的第一步。
https://blog.usejournal.com/first-step-to-redis-cluster-7712e1c31847


Tip
--------------------------------------------------------------------------------
java中的特殊字符串处理，比如split 或 replace 的时候，无法使用。会报错找不到这个特殊字符。
需要在特殊字符增加 \\进行转义
比如"\\{", 这样进行 分割和替换的时候就不会报错。


Share
--------------------------------------------------------------------------------
什么是分布式计算系统？
对于分布式还是比较懵逼，需要加大力度学习。
https://juejin.im/post/5c8f92d3f265da60d1081514?utm_source=gold_browser_extension