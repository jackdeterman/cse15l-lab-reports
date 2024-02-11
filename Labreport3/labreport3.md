_Part 1_

The bug I am choosing from Week 4's lab is the bug present in the `append` method in the `LinkedList` class. 

<br>
<br>
<br>

Here is a failure-inducing input for the buggy method:

<br>

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
<br>

The associated code that causes this to fail is the following:

<br>

```
while(n.next != null) {
            n = n.next;
            n.next = new Node(value, null);
        }
```

<br>
<br>
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

<br>
<br>

```
Node n = this.root;
        if(n.next == null) {
            n.next = new Node(value, null);
            return;
        }
```




