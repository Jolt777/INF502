# PA 1 - DNA Similarity

## Name: Jolten Larremore
## Insturctor: Dr. Igor Steinmacher
## Course: INF502
## Date: 10/08/2020



## Igor Feedback

* Overall: Maximum score works. Contiguous chain does not. Too many prints makes it really hard to read. The errors are found with if/else, but the algorithm is not stopped. The function names are not meaningful. Max contiguous does not work. The input as a string is not a good decision (use an int or single char). See comments in the code. Last submission was late.

* Number of matches: Correct, but it does not show WHICH configuration is the best one (number of shifts).
* Maximum chain: Does not give the right answer
* User-input: OK. But I need to restart if there is one error (filename for example), and I need to use a string
* Max Shift: OK
* Exception handling/checks: It is there, but does not catch and treat. I even receive an IndexError when the sequences have different length
    - Files: OK!
    - Conversions: OK
    - Inputs: OK... But, errors appear just after input everything (If a filename is wrong, let me know, and let me provide another file)
    - same size, no bad chars, etc.: See above.
* Functions: Good

* Variable + function names: Not good

* **Your grade is 50/100**


### Short Description of my Solution Appoarch in Implementing the Algorithm
#### (as explained one function at a time)
    * import os
        * import the "os" python module
               * The "os" python module provides a portable way of using operating system dependent functionality.
               
    * important(s1, s2)
        * Takes s1 (for sequence 1) and s2 (for sequence 2) as the inputs.
        * Check to see if the lengths of both sequences are equal.
               * If not, three print functions will be activated, telling the user that the lengths of the two sequences does not match. In addition, the lengths of both sequences are posted, so that the user will have a visual on the statement Python is trying to make.
               * If the sequences do match, a print statement will be activated, which will tell the user that the sequences are in the same length, and will continue on with the run.
               
    * vital(s)
        * This function takes in a sequence, "s", as the input
        * The value "nucleotides" is created to store a list of the nucleotides: A, T, C, G
        * A for loop is created as means of reading each base ("i") in "s"
            * A conditional IF statement to check if the base doesn't match any nucleotides
                  * If it does, a print function will inform the user that an error has been found, and "returns" False.
                  * If it does not, the loop is closed when every base in the sequence is a nucleotide.
            * A print function will inform the user that the seqeunce has the right nucleotides within it, and that tha real analysis begins.
            * The function ends when it "returns" True.

    * read_for_matches(s1, s2)
        * This function takes in "s1" and "s2" as the inputs.
        * A "match" value is created, which stores a zero.
        * A for loop is created, which will reads every nucleotide in a range from zero to the total length of sequence 1
            * Within the loop, the nucleotide in s1 and s2 is stored in the variables "s1_base" and "s2_base" respectively.
            * A conditional statement (IF) checks to see if the current "s1_base" matches with the current "s2_base"
                  * If it does, the "match" value is increase by 1
                  * If it does not, an "else" statement will be run. In it, a "continue" statement will tell Python to continue the loop.
        * Once the for loop is completed and close, the function ends with a "return" of the "match" value.
   
    * num_of_matches(s1, s2, ms)
         * This function is design to read the pairwise alignment between the two sequences, stores the amount of matches per each shift per each sequence, and finds the maximum out of a list containing the recorded amount of matches.
         * The maximum shift (ms) determines the amount of nucleotides in a sequence shifted.
               * It should happen in three phases:
                     1. No shifts occur in either sequence
                     2. The shifts occur in sequence one only.
                     3. The shifts occur in sequence two only.
    
    
    * nm_remove(s1, s2)
         * Takes in s1 and s2 as the inputs.
         * A variable titled "collection_1" is formed, storing only an empty string.
         * A variable titled "collection_2" is formed, storing only an empty string.
         * A for loop is created, which will reads each nucleotide ("n") in the entire length of s1. The loop starts with position 0 of the s1 sequence.
            * Within the loop, the nucleotide in s1 and s2 is stored in the variables "s1_base" and "s2_base" respectively.
            * A condition "if" statment checks to make sure the current "s1_base" matches with the current "s2_base"
                  * If it does, "s1_base" and "s2_base" is added to "collection_1" and "collection_2" respectively.
                  * If it does not, an "elif" statement checks to make sure the current "s1_base" does not match with the current "s2_base"
                        * If it does, a "_" is added to both "collection_1" and "collection_2" respectively.
                              * If the "elif" statment fails for some reason, a print statment will tell the user an error has been found.
        * Once the for loop is completed and close, the function ends with a "return" of collection_1 and collection_2.
    
    * collect_max_cm(collection 1, collection 2)
         * Takes in s1, s2, and ms as the inputs.
         * A value "m" (for contiguous matches) is set to zero.
         * An empty list is stored in the variable "rc" (stands for "real collection")
         * A for loop is created, which reads every nucleotide in the entire legnth of collection_1
            * Within the loop, the nucleotide or "_" in collections 1 and 2 is stored in the variables "char1" and "char2" respectively.
            * A conditional "if" statement that checks to see if the current state of "char1" and "char2" does not contain a "_" in them.
               * If it does not, the "m" value is increase by 1.
               * If it does, an "elif" statment checks to see if the current state of "char1" and "char2" does contain a "_" in them.
                     * If the "elif" statement succeeds in its performance, the current value of "m" is added to the empty "rc" list using append()
                     * If the "elif" statement fails, a print statement tells the user an error has been detected.
         * Once the loop is completed and close, the function closes by returning the "rc" list.
    
    * max_value(contiguous)
         * This function takes in the "contiguous" list as the input.
         * It only has a single line within the function, which is a return statement.
               * By using the return statmenet, it ends the function, and returns the maximum value of the "contiguous" list to the caller.
    
    * max_chain(s_1, s_2, ms)
         * This function is to detect and keep any matches found between the two sequences in two collections, one for each sequence. Then, it detects and collects the maximum contiguous matches found in the pairwise alignment. Next, these matches are store in a list. Lastly, the maximum value of that list is chosen as the answer.
         * The maximum shift (ms) determines the amount of nucleotides in a sequence shifted.
               * It should happen in three phases:
                     1. No shifts occur in either sequence
                     2. The shifts occur in sequence one only.
                     3. The shifts occur in sequence two only.
    
    * file_input(f)
         * This is where the execution handling aspect of the code takes place.
         * The function takes in one file as the input.
         * The function will first try to do the following:
               * Assign the variable "seq" (for sequence) to an empty string
               * Using a "with" statement, Python will open the .txt file, in read mode, as the label "input_file".
                  * The user input files will always have one line reserve for the DNA sequence.
                  * A "for" loop is performed within the "with" statement, which will read every line in the file.
                        * The line that is read is stored in the "seq" variable.
         * If there's an I/OError detected, the function will print out a message to the user, saying that the file the user put in is not found.
    
    * print_intro()
         * Three print functions will be used to create a title card, with the words "DNA SIMILARITY!"
         * print('\n\n\n') for a 3 line breaks.
         * A fourth print function that will ask the user to please enter the following information (i.e. user inputs)
    
    * user_input()
         * An os.system('clear') will be run first. 
               * This will tell Python to talk to the operating system, and ask the system to run a clear command.
               * This is to make every run of the code starts fresh with a clear terminal window.
         * A print_intro() function is the next piece of code to be run.
         * A "ms" variable is created to store the user input on the maximum shift
               * This user input is stored in the form of an integer
         * An "approach" variable is created to store the user input of the answer on which approach the user wants to use.
               * The answer is either "number of matches" or "maximum chain"
                     * This user input is stored in the form of a string
         * A variable titled "file_1" will store a string version of the first input file the user put in.
         * A variable titled "file_2" will store a string version of the second input file the user put in.
         * print("\n") for a single line break.
         * An "s1" variable will store the first DNA sequence
               * The first DNA sequence is originated as the output of the file_input() function
         * An "s2" variable will store the second DNA sequence
               * The second DNA sequence is originated as the output of the file_input() function
         * print("\n") for a single line break.
         * A conditional "if" statement appears where it checks to see if the "approach" user input matches with this string: "number of matches"
               * If it does, the number_of_matches function will be run.
                     * The number_of_matches() function takes in the variables "s1", "s2", and "ms" as the inputs
               * If it does not, a conditional "elif" statment appears where it checks to see if the "approach" user input matches with this string: "maximum chain"
                     * If it does, the max_chain() function will be run.
                           * The max_chain() function takes in the variables "s1", "s2", and "ms" as the inputs.
    
    * while(True)
         * A while(True) assures Python that the loop goes on forever until a break mechanism is encountered.
         * Inside the while(True) lies the user_input() function, which will be activated first.
               * The user_input() will be the first function to be run by Python.
         * After everything within the user_input() is complete, a break mechanism is encountered as means of signaling the end of the code's run.


### Source Code

```
#Igor: nothing happens if the length of the sequences are the same.
#getting an exception (IndexError).
#The same for the char diff than ACTG
#TOO MANY PRINTS...
#The algorithm does not tell me what is the number of shifts for the
#max score or max contiguous 
import os

#Igor: function name does not tell me anything
#You got the problem, but the algorithm does not stop...IndexError
def important(s1, s2):
    if not len(s1) == len(s2):
        print("The lengths of the two DNA sequences does not match.")
        print("Sequence 1, which is depicted as (", s1, ") has a length of ", str(len(s1)))
        print("Sequence 2, which is depicted as (", s2, ") has a length of ", str(len(s2)))
        return False
    else:
        print("The sequences are the same length! Please continue.")

#Igor: getting error here because the code is considering the line break
# although my file has no bad character, I am receiving a "I found an error"
#Moreover, the algorithm does not stop when this happens
def vital(s):
    nucleotides = ['A', 'T', 'C', 'G']
    for i in s.strip():
        if i not in nucleotides:
            print("I found an error")
            return False
    print(s, " has the right nucleotides! Everything checks out! Now on to the analysis!")
    return True


def read_for_matches(s1, s2):
    match = 0
    for nucleotide in range(0, len(s1)):
        s1_base = s1[nucleotide]
        s2_base = s2[nucleotide]
        if s1_base == s2_base:
            match += 1
        else:
            continue
    return match


# "s1" for sequence 1
# "s2" for sequence 2
# "ms" for maximum shift

def num_of_matches(s1, s2, ms):
    # initiate the "important" function, taking in sequence 1 and sequence 2 as the inputs.
    important(s1, s2)
    # initiate the "vital" function, taking in sequence 1 and sequence 2 as the inputs.
    #vital(s1)
    #vital(s2)
    print("\n")
    # "shift" for the current shift position.
    shift = -1
    lr = -1
    score = []
    # multiplier for the amount of dashes added in each sequence after each shift
    x1 = 0
    x2 = 0
    while shift < ms:
        if shift < 0:
            # number of matches collected, and stored in "match"
            match = read_for_matches(s1, s2)
            score.append(match)
            print(s1)
            print(s2)
            print(score)
            print("\n")
        else:
            if lr < ms:
                s1_n1 = ("-" * x1) + s1
                s2_n1 = s2 + ("-" * x1)
                match = read_for_matches(s1_n1, s2_n1)
                score.append(match)
                print(s1_n1)
                print(s2_n1)
                print(score)
                print("\n")
            else:
                if lr == ms:
                    x2 += 1
                    shift_rs = 0
                    shift = shift * shift_rs
                else:
                    if x2 < 0:
                        s1_n2 = s1 + ("-" * x2)
                        s2_n2 = ("-" * x2) + s2
                        match = read_for_matches(s1_n2, s2_n2)
                        score.append(match)
                        print(s1_n2)
                        print(s2_n2)
                        print(score)
                        print("\n")
        x1 += 1
        lr += 1
        shift += 1
    print("The Maximum Score is = ", max(score))


def nm_remove(s1, s2):
    collection_1 = ''
    collection_2 = ''
    for n in range(0, len(s1)):
        s1_base = s1[n]
        s2_base = s2[n]
        if s1_base == s2_base:
            collection_1 += s1_base
            collection_2 += s2_base
        elif s1_base != s2_base:
            collection_1 += "_"
            collection_2 += "_"
        else:
            print("I found an error.")
    return collection_1, collection_2


def collect_max_cm(collection_1, collection_2):
    m = 0
    rc = []
    for c in range(0, len(collection_1)):
        char1 = collection_1[c]
        char2 = collection_2[c]
        if char1 != "_" and char2 != "_":
            m += 1
        elif char1 == "_" and char2 == "_":
            rc.append(m)
            m = m * 0
        else:
            print("Error. Please look over the code thoroughly, re-work it, and try again.")
    return rc


def max_value(contiguous):
    return max(contiguous)

#Igor: THis does not work...
def max_chain(s1, s2, ms):
    important(s1, s2)
    #vital(s1)
    #vital(s2)
    print("\n")
    s = -1
    x1 = 0
    x2 = 0
    lr = -1
    contiguous = []
    while s < ms:
        if s < 0:
            print(s1)
            print(s2)
            collection_1, collection_2 = nm_remove(s1, s2)
            print("\n")
            contiguous = collect_max_cm(collection_1, collection_2)
        else:
            if lr < ms:
                s1n1 = ("-" * x1) + s1
                s2n1 = s2 + ("-" * x1)
             #   print(s1n1)
             #   print(s2n1)
                collection_1, collection_2 = nm_remove(s1n1, s2n1)
             #   print("\n")
                contiguous = collect_max_cm(collection_1, collection_2)
            else:
                if lr == ms:
                    x2 += 1
                    s_rs = 0
                    s = s * s_rs
                else:
                    if x2 < 0:
                        s1n2 = s1 + ("-" * x2)
                        s2n2 = ("-" * x2) + s2
                        print(s1n2)
                        print(s2n2)
                        collection_1, collection_2 = nm_remove(s1n2, s2n2)
                        print("\n")
                        contiguous = collect_max_cm(collection_1, collection_2)
        x1 += 1
        lr += 1
        s += 1
    result = max_value(contiguous)
    print("The Maximum Contiguous for this setting is = ", result)


def file_input(f):
    try:
        seq = ""
        with open(f, 'r') as input_file:
            for line in input_file:
                seq += line
        return seq
    except IOError:
        print("File not found!")


def print_intro():
    print("\t********************************************")
    print("\t************* DNA SIMILARITY!!! ************")
    print("\t********************************************")
    # 3 line break
    print("\n\n\n")
    print("Please enter the following information: ")


def user_input():
    os.system('clear')
    print_intro()
    #Igor: Please use number or single char instead of a long string as input
    ms = int(input("Enter the maximum shift: "))
    approach = str(input("Enter the approach that you want to use (number of matches/maximum chain): "))
    file_1 = str(input("Enter the name of the first input file: "))
    file_2 = str(input("Enter the name of the second input file: "))
    print("\n")
    s1 = file_input(file_1)
    s2 = file_input(file_2)
    print("\n")
    if approach == "number of matches":
        num_of_matches(s1, s2, ms)
    elif approach == "maximum chain":
        max_chain(s1, s2, ms)


while True:
    user_input()
    break

```

### Results
### Number of Matches Approach

**Files Used**:
* Seq1.txt ---> ACTGACTTTT
* Seq2.txt ---> TTTAGCCGAT

**Maximum Shift Selected:** 2

**Outcome:**
********************************************
************* DNA SIMILARITY!!! ************
********************************************




Please enter the following information: 
Enter the maximum shift: **TERM environment variable not set.**
2
Enter the approach that you want to use (number of matches/maximum chain): number of matches
Enter the name of the first input file: Seq1.txt
Enter the name of the second input file: Seq2.txt




The sequences are the same length! Please continue.
ACTGACTTTT  has the right nucleotides! Everything checks out! Now on to the analysis!
TTTAGCCGAT  has the right nucleotides! Everything checks out! Now on to the analysis!


ACTGACTTTT
TTTAGCCGAT
[3]


-ACTGACTTTT
TTTAGCCGAT-
[3, 3]


--ACTGACTTTT
TTTAGCCGAT--
[3, 3, 1]


The Maximum Score is =  3

### Maximum Chain Approach

**Files Used:**
* Seq1.txt ---> ACTGACTTTT
* Seq2.txt ---> TTTAGCCGAT

**Maximum Shift Selected:** 2

**Outcome:**
********************************************
************* DNA SIMILARITY!!! ************
********************************************




Please enter the following information: 
Enter the maximum shift: TERM environment variable not set.
2
Enter the approach that you want to use (number of matches/maximum chain): maximum chain
Enter the name of the first input file: Seq1.txt
Enter the name of the second input file: Seq2.txt




The sequences are the same length! Please continue.
ACTGACTTTT  has the right nucleotides! Everything checks out! Now on to the analysis!
TTTAGCCGAT  has the right nucleotides! Everything checks out! Now on to the analysis!


ACTGACTTTT
TTTAGCCGAT


-ACTGACTTTT
TTTAGCCGAT-


--ACTGACTTTT
TTTAGCCGAT--


The Maximum Contiguous for this setting is =  1

### Hurdles and Benefits of Developing Each Approach, and How I Handled Them
#### Number of Matches Approach

Hurdles:
  * Having the conditional statmenets in the num_of_matches function to be read correctly (and still am by the time I'm writing this).
  * Having the real amount of matches to be printed for the user to see it.
      * Solution: In the read_for_matches() function, set a "return" statement at the end. This is done to have the amount be sent to the caller, which is then stored in a variable titled "match".

Benefits:
  * The simplied setup of adding a "number of matches" by 1, whenever there's a match detected in the read_for_matches() function. 

#### Maximum Chain Approach

Hurdles
   * Having great difficulty distinguishin between a "normal" match and a "contiguous" match.
      * Solution: With heavy research and assistance from the instructor, I realized that the amount of "contiguous" matches is determined by the adjacency of the "normal" matches.
   * Finding a way to return the two collections in the nm_removal function.
      * Solution: A simple write-up like this: "return collection1, collection2". This is to make sure the "return" statement sends multiple values to the caller.

Benefits
   * Having a nm_remove() function be programmed to detect "normal" matches and remove the nucleotides that are not matching from the pairwise alignment.

