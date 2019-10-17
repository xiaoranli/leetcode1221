# 16、leetcode1221. 分割平衡字符串
解法一：
--  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/17 20:52
 * @descriptor 1221. 分割平衡字符串
 */
public class BalancedStringSplit_1221 {
    //一般思想
    public static int balancedStringSplit(String s) {
        if(s == null || s.length() < 1)
            return 0;
        int r = 0,l = 0,count = 0;
        for (int i = 0; i < s.length(); i++) {
            if(s.charAt(i) == 'R')
                r++;
            else if(s.charAt(i) == 'L')
                l++;
            if(r == l) {
                count++;
            }
        }
        return count;
    }
    public static void main(String[] args) {
        String s = "LLLLRRRR";
        int i = balancedStringSplit1(s);
        System.out.println(i);
    }
}
</pre>
解法二：
--  
思路：
--
    使用一个栈来实现该功能：1)当栈中没有元素时，当前字符入栈;2)当栈中有元素时，若栈顶字符与当前字符一致，字符入栈，否则栈顶出栈；3)检查当前栈是否为空，若为空则平衡次数+1；    
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/17 20:52
 * @descriptor 1221. 分割平衡字符串
 */
public class BalancedStringSplit_1221 {
    //使用栈
    public static int balancedStringSplit1(String s) {
        Stack<Character> stack = new Stack<>();
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if(stack.empty() || stack.peek() == c){
                stack.push(s.charAt(i));
            }else{
                stack.pop();
            }
            if(stack.empty())
                count++;
        }
        return count;
    }

    public static void main(String[] args) {
        String s = "LLLLRRRR";
        int i = balancedStringSplit1(s);
        System.out.println(i);
    }
}
</pre>
