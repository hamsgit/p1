public static void main(String args[])
	{
		Scanner myObj = new Scanner(System.in);
		System.out.println("Which nth triangular number to be printed: ");
		int Number = myObj.nextInt();	//To read user input
		System.out.println("The "+Number+"th triangular number is: "+triangle(Number)); //calling triangle() method
		
		System.out.println("Which nth factorial number to be printed: ");
		Number = myObj.nextInt();	
		System.out.println("The "+Number+"th factorial number is: "+factorial(Number)); //calling factorial method
	
		System.out.println("Enter the word: ");
		String word = myObj.next();	
		System.out.println("Anagrams: ");
		anagram("",word); //since intially there is no prefix we have to use an empty space as a prefix
		
		System.out.println("Enter the number of disk: ");
		int Disk = myObj.nextInt();	//to the number of disks
		System.out.println("The solution is: ");
		hanoi(Disk,'A','B','C');
	}
	
	public static int triangle(int n) //recursive function
	{
		if(n==1)
			return 1; //base case
		else
			return n+triangle(n-1); //recursive step
	}
	
	public static int factorial(int n) //recursive function
	{
		if(n==1) //base case factorial of 1 is 1
			return 1;
		else
			return n*factorial(n-1); //recursive case if n=2 return 2*factorial(1) which will return the base case
	}
	
	public static void anagram(String prefix, String word)
	{
		if (word.length()==1)
			System.out.println(prefix+word); //base case if the word is one letter
		else 
			for(int i=0; i<word.length(); i++) //To loop through all letters 
			{
				String temp = word.substring(i, i+1); //to isolate one letter to start 
				String leftstr = word.substring(0,i); //To isolate the left side letters of the current letter
				String rightstr = word.substring(i+1); //to isolate the right side letters of the current letter
				anagram(prefix+temp, leftstr+rightstr); /*recursion step this time as prefix the code will 
														use the current letter as prefix and bala	nce letters as word parameter*/
			}
	}
	
	public static void hanoi(int n, char initial, char destination, char assist )
	{
		if (n==1)
			System.out.println("Move disk "+n+" from "+initial+" to "+destination); //base case
		else 
		{	//recursive step
			hanoi(n-1,initial,assist,destination); //moves n-1 disks to the auxillary rod
			System.out.println("Move disk "+n+" from "+initial+" to "+destination); //Then moves the nth rod to the destination
			hanoi(n-1,assist,destination,initial); //after that moves n-1 disks to destination
		}
	}
}# p1
