Preliminaries
Homework is due prior to the start of lecture. If it is submitted more than 10 minutes after the start of lecture, it will be considered a full day late. There will be a 10% deduction for late submissions that are made by 11:59 p.m. Eastern time on the Sunday after the deadline, and a 20% deduction for submissions that are made after that Sunday and before the start of the next lecture. We will not accept any homework that is more than 7 days late. Plan your time carefully, and don’t wait until the last minute to begin an assignment. Starting early will give you ample time to ask questions and obtain assistance.

In your work on this assignment, make sure to abide by our policies on academic conduct.

If you haven’t already done so, you should complete Problem Set 0 before beginning this assignment.

If you have questions while working on this assignment, please come to office hours, post them on Ed Discussion, or email cscie22-staff@lists.fas.harvard.edu

Part I: Short-answer problems
40 points total

Creating the necessary folder
If you haven’t already created a folder named e22 for your work in this course, follow these instructions to do so.

Then create a subfolder called ps1 within your e22 folder, and put all of the files for this assignment in that folder.

Creating the necessary file
The problems from Part I will all be completed in a single PDF file. To create it, you should do the following:

Access the template that we have created by clicking on this link and signing into your Google account as needed.

When asked, click on the Make a copy button, which will save a copy of the template file to your Google Drive.

Select File->Rename, and change the name of the file to ps1_partI.

Add your work for the problems from Part I to this file.

Once you have completed all of these problems, choose File->Download->PDF document, and save the PDF file in your ps1 folder. The resulting PDF file (ps1_partI.pdf) is the one that you will submit. See the submission guidelines at the end of Part I.

Problem 1: Memory management and arrays
8 points

Java built-in classes

In your work on this and subsequent problem sets, you should not use any of Java’s built-in collection classes (e.g., ArrayList) or utility classes (e.g., Arrays), unless a problem explicitly states that you may do so.
Consider the following lines of Java code:

int[] a = {5, 4, 3, 2, 1};
int[] b = {5, 4, 3, 2, 1};
int[] c = a;

for (int i = 0; i < b.length; i++) {
    c[i] = b[i];
}

b[3] += b.length;
a[3]--;

System.out.println(a[3] + " " + b[3] + " " + c[3]);
(6 points) In ps1_partI (see above), we have given you the beginnings of a memory diagram for these lines of code. It includes both the stack and the heap.

On the stack, we have included a stack frame for the main method, which is where we are assume that the above lines are found. On the heap, we have included the array to which the variable a refers.

Complete the provided memory diagram so that it shows the final result of the above lines of code.

To do so, you should:

Click on the diagram and then click the Edit link that appears below the diagram.

Make whatever changes are needed to the diagram. Below the thick horizontal line, we have given you a set of extra components that you can use as needed by dragging them above the thick line and putting them in the correct position. You may not need all of the provided components.

You can also edit any of the values in an array by clicking on one of its cells and editing the text that is inside the cell.

Once you have made all of the necessary changes, click the Save & Close button.

(2 points) Indicate what will be printed by the final line of code shown above.

Problem 2: Array practice
10 points total; 5 points each part

In this problem, you will write static methods that operate on arrays. These methods do not need to use recursion, and they do not need to be implemented as part of a class. Simply include the methods with your answers for the other problems from Part I.

Write a method with the header

public static void shiftRight(int[] arr)
that takes a reference to an array of integers and shifts all of the array elements one position to the right, with the original last element wrapping around to become the new first element. For example, consider this array:

int[] values = {0, 2, 4, 6, 8, 10};
After calling shiftRight(values), the contents of the values array should be {10, 0, 2, 4, 6, 8}.

Special cases:

If the method is passed a value of null, it should throw an IllegalArgumentException.

If the method is passed an array with a length of 0 or 1, it should leave the array unchanged.

This method does not need to use recursion. See below for a recommended approach to testing it.

(Note: Java has a built-in method called System.arraycopy() that you should not use in your solution.)

Write a method with the header

public static int indexOf(int[] arr1, int[] arr2)
that takes two arrays of integers and that returns the index of the first occurrence of the first list in the second list, or -1 if the first list does not appear in the second list. For example, suppose that you have these arrays:

int[] list1 = {1, 3, 6};
int[] list2 = {1, 3, 5, 8, 12, 1, 3, 17, 1, 3, 6, 9, 1, 3, 6};
then the call indexOf(list1, list2) should return 8 because the sequence of values stored in list1 appears in list2 starting at index 8. Notice that list1 actually appears twice in list2, starting at position 8 and starting at position 12. Your method should return the first such position.

If the first list is not contained in the second list, then the method should return -1. For example, if list2 had the same values as before but list1 stored {12, 1, 3, 6}, then the call indexOf(list1, list2) should return -1 because list1 is not contained in list2. You may assume that neither parameter is null and that both arrays have at least one element.

This method does not need to use recursion.

Testing Your Methods in VS Code We encourage you to use VS Code to test your methods for parts 1 and 2 above. Here are the steps:

If you haven’t already done so, create a folder named ps1 for your work on this assignment.

Download the following file: Problem2Test.java

Make sure to put the file in your ps1 folder. If your browser doesn’t allow you to specify where the file should be saved, try right-clicking on the link above and choosing Save as... or Save link as..., which should produce a dialog box that allows you to choose the correct folder for the file.

In VS Code, select the File->Open Folder or File->Open menu option, and use the resulting dialog box to find and open the folder that you created for this assignment. (Note: You must open the folder; it is not sufficient to simply open the file.)

The name of the folder should appear in the Explorer pane on the left-hand side of the VS Code window, along with the name of the Problem2Test.java file that you downloaded above.

Click on the name Problem2Test.java, which will open an editor window for that file.

Put your methods inside the provided class. We have given you some code in the main method for testing your methods, but we encourage you to add additional tests as well.

Note: You may use the Arrays.toString() method for testing, since it allows to easily view the contents of an array. However, you should not be using this method or any other method from the Arrays class for any purpose other than testing.

Run your program and make sure that the tests produce the expected results.

Once you are happy with your methods, put them in your ps1_partI file. Do not submit the Problem2Test.java file.

Problem 3: Recursion and the runtime stack
12 points

We will cover the material needed for this problem on January 30.

Consider the following recursive method:

public static int mystery(int a, int b) {
    if (a * b == 0) {
        return a;
    } else {
        int myst_rest = mystery(a - 1, b - 2);
        return b + myst_rest;
    }
}
(5 points) Trace the execution of mystery(5, 6). To do so, complete the template that we have provided in section 3-1 of ps1_partI. In particular, you should:

Include a separate “frame” for each call. We have filled in some of the components of the frames for the first two calls for you. You should replace each ... with the appropriate integer, and you should add frames for additional calls as needed, until you reach the base case.

Begin each frame with lines that explicitly state the values assigned to the parameters, as we have done for the first call.

Next, if the call is a base case, you can simply show the value that is returned (omitting the line for myst_rest). If the call is a recursive case, you should show the recursive call on the line for myst_rest.

Once you have reached the base case, you should work your way back through the frames for the previous calls. Add in both the results of the recursive call (i.e, the value assigned to myst_rest) and the value returned by the call itself.

(2 points) What is the value returned by mystery(5, 6)?

(2 points) During the execution of mystery(5, 6), method frames are added and then removed from the stack. How many method frames are on the stack when the base case is reached? You should assume that the initial call to mystery(5, 6) is made from within the main() method, and you should include the stack frame for main in your count.

(3 points) Give an example of values of a and b that would produce infinite recursion, and explain why it would occur.

Problem 4: Rewriting a method
10 points

We will cover the material needed for this problem on January 30.

Consider the following method, which uses iteration (a for loop) to search for an item in an array of integers. The method returns true if the item is found in the array, and false if it is not.

public static boolean search(int item, int[] arr) {
    for (int i = 0; i< arr.length; i++) {
        if (arr[i] == item) {
            return true;
        }
    }

    return false;
}
(4 points) Rewrite this method so that it searches for an item an array that can contain any type of object. Change the types of the parameters accordingly, and make whatever changes are needed to the body of the method.

(6 points) Rewrite your answer to part 1 so that it uses recursion instead of iteration. You will need to add a third parameter (call it start) that keeps track of where you are in the array. More precisely, start will specify the position in the array where the search for item should begin. For example, search("hello", arr, 0) should search for “hello” in the full array (beginning at position 0), whereas search("hello", arr, 2) should search for "hello" in the subarray that begins at position 2 and goes to the end of the array.

Submitting your work for Part I
Coming soon!

Part II: Programming problems
60-70 points total

Problem 5: Adding methods to the ArrayBag class
25 points total

Begin by downloading the following files:

Bag.java
ArrayBag.java
Put them in the ps1 folder that you’re using for your work on this assignment, and open the folder in VS Code.

In ArrayBag.java, add the methods described below to the ArrayBag class, and then add code to the main() method to test these methods. In addition, you should update the Bag interface that we have given you in Bag.java to include these new methods. These methods should be publicly accessible. You should not add any new fields to the class.

public int capacity()
This method should return the maximum number of items that the ArrayBag is able to hold. This value does not depend on the number of items that are currently in the ArrayBag — it is the same as the maximum size specified when the ArrayBag was created.

public boolean isFull()
This method should return true if the called ArrayBag is full, and false otherwise.

public void increaseCapacity(int amount)
This method should increase the maximum capacity of the called ArrayBag by the specified amount. For example, if b has a maximum capacity of 10, then b.increaseCapacity(5) should give b a maximum capacity of 15. As part of your implementation, you will need to create a new array with room to support the new maximum capacity, copy any existing items into that array, and replace the original array with the new one by storing its reference in the called object.

Special cases:

If the parameter is 0, the method should just return without making any changes to the called object.
If the parameter is negative, the method should throw an IllegalArgumentException. See our second ArrayBag constructor for an example of throwing an exception.
public boolean removeItems(Bag other)
This method should attempt to remove from the called ArrayBag all occurrences of the items found in the parameter other. If the called object contains multiple copies of an item from otherBag, all of the copies should be removed. The method should return true if one or more items are removed and false otherwise.

Special cases:

If the parameter is null, the method should throw an IllegalArgumentException.
If the parameter is an empty Bag, the method should return false.
Note that the parameter is of type Bag. As a result, your method should use method calls to access the internals of that bag. See our implementation of the containsAll() method for an example of this.

public Bag unionWith(Bag other)
This method should create and return an ArrayBag containing one occurrence of any item that is found in either the called object or the parameter other. For full credit, the resulting bag should not include any duplicates. For example, if b1 represents the bag {2, 2, 3, 5, 7, 7, 7, 8} and b2 represents the bag {2, 3, 4, 5, 5, 6, 7}, then b1.unionWith(b2) should return an ArrayBag representing the bag {2, 3, 4, 5, 6, 7, 8}. Give the new ArrayBag a maximum size that is the sum of the two bag’s maximum sizes.

Special cases:

If one of the bags is empty, the method should return an ArrayBag containing one occurrence of each item in the non-empty bag.

If both of the bags are empty, the method should return an empty ArrayBag.

If the parameter is null, the method should throw an IllegalArgumentException.

Here again, the parameter is of type Bag. As a result, your method should use method calls to access the internals of that bag. See our implementation of the containsAll() method for an example of this. The return type is also Bag, but polymorphism allows you to just return the ArrayBag that you create, because ArrayBag implements Bag.

Problem 6: Recursion and strings
10-20 points total; 5 points each part

We will cover the material needed for this problem on January 30.

In a file named StringRecursion.java, implement the methods described below, and then create a main() method to test these methods.

Requirements:

The methods that you write must be purely recursive. The use of iteration (i.e., for, while, or do-while loops) is not allowed.
The only built-in String methods that you may use are charAt, length, equals, and substring. No use of other String methods is allowed. In addition, make sure to follow any additional restrictions specified in the problem.
Do not use any global variables — i.e., variables that are declared outside of a method.
Use the headers specified for the methods without changing them in any way.
Limit yourself to writing the methods specified below. Do not write any additional “helper” methods that assist the required methods; rather, the methods listed below should provide all of their required functionality by themselves.
Here are the methods:

public static void printLetters(String str)
This method should use recursion to print the individual characters in the string str, separated by commas. All characters in the string should be printed, not just the letters. For example, printLetters("Rabbit") should print

R, a, b, b, i, t
and printLetters("I like to recurse!") should print

I,  , l, i, k, e,  , t, o,  , r, e, c, u, r, s, e, !
Note that there is a single space between each comma and the subsequent character. The method should not do any printing if the empty string ("") or the value null is passed in as the parameter; it should simply return.

public static String replace(String str, char oldChar, char newChar)
This method should use recursion to return a String that is formed by replacing all occurrences of the character oldChar in the string str with the character newChar. For example:

replace("base case", 'e', 'y') should return "basy casy"
replace("base case", 'r', 'y') should return "base case"
This method should not do any printing; it should simply return the resulting string.

Special cases:

If the first parameter is null, the method should return null.

If the first parameter is the empty string (""), the method should return the empty string.

(required for grad-credit students; “partial” extra credit for others)

public static int indexOf(char ch, String str)
This method should use recursion to find and return the index of the first occurrence of the character ch in the string str, or -1 if ch does not occur in str. For example:

indexOf('b', "Rabbit") should return 2
indexOf('P', "Rabbit") should return -1
The method should return -1 if the empty string ("") or the value null is passed in as the second parameter. The String class comes with a built-in indexOf() method; you may not use that method in your solution!

(required for grad-credit students; “partial” extra credit for others)

public static String trim(String str)
This method should take a string str and use recursion to return a string in which any leading and/or trailing spaces in the original string are removed. For example:

trim(" hello world ") should return the string "hello world"
trim("recursion ") should return the string "recursion"
The String class comes with a built-in trim() method that does the same thing as the method that we’re asking you to write; you may not use that method in your solution!

Special cases:

If the parameter is null, the method should return null.

If the parameter is the empty string, the method should return the empty string.

Problem 7: A Letter Square solver
25 points

We will cover the material needed for this problem on January 30.

The New York Times includes a daily puzzle called “Letter Boxed.” It involves a set of 12 letters arranged around the sides of a square, such as the following:



To solve the puzzle, you need to come up with a sequence of English words in which each letter in the puzzle appears at least once. In addition, the words in the sequence must observe the following constraints:

Each word must be at least 3 letters long.

Adjacent letters must come from different sides of the square. For example, when solving the puzzle above, if the first letter in a word is T, the second letter in that word cannot be either A or E, since A and E are on the same side of the square as T.

One word that can be formed from the puzzle above is TIME. I is on a different side of the square than T, M is on a different side than I, and E is on a different side than M.

The last letter of one word of the sequence must match the first letter in the next word in the sequence. For example, if we use TIME as the first word in our solution, the second word must then begin with E, since TIME ends with E.

For a given puzzle, there are many possible solutions, but solutions that use fewer words are preferred. For the puzzle above, one possible solution is

LIMES
STONES
SHAKY
However, an even better solution is

MILESTONES
SHAKY
because it uses fewer words.

In this problem, you will write a program that solves this type of puzzle using recursive backtracking!

Task 1: download and review the provided code
Begin by downloading the following zip file: problem7.zip

Unzip this archive, and you should find a folder named problem7 that contains all of the files that you need for this problem. You should not move any of the files out of the problem7 folder.

Keep all of the files in the problem7 folder, and open that folder in VS Code using the File->Open Folder or File->Open menu option.

We have provided:

a class called LetterSquare that will serve as a blueprint for objects that represent a Letter Square puzzle, and that can be used to solve the puzzle. We have included some starter code, and you will implement two key methods of the class.

a separate class called Dictionary that serves as a blueprint for a Dictionary object that you can use to check if a string is a word or the prefix of a word in a collection of common English words. You should not modify this class in any way.

a text file called word_list.txt containing the words in the dictionary.

Begin by reading over the code that we have given you in LetterSquare.java. The provided code includes:

a constant called dictionary that refers to the Dictionary object described above. The two key methods in this object are:

dictionary.hasString(s), which returns true if the string s is either a word or the prefix of a word in the dictionary of words, and false otherwise. For example, because "game" is a word in the dictionary, all of the following calls will return true:

dictionary.hasString("g")
dictionary.hasString("ga")
dictionary.hasString("gam")
dictionary.hasString("game")
However, dictionary.hasString("gome") will return false, because the string `”gome” is neither a word nor the prefix of a word in the dictionary.

dictionary.hasFullWord(s), which returns true if the string s is a “full word” (i.e., a word that can stand on its own, and is not only a prefix) in the dictionary of words, and false otherwise. For example:

dictionary.hasFullWord("game") will return true, because "game" is a full word in the dictionary.

dictionary.hasFullWord("g"), dictionary.hasFullWord("ga"), and dictionary.hasFullWord("gam") will all return false, because these strings are not full words in the dictionary.

a field called sides that refers to an array of strings. It is used to store the letters on each side of the puzzle, with each side represented by a three-letter string. For example, the sides of the puzzle above would be stored as the following array:

{"tae", "nih", "omk", "lys"}
(Either lower-case or upper-case characters can be used.)

a field called letters that refers to an array of single-letter strings. This array is used to store the individual letters in the puzzle. For example, the letters in the puzzle above would be stored as the following array:

{"t", "a", "e", "n", "i", "h", "o", "m", "k", "l" , "y", "s"}
(Note: We are using an array of String objects, not an array of char values. Doing so simplifies some of the necessary constraint-checking. In particular, it allows us to use the built-in contains method from the String class to determine if a given letter is found within a given string.)

a field called words that refers to an array of strings. It will be used to store the words in the solution to the puzzle. When the LetterSquare object is created, this array is initially filled with empty strings.

a constructor that takes an array representing the sides of the puzzle and initializes the fields.

a toString method that returns a string representation of the puzzle that will be used when you print a LetterSquare object.

private static helper methods that make it easier to perform two types of operations on String objects:

one called lastLetter(word) that can be used to obtain a single-letter string consisting of the last letter in the string word; for example, lastLetter("world") would return the string "d".

one called removeLast(word) that takes a string word and returns the new string formed by removing the last letter in word; for example, removeLast("world") would return the string "worl".

a private method called addLetter that takes a single-character string letter and an integer wordNum, and that adds the specified letter to the end of the word in position wordNum of the words array.

a private method called removeLetter that takes an integer wordNum and that removes the last letter from the word in position wordNum in the words array.

a private method called alreadyUsed that takes an arbitrary string word and that returns the boolean value true if word is already one of the words in the solution, and false otherwise.

a private method called onSameSide that takes two single-character strings letter1 and letter2, and that returns true if letter1 and letter2 are on the same side of the puzzle, and false otherwise.

a private method called allLettersUsed that returns the boolean value true if all of the letters in the puzzle have been used somewhere in the solution, and false otherwise.

a private method called printSolution that takes an integer wordNum and prints the words in positions 0 through wordNum of the words array.

the skeleton of a private method called solveRB that you will implement. This is the recursive-backtracking method, and it should return true if a solution to the puzzle has been found and false if no solution has been found (i.e., if the method is backtracking).

the skeleton of a private method called isValid that you will also implement. This method should be called by solveRB to check if a given letter would work as the next letter in the current word.

a public method named solve that clients can call to solve a LetterSquare puzzle. It repeatedly calls solveRB with increasing values of maxWords until it finds a solution to the puzzle, or until it has tried and failed to find solutions of up to 10 words.

a main method that allows the user to enter and solve a puzzle.

The only methods that you should change are solveRB and isValid. All of the other provided methods should be left unchanged. You are welcome to add your own additional helper methods, although doing so is not required.

Task 2: implement isValid
Once you have reviewed the provided code, you can begin to implement the bodies of the two methods that you are required to write. You should not change the headers that we have provided.

You should start by implementing the isValid helper method that will be used to check if a given letter would work as the next letter in the current word, given the words and prefixes in the dictionary and the constraints of the puzzle described at the beginning of the problem.

This method must take three parameters:

letter: a single-character string representing the letter whose validity is being tested

wordNum: an integer specifying the index of the position in the words array of the word that is currently being built

charNum: an integer specifying the index of the position within the current word that letter is being considered for.

It should return true if the specified letter is a valid choice for the letter in position charNum of the word in position wordNum of the words array, and false otherwise. You may assume that only appropriate values will be passed in. In particular, you may assume that letter is one of the letters of the puzzle.

The constraints that you need to check will depend on the value of the charNum parameter (and possibly also of the wordNum parameter).

For example, let’s assume that we have the following situation:

We are solving the puzzle shown at the start of the problem (the one with sides {"tae", "nih", "omk", "lys"}).

We are looking for a solution of at most 2 words.

The current partial solution is {"time", ...}.

We are within the call this.solveRB(0, 4, 2) – i.e., we are attempting to expand the word in position 0 ("time") by finding a letter that would work in position 4 of that word.

Given this situation:

this.isValid("l", 0, 4) should return true because "l" is on a different side of the puzzle than "e" (the letter that was added to give "time") and "timel" is a word and/or a prefix of a word in the dictionary (which we know because dictionary.hasString("timel") returns true)

this.isValid("s", 0, 4) should also return true because "s" is on different side of the puzzle than "e" and dictionary.hasString("times") returns true

this.isValid("a", 0, 4) should return false because "a" is on the same side of the puzzle as "e"

this.isValid("y", 0, 4) should return false because "timey" is neither a word nor a prefix of a word in the dictionary (which we know because dictionary.hasString("timey") returns false).

Now imagine that we have added the letter "s" to the partial solution described above to give a new partial solution {"times", ...} and that we are now focused on the first letter in second word in the solution (i.e., that we are within the call this.solveRB(1, 0, 2)). Given this situation:

this.isValid("s", 1, 0) should return true because we are focused on the first letter in a new word and "s" is the last letter of the previous word ("times")

this.isValid("l", 1, 0) should return false because we are focused on the first letter in a new word and "l" is not the last letter of the previous word.

Other notes:

You should take advantage of one or more of the methods in the Dictionary object given by the class constant dictionary.

You will need a special case for handling the first character of the first word in the solution. In that case, any letter of the puzzle is valid!

When is considering a case in which the current word is being expanded by one letter, the method should return false if adding the letter would produce a word that is already part of the solution. Otherwise, you could end up producing a solution that repeatedly uses the same word (e.g., {"toast", "toast", ...}). Note that we have given you a helper method that makes it easy to check for this case!

isValid should only determine if the specified letter is a valid choice for the next letter. It should not actually add the letter to the solution.

We strongly encourage you to thoroughly test your isValid method to ensure that it works in all cases!

The best way to do this is to add some temporary test code to the beginning of the main method in LetterSquare.

For example, the description above includes some cases involving isValid that are based on the puzzle shown at the start of the problem (the one with sides {"tae", "nih", "omk", "lys"}).

You could test these cases by adding temporary code that looks like the following to the start of main:

String[] testSides = {"tae", "nih", "omk", "lys"};
LetterSquare test = new LetterSquare(testSides);
test.words[0] = "time";

// to test cases involving the second or third word,
// assign strings to other positions in test.words

// should get true
System.out.println(test.isValid("l", 0, 4));

// should get false
System.out.println(test.isValid("a", 0, 4));

// other tests go here

// exit the program after testing
System.exit(0);
To test other scenarios, you can change the strings in the testSides array and/or the strings assigned to the positions in the test.words array.

Once you have convinced yourself that your isValid method works in all cases, you can remove any temporary test code that you added to the start of main and run the program to see if it works.

Task 3: implement solveRB
The recursive-backtracking method (solveRB) must take three integer parameters:

wordNum: the index of the position in the words array of the word that is currently being built

charNum: the index of the character within the current word that this call is responsible for adding

maxWords: the maximum number of words that the solution is allowed to have.

It should follow the same basic approach as the recursive-backtracking template from lecture (the one designed to find a single solution). However, there will be a couple of key differences:

In addition to a base case that checks if the puzzle has been solved, you will need a second base case for calls in which wordNum is too big, given the value of maxWords. For example, the call this.solveRB(3, 0, 3) should return false, because if maxWords is 3, we shouldn’t be looking for a fourth word (which is what a first input of 3 indicates).

If the current call is able to add a letter to the solution, you may need to make two separate recursive calls:

First, you should make a call that attempts to expand the current word in the solution, making it one letter longer.

Then, if the first recursive call does not succeed in finding a solution and if the current word in the solution is a full word of at least three letters, you should make a second recursive call that moves on to the next word in the solution.

For example, let’s say that the call this.solveRB(0, 3, 2) adds the letter e to position 3 of the first word in the solution, giving us the string "time" as that first word.

First, we would make the call this.solveRB(0, 4, 2) to see if we can expand "time" into a longer word.

Then, if the first call returns false, we would check if "time" is a full word of at least 3 letters. Because it is, we would make the call this.solveRB(1, 0, 2) to move onto the second word in the solution (the one in position 1 of the words array). Note that we also use a 0 for the second input of this call, since the call will be focused on the first letter in that new word.

Note that you should only make a second recursive call if the first call returns false and the current word is a full word of at least three letters.

Other notes:

Make sure that you use the addLetter() and removeLetter() methods when updating the state of the puzzle.

In addition, take advantage of the other helper methods that we have provided – including the methods in the Dictionary object given by the class constant dictionary.

Task 4: test your code
Below are some puzzles that you can use for testing your full implementation. (In each case, we specify the four sides of the puzzle, separated by commas. You should enter them one at a time, without the commas!)

puv, rce, otl, diy
This has a single-word solution: productively

puv, rce, otl, dix
This has a two-word solution:

productive
expel
abc, def, ghi, jkl
The shortest possible solution is one of length 6:

jibe
eagle
elf
fleck
kea
ahead
Depending on how you implement the methods, you may end up with different solutions than the ones shown above. However, you should still end up with a solution that has the same number of words as our solution.

If your program doesn’t correctly solve these test cases, see the PS 1 FAQ for suggestions on debugging.

