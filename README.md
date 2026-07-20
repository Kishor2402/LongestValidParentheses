# LongestValidParentheses
Longest Valid Parentheses code


import java.util.Stack;

public class LongestValidParentheses {

    public static int longestValidParentheses(String s) {

        Stack<Integer> stack = new Stack<>();
        stack.push(-1);   // Base index

        int maxLength = 0;

        for (int i = 0; i < s.length(); i++) {

            if (s.charAt(i) == '(') {
                stack.push(i);
            } else {

                stack.pop();

                if (stack.isEmpty()) {
                    stack.push(i);
                } else {
                    int length = i - stack.peek();
                    maxLength = Math.max(maxLength, length);
                }
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {

        System.out.println(longestValidParentheses("(()"));      // 2
        System.out.println(longestValidParentheses(")()())"));   // 4
        System.out.println(longestValidParentheses(""));         // 0
    }
}
