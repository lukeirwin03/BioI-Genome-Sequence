# BioI-Genome-Sequence
\nTLDR: This program creates a simulated strand of DNA has some methods to loop through it to find a desired sequence and count how many times it appears in the DNA strand.
------------------------------------------------------------------------------
\nWhat it is: The code that I wrote works but having two separate classes with one being the Main class and the other being the DNA class. The way in which these two classes interact is that the Main class is only used to create a DNA object and call the methods with respect to the DNA object. The DNA class houses all of the methods that can be called of DNA and all of the variables needed to make it work. 
\nMethods In DNA:
\nConstructor: The constructor in the DNA class has no variables that need to be input because within the constrtuctor, there is a scanner that interacts with the user. The scanner will ask the user to input the length of the DNA strand or the number of base pairs for the length and then uses a for loop that uses Math.random() to make a random number 1 through 4. Then the random numbers are assigned a specific letter and are added to an array of strings. 
`
  public DNA(){
    Scanner kb = new Scanner(System.in);
    System.out.print("How long would you like the DNA strand to be? ");
    length1 = kb.nextInt();
    strand1 = new String[length1];
    for(int i = 0; i < strand1.length; i++){
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
  `
getPair(): The getPair() method will take in one string at a time and return the abreviated base pair that pairs with the one that is taken in.
pairDNA(): The pairDNA() method will create an array of the complements to the main DNA strand. It does this by utilizing the getPair() method.
printDNA(): The printDNA() method will just loop through both of the strands(main and complementary) and print out the index of the strand and its complement. There is also a little bit of formatting just to make it look a little nicer.
getNumSequence(): The getNumSequence() method uses a scanner to ask the user for a base pair sequence to search through the DNA for. The method will then use a for loop to loop through the entire strand and look for the sequence. Any time that the DNA sequence occurs in the strand, the loop will add 1 to a counter variable. Once the entire array has been searched, the count variable is returned.
