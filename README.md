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







package Task3;

public class ADT {
	
    private int[] x;
    private int r;
    private int b;
    
    public ADT(int capacity) {
        x = new int[capacity];
        r = -1;
        b = capacity;
    }
    
    public void Red(int item) {
    	
        if (r + 1 >= b) {
            throw new RuntimeException("red is full");
        }
        
        x[++r] = item;
    }
    
    public void Blue(int item) {
    	
        if (b - 1 <= r) {
            throw new RuntimeException("blue is full");
        }
        
        x[--b] = item;
    }
    
    public int Red() {
    	
        if (r == -1) {
            throw new RuntimeException("red is empty");
        }
        
        return x[r--];
    }
    
    public int Blue() {
    	
        if (b == x.length) {
        	
            throw new RuntimeException("blue is empty");
        }
        
        return x[b++];
    }
    
    public boolean RedE() {
    	
        return r == -1;
    }
    
    public boolean BlueE() {
    	
        return b == x.length;
    }
    
    public boolean RedF() {
    	
        return r + 1 >= b;
        
    }
    
    public boolean BlueF() {
    	
        return b - 1 <= r;
        
    }
    
    public static void main(String[] args) {
    	
        ADT S = new ADT(15);
        
        S.Red(7);
        S.Red(8);
        S.Blue(6);
       S.Blue(3);
        
        System.out.println(S.Red());
        System.out.println(S.Blue());
        System.out.println(S.Red());
        System.out.println(S.Blue());
    }
}










package Task4;

import java.util.*;

public class CPU_Jobs {
    
    private static class Job {
        int id;
        int priority;
        int duration;
        
        public Job(int id, int priority, int duration) {
            this.id = id;
            this.priority = priority;
            this.duration = duration;
        }
    }
    
    public static void main(String[] args) {
        // create some sample jobs
        
        ArrayList<Job> jobs = new ArrayList<Job>();
        // take job inputs from user
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of jobs: ");
        int n = sc.nextInt();
        for(int i=0;i<n;i++){
            System.out.print("Enter job id: ");
            int id = sc.nextInt();
            System.out.print("Enter job priority: ");
            int priority = sc.nextInt();
            System.out.print("Enter job duration: ");
            int duration = sc.nextInt();
            jobs.add(new Job(id, priority, duration));
        }
        
        ArrayList<Integer> schedule1 = FirstComeFirstServeSchedule(jobs);
        System.out.println("First Come First Serve Schedule: ");
        for(int i=0;i<schedule1.size();i++){
            System.out.println("System time [" + (i) + "] - Job " + schedule1.get(i) + " is running");
        }


        ArrayList<Integer> schedule2 = PrioritySchedule(jobs);
        System.out.println("Priority Schedule: ");
        for(int i=0;i<schedule2.size();i++){
            System.out.println("System time [" + (i) + "] - Job " + schedule2.get(i) + " is running");
        }

        ArrayList<Integer> schedule3 = ShortestRemainingTimeFirstSchedule(jobs);
        System.out.println("Shortest Remaining Time First Schedule: ");
        for(int i=0;i<schedule3.size();i++){
            System.out.println("System time [" + (i) + "] - Job " + schedule3.get(i) + " is running");
        }

    }
    public static ArrayList<Integer> FirstComeFirstServeSchedule(ArrayList<Job> jobs){
        var totalTime = 0;
        for(var job: jobs){
            totalTime += job.duration;
        }
        var schedule = new ArrayList<Integer>(totalTime);
        for(var job: jobs){
            for(var i = 0; i < job.duration; i++){
                schedule.add(job.id);
            }
        }
        return schedule;
    }

    public static ArrayList<Integer> PrioritySchedule(ArrayList<Job> jobs){
        var totalTime = 0;
        for(var job: jobs){
            totalTime += job.duration;
        }
        var schedule = new ArrayList<Integer>(totalTime);
        jobs.sort((a, b) -> a.priority - b.priority);
        Collections.reverse(jobs);
        for(var job: jobs){
            for(var i = 0; i < job.duration; i++){
                schedule.add(job.id);
            }
        }

        return schedule;
    }

    public static ArrayList<Integer> ShortestRemainingTimeFirstSchedule(ArrayList<Job> jobs){
        var totalTime = 0;
        for(var job: jobs){
            totalTime += job.duration;
        }
        var schedule = new ArrayList<Integer>(totalTime);
        
        jobs.sort((a, b) -> a.duration - b.duration);
        for(var job: jobs){
            for(var i = 0; i < job.duration; i++){
                schedule.add(job.id);
            }
        }

        return schedule;
    }


}









package Task7;

import java.util.Arrays;

public class Heap {
    
    public static void main(String[] args) {
        int[] a = {4, 9, 11, 10, 5, 2};
        System.out.println(  Arrays.toString(a));
    }
    
    public static void heapsort(int[] a) {
        buildMinHeap(a);
        for (int i = a.length - 1; i >= 0; i--) {
            int temp = a[0];
            a[0] = a[i];
            a[i] = temp;
            minHeapify(a, 0, i);
        }
    }
    
    public static void buildMinHeap(int[] a) {
        for (int i = a.length / 2 - 1; i >= 0; i--) {
            minHeapify(a, i, a.length);
        }
    }
    
    public static void minHeapify(int[] a, int b, int c) {
        int left = 2 * b + 1;
        int right = 2 * b + 2;
        int smallest = b;
        if (left < c && a[left] < a[smallest]) {
            smallest = left;
        }
        if (right < c && a[right] < a[smallest]) {
            smallest = right;
        }
        if (smallest != b) {
            int temp = a[b];
            a[b] = a[smallest];
            a[smallest] = temp;
            minHeapify(a, smallest, c);
        }
    }
}


