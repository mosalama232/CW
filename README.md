# Task 1



package Task1;

import java.util.HashSet;

public class DuplicateElements {


	    public static void main(String[] args) {
	    	
	        char[] m = {'m', 'o', 'h', 'h', 'a', 'a', 'a', 'e', 'd', 'd'};
	        

	        char[] a = removeDuplicates(m);
   	        System.out.println("Array with no duplicates: " + new String(a));
    }

	    public static char[] removeDuplicates(char[] m) {
	        HashSet<Character> set = new HashSet<>();
	        for (char c : m) {
	            set.add(c);
	        }
	        
	        char[] a = new char[set.size()];
        int b = 0;
	        for (Character c : set) {
            a[b++] = c;
	        }
      
        return a;
	    }
	
}
