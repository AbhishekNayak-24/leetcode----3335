# leetcode----3335
Total Characters in string after Transformations I
//CODE IN JAVA
import java.util.LinkedList;

public class Solution {
    public int lengthAfterTransformations(String s, int t) {
        int[] count = new int[26];
        for (char c : s.toCharArray()) {
            count[c - 'a']++;
        }
        LinkedList<Integer> list = new LinkedList<>();
        for (int c : count) {
            list.add(c);
        }
        int delta = s.length() % 1000000007;
        for (int i = 0; i < t; i++) {
            int zCount = list.removeLast() % 1000000007;
            int aCount = list.pollFirst() % 1000000007;
            list.offerFirst((aCount + zCount) % 1000000007);
            list.offerFirst(zCount);
            delta = delta % 1000000007;
            delta = (delta + zCount) % 1000000007;
        }
        return delta;
    }
}
