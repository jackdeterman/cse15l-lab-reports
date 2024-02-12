_Part 1_

The bug I am choosing from Week 4's lab is the bug present in the `append` method in the `LinkedList` class. 

<br>
<br>
<br>

Here is a failure-inducing input for the buggy method:

```
@Test 
	public void testappend() {
    LinkedList test = new LinkedList();
    test.append(1);
    test.append(2);
    test.append(3);
    assertEquals(test.first(), 1);
    assertEquals(test.last(), 3);
	}
```
<br>

The associated code that causes this to fail is the following:
```
while(n.next != null) {
            n = n.next;
            n.next = new Node(value, null);
        }
```

<br>


An input that doesn't induce a failure is

```
@Test 
	public void testappend() {
    LinkedList test = new LinkedList();
    test.append(1);
    assertEquals(test.first(), 1);
	}
```

<br>

The code associated with this test's passing is 

```
Node n = this.root;
        if(n.next == null) {
            n.next = new Node(value, null);
            return;
        }
```
<br>
<br>

The symptoms associated with running the tests are shown below:

![image](Lab_Report_3_Tests.png)

<br>
<br>

And the bug, as before and after code blocks, is also shown below:

![image](Lab_Report_3_Before.png)
![image](Lab_Report_3_After.png)

<br>

The issue in the starter code is in the logic of the `while`-loop. Each time through the `while`-loop, `n.next` would be assigned to a new `Node` containing the `value` the user wanted to append to the list. As such, `n.next == null` was never satisfied, as `n.next` would be assigned to a new `Node` every time the `while`-loop was executed. This meant that the loop would run forever if the program reached it. By moving the assignment of the new `Node` to the outside of the `while`-loop, we prevent an infinite amount of new `Node` assignments. Now, only _after_ reaching the end of the list and satisfying `n.next == null`, we create a new `Node` with the desired `value` and append it to the list.


<br>
<br>
<br>

_PART 2_

<br>

Examples of using `grep -A`:

```
grep -A 1 "Alcohol" Session2-PDF.txt
Identifying ED Patients with Alcohol Problems
ーー
Alcohol problems defined
Alcohol problems designate a spectrum from risk behavior to illness, and from problematic consumption to alcohol use disorder.
```

```
grep -A 1 "Clinical" Session2-PDF.txt
willing to have blood drawn or submit to breathalyzers. Clinical staff may be uncomfortable asking some types of questions.
ーー
Clinical impression
Clinicians often use their general impression to help with
```
<br>
<br>

Examples of using `grep -i`:

```
grep -i "Clinical" Session2-PDF.txt
alcohol concentration (BAC), coupled with our clinical screening test to an already lengthy list of clinical care duties.
In clinical practice, several practical issues will make all the willing to have blood drawn or submit to breathalyzers. Clinical
```

```
grep -i "Alcohol" Session2-PDF.txt
Identifying ED Patients with Alcohol Problems
Many patients in the emergency department (ED) have alcohol further examine and refine alcohol-screening questionnaires in the
Alcohol problems defined
```
<br>
<br>

Examples of using `grep -o`:

```
grep -i -o "Alcohol" Session2-PDF.txt
Alcohol
alcohol
alcohol
Alcohol
Alcohol
```

```
grep -i -o "Clinician" Session2-PDF.txt
Clinician
Clinician
clinician
```

<br>
<br>

Examples of using `grep -n`:

```
grep -i -n "Alcohol" Session2-PDF.txt
6:Identifying ED Patients with Alcohol Problems
9: Many patients in the emergency department (ED) have alcohol
13: further examine and refine alcohol-screening questionnaires in the
21: Alcohol problems defined
```

```
grep -i -n "Clinician" Session2-PDF.txt
26: endpoints we are measuring. Clinicians in the ED are interested in
140: Clinicians often use their general impression to help with
406: unavailable, screening makes little sense to clinicians. Realizing
```

All of these examples were done using the same `.txt` file to show the contrasting results using the same source. While the Lab Report Write-Up does not explicitly instruct us to explain what the command-line options do, I assume it is expected.

<br>

`grep -A n` (I used the default parameter `-A`) prints "...searched line and nlines after the result." This command is useful because if you are ever searching for a specific phrase in context, using `grep -A` (Or `grep -B n` and `grep -C n`) allows you to look at lines of a text file that surround the one matching phrase you are searching for. For example, if one was using `grep` on a large `.txt` file containing the medical histories of patients, it would be very useful to use something like `grep -A 150 "Jack Determan" history.txt`. This would allow someone to search for my name in the `.txt` file and output the lines following my name, which would presumably be a known amount of lines containing my medical history.
<br>
`grep -i` "Ignores, case for matching." I imagine this option being extremely useful when working with any data that is untidy (Which is almost all data). Searching for keywords among documents that contain uppercase and lowercase phrases implies using multiple `-grep` commands, one with an uppercase instance of the desired phrase and one with the lowercase instance. Being able to use `grep -i` bypasses this need, halving the time it takes to search a document for your desired phrase.
<br>
`grep -o` "Print only the matched parts of a matching line, with each such part on a separate output line." This command-line option is useful when all you care about is the exact phrase you're searching for. 
<br>
`grep -n`  "Display the matched lines and their line numbers." This is useful when you are going to plunge into the `.txt` file yourself after using `grep` to locate instances of your desired phrase. By knowing the location of the phrase in your file, you can easily find it and read the surrounding areas / extract the information that you need on your own.

All of these command-line options were found on [Geeks for Geeks](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

