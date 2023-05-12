# Courswork



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







package Task2;

import java.util.HashSet;

public class UnorderedNumbers {
	
	 public static void main(String[] args) {
	    	
	        int[] arr1 = new int [] {8, 4, 5, 2, 9, 1}; 
	        int[] arr2 = new int [] {4, 5, 3, 2, 1, 9};
	        
	        
	        HashSet<Integer> arr3 = new HashSet<>();
		    HashSet<Integer> arr4 = new HashSet<>();
		    
		    
		    for (int a : arr1) {
		        arr3.add(a);
		    }
		    
		    for (int b : arr2) {
		        arr4.add(b);
		    }
		    
		    if (arr3.equals(arr4)) {
		        System.out.println("Have the same set of numbers");
		    }
		    
		    else {
		        System.out.println("Doesn't have the same set of numbers");
		    }
		}
	        
}


