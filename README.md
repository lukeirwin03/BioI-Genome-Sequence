## BioI-Genome-Sequence
Purpose: This program creates a simulated strand of DNA has some methods to loop through it to find a desired sequence and count how many times it appears in the DNA strand.
------------------------------------------------------------------------------
What it is: The code that I wrote works but having two separate classes with one being the Main class and the other being the DNA class. The way in which these two classes interact is that the Main class is only used to create a DNA object and call the methods with respect to the DNA object. The DNA class houses all of the methods that can be called of DNA and all of the variables needed to make it work. 

Methods In DNA:

DNA(): The constructor in the DNA class has no variables that need to be input because within the constrtuctor, there is a scanner that interacts with the user. The scanner will ask the user to input the length of the DNA strand or the number of base pairs for the length and then uses a for loop that uses Math.random() to make a random number 1 through 4. Then the random numbers are assigned a specific letter and are added to an array of strings.
```
  public DNA(){
    Scanner kb = new Scanner(System.in); // scanner for user input
    System.out.print("How long would you like the DNA strand to be? ");
    length1 = kb.nextInt(); // length of the DNA determined by user input
    strand1 = new String[length1];  // creates the array
    for(int i = 0; i < strand1.length; i++){ // fills the array
       random = (int)((Math.random() * 4) + 1);
       if(random == 1)
          strand1[i] = "A";
       if(random == 2)
          strand1[i] = "T";
       if(random == 3)
          strand1[i] = "C";
       if(random == 4)
          strand1[i] = "G";
    }
  }
  ```

getPair(): The getPair() method will take in one string at a time and return the abreviated base pair that pairs with the one that is taken in. It does this with four unique if statements that compare the string that is taken in from the *strand1* array and return the complementary base pair.
```
  public static String getPair(int i, String[] strand1){
    if(strand1[i].equals("A")) // compares the index of strand1 to a letter
        return "T"; // returns complement
      if(strand1[i].equals("T"))
        return "A";
      if(strand1[i].equals("C"))
        return "G";
      if(strand1[i].equals("G"))
        return "C";
      return "";
  }
```

pairDNA(): The pairDNA() method will create an array of the complements to the main DNA strand. It does this by utilizing a for loop and calls the getPair() method. 
```
  public void pairDNA(){
    String[] strand2 = new String[strand1.length]; // makes the complement Array
    for(int i = 0; i < strand2.length; i++) // loops through strand1 and uses getPair() to fill new strand with complements
      strand2[i] = getPair(i, strand1); 
  }
```

printDNA(): The printDNA() method will just loop through both of the strands(main and complementary) and print out the index of the strand and its complement. There is also a little bit of formatting just to make it look a more comprehensible and partially simulate the structure of DNA.
```
  public void printDNA(){
    for(int i = 0; i < strand1.length; i++) // loops through the DNA strands and prints it out in an organized format
      System.out.println(strand1[i] + " - " + getPair(i, strand1));
  }
```

getNumSequence(): The getNumSequence() method uses a scanner to ask the user for a base pair sequence to search through the DNA for. The method will then use a for loop to loop through the entire strand and look for the sequence. Any time that the DNA sequence occurs in the strand, the loop will add 1 to a counter variable. Once the entire array has been searched, the count variable is returned.
```
  public void getNumSequence(){
    Scanner kb = new Scanner(System.in); // scanner for user input
    int count = 0; // counter for how many times the sequence occurs in strand1
    System.out.print("Enter Desired Sequence: ");
    seq = kb.next();
    seq = seq.toUpperCase(); // makes sure that it will be formatted correctly
    strand1String = "";

    for(int i = 0; i < strand1.length; i++) // makes strand1 a string for sake of ease when searching
      strand1String += strand1[i];

    for(int i = 0; i < strand1String.length() - seq.length(); i++){ // searches strand1 for the desired sequence
      if(strand1String.substring(i, i + seq.length()).equals(seq))
        count++;
    }
     System.out.println("Sequence " + seq + " appears in Strand1 " + count + " times.");
  }
```

toString(): The toString() method is a way of printing out the DNA object and it just returns the strand1 array as a string. This is done in order to simulate an NCBI-like random DNA sequence. 
```
  public String toString(){ // prints out the DNA object as a string
    String dnaString = "";
    for(int i = 0; i < strand1.length; i++)
      dnaString += strand1[i];
    return "\n" + dnaString;
  }
```

# Sample Input/Output
How long would you like the DNA strand to be? 10 *(User Input)*  
A - T  
C - G  
C - G  
C - G  
A - T  
A - T  
C - G  
C - G  
T - A  
G - C  
Enter Desired Sequence: ac *(User Input)*  
Sequence AC appears in Strand1 2 times.  
  
ACCCAACCTG

# Dependencies and Configuration Instructions
This program was written and tested in Java 17 using Eclipse 4.12. There are no dependencies and should be able to be run in any IDE.

# Applications
This can be used to visualize how sequencing DNA can look and replicate it in a simple and visual way. It is used to demonstrate how researchers can take a strand of DNA and identify the base pairs and specific sequences. Another use for it could be with sample files with a specific sample of DNA and a specific gene to look for within the sample. This is more of a learning tool to visualize and demonstrate the process in a simple way. It basically replicates NCBI's random sequence generator, but my code also give you the pair. 

# Files in this Directory
- Main.java
- DNA.java
- LICENSE: Boost Software License 1.0
- This README

# Contact Info
Author: Luke Irwin, lukeirwin [at] unomaha [dot] edu  

# Known Bugs
As of 11/17/21 there are no known bugs in the program.
