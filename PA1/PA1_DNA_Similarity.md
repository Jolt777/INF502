# PA 1 - DNA Similarity

## Name: Jolten Larremore
## Insturctor: Dr. Igor Steinmacher
## Course: INF502
## Date: 10/08/2020

### Short Description of my Solution Appoarch in Implementing the Algorithm
#### (as explained one function at a time)



### Source Code

```
import os


def important(s1, s2):
    if not len(s1) == len(s2):
        print("The lengths of the two DNA sequences does not match.")
        print("Sequence 1, which is depicted as (", s1, ") has a length of ", str(len(s1)))
        print("Sequence 2, which is depicted as (", s2, ") has a length of ", str(len(s2)))
        return False
    else:
        print("The sequences are the same length! Please continue.")


def vital(s):
    nucleotides = ['A', 'T', 'C', 'G']
    for i in s:
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
    vital(s1)
    vital(s2)
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


def max_chain(s1, s2, ms):
    important(s1, s2)
    vital(s1)
    vital(s2)
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
                print(s1n1)
                print(s2n1)
                collection_1, collection_2 = nm_remove(s1n1, s2n1)
                print("\n")
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



#### Maximum Chain Approach

