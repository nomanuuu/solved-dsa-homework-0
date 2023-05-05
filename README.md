Download Link: https://assignmentchef.com/product/solved-dsa-homework-0
<br>
<h1>Problem Outline</h1>

<ul>

 <li>Problem 1 – Greatest Common Divisor of Big Integers (Programming) Foundations: array, loop</li>

 <li>Problem 2 – Nonogram Solver (Programming)</li>

</ul>

Foundations: string, recursion, two dimensional array, etc.

<ul>

 <li>Problem 3 – *(Human Compiler) (Non-programming) Foundations: pointer, etc.</li>

</ul>

<h1>Problem 1 – Greatest Common Divisor of Big Integers (Programming)</h1>

<h2>Problem Description</h2>

The greatest common divisor <em>gcd</em>(<em>a,b</em>) between two positive integers <em>a </em>and <em>b </em>is defined as the largest positive integer that divides both <em>a </em>and <em>b </em>without a remainder. Mathematically speaking, ∀<em>k </em>∈ N and <em>k &gt; gcd</em>(<em>a,b</em>), (<em>a </em≯≡ 0 mod <em>k</em>) or (<em>b </em≯≡ 0 mod <em>k</em>).

GCD is a very powerful tool in modern cryptography, and when the target integers to be calculated are small (less than 10<sup>8</sup>), GCD can be calculated in a few seconds with a naïve method. However, the numbers in modern cryptography requires at least 512 digits to prevent attackers from using a brute-force method to derive the secret key. This required number is too large for the naïve methods to calculate GCD in a reasonable time and the numbers exceeds the limit of even long long in the C language. In this problem, we will guide you to calculate the GCD of two big integers efficiently.

<h2>Implementation</h2>

First, to deal with the big integers, we need a “data structure”, such as an integer array in C to represent larger values. We will call it BigInt. For instance, you can use an integer array where each element represents one (decimal) digit, like representing 17202 by the following code snippet.

int digits[10]={2,0,2,7,1};

It is not required to use the representation above, though. You can use any representation that facilitates your implementation of the following algorithm. It is an opportunity to think about how “well-designed data structures” can lead to “efficient algorithms.”

Next, please implement the following algorithm, called Binary Algorithm, using the C language. Then you will miraculously get the correct GCD. Note that you need to implement four components: a comparator between two BigInts, subtraction between two BigInts, division by 2 for one BigInt, and multiplication by 2<em><sup>k </sup></em>for one BigInt with some <em>k</em>. It is strongly recommended to implement the four components as separate functions, and test their correctness separately, before combining them with the Binary Algorithm.

<strong>Algorithm 1: </strong>Binary Algorithm for Greatest Common Divisor

<strong>Input: </strong>Two positive integers <em>a </em>and <em>b</em>.

<strong>Output: </strong>A positive integer <em>ans </em>representing greatest common divisor of <em>a </em>and <em>b</em>.

<strong>Input</strong>

One line containing two integers, <em>a </em>and <em>b</em>, where 0 <em>&lt; a,b &lt; </em>10<sup>256</sup>.

<strong>Output</strong>

Please output an integer representing <em>gcd</em>(<em>a,b</em>).

<strong>Sample Input 1</strong>

20210208 80201202

<strong>Sample Output 1</strong>

6

<strong>Sample Input 2</strong>

987654321987654321987654321 123456789123456789123456789

<strong>Sample Output 2</strong>

9000000009000000009

<h2>Correctness (Optional)</h2>

You are encouraged to think about how we can prove that the Binary Algorithm is correct. The proof can be done if you can prove the correctness of the following theorems <em>from the definition of </em><em>gcd</em>. We will teach you more about proving the correctness of algorithms in the semester, but feel free to make attempts by yourself now.

<ol>

 <li>Assume that <em>k </em>is a positive integer and <em>k </em>| <em>a </em>but <em>k </em≯ | <em>b</em>, then <em>gcd</em>(<em>a</em>/<em>k,b</em>) = <em>gcd</em>(<em>a,b</em>)</li>

 <li>Assume that <em>k </em>is a positive common divisor of <em>a </em>and <em>b</em>, then <em>k</em><em>gcd</em>(<em>a</em>/<em>k,b</em>/<em>k</em>) = <em>gcd</em>(<em>a,b</em>)</li>

 <li>Assume that <em>a &gt; b</em>, then <em>gcd</em>(<em>a,b</em>) = <em>gcd</em>(<em>a </em>− <em>b,b</em>)</li>

</ol>

<h1>Problem 2 – Nonogram Solver (Programming)</h1>

<h2>Problem Description</h2>

Nonogram, also known as Paint by Numbers, Picross, Griddlers, Pic-a-Pix, and various other names, is a logic puzzle in which cells in a grid must be painted according to the given row clues and column clues. Players are requested to paint each grid cell into either “white” or “black”, such that the segments consisting of consecutive black cells in each row or column matches the corresponding row clue and column clue. The clues or numbers are a form of discrete tomography that measures the numbers of consecutive painted cells in any given row or column. For example, a clue of “4 8 3” would mean that there are sets of four, eight, and three filled (black) cells, in that order, with at least one blank (white) cell between successive sets. Moreover, solving nonogram puzzles is proved to be a <a href="https://en.wikipedia.org/wiki/NP_(complexity)">NP-complete problem</a>, which roughly means that no <em>known </em>algorithm can solve the puzzles efficiently in general. See Figure 1 for an example.

If you are interested in this puzzle game, you can play the simple version (<a href="https://puzzle-nonograms.com/">link</a>) or download similar games to your smartphone.

Figure 1: A nonogram example: clues and solution.

Now given the height and width of the nonogram puzzle, denoted as <em>N </em>and <em>M</em>, and clues of each row and column, please put together a program to solve this puzzle and draw it.

<h2>Input</h2>

The first line of the input contains two integers <em>N </em>and <em>M</em>, representing the number of rows and the columns of the nonogram puzzle.

Next <em>N </em>+ <em>M </em>lines are the clues. The first <em>N </em>lines represent the clues of the <em>N </em>rows while the rest <em>M </em>lines represent the clues of the <em>M </em>columns. Each clue line starts with an integer <em>n</em>, representing the number of segments of consecutive black cells the row or column contains. The next <em>n </em>integers represent the numbers of consecutive black cells in the segments. For row clues, the numbers are marked from left to right, and, for column clues, the numbers are marked from top to bottom.

The puzzle size <em>N </em>×<em>M </em>is less than 25, meaning that a brute-force algorithm with little optimization should be able to solve the puzzle within reasonable time. However, if you are interested in better solutions, try out other approaches (e.g., develop new algorithms or improve pruning mechanisms) and see if you can solve larger puzzles.

<h2>Output</h2>

Output the puzzle in <em>N </em>lines; each of them should contain <em>M </em>cells. Print ‘o’ if the corresponding cell is black; otherwise print ‘_’.

<strong>Sample Input 1                                                          Sample Input 2</strong>

5 5

4 4                                      1 4

2 1 1                                    1 2

2 1 1                                    1 3

2 1 1                                    1 2

<ul>

 <li>4 1 4</li>

 <li>1 2 2 1 1</li>

</ul>

2 1 1                                    2 3 1

2 1 2                                    3 1 1 1

2 1 1                                    2 1 3

2 1 1

<strong>Sample Output 1                                                       Sample Output 2</strong>

_oooo

o_o_                                     oo___

_o_o                                     _ooo_

o_o_                                     ___oo

oooo                                     oooo_

Figure 2: Puzzle of sample 1                               Figure 3: Puzzle of sample 2

<h2>Hint</h2>

If you don’t know where to start with, you can follow the template below. Note that it is written in the form of <em>pseudo code</em>, and you have to covert it to real C code, where implementation details need to be carefully

<h1>Reference</h1>

<ol>

 <li>Rules about Nonogram. (https://en.wikipedia.org/wiki/Nonogram)</li>

 <li>Example puzzle in problem 2. (https://www.chessprogramming.org/Nonogram)</li>

</ol>

<h1>Problem 3 – *(Human Compiler) (Hand-written)</h1>

<h2>Problem Description</h2>

There are four questions related to <em>pointers </em>in <em>C</em>. In each of the following questions, you will be given an incomplete code segment and its purpose. Without the help of compilers, please fill in blank segments and achieve the purpose. After completing the code segments, you are encouraged to run the codes and verify the correctness on your own.

Compared with <em>Python</em>, it is easy to get a <em>Runtime Error </em>(RE) when dealing with <em>pointers </em>in <em>C</em>. For example, the following code segment may lead to a <em>Segmentation Fault </em>(depends on the compiler).

<strong>int </strong>*ptr = NULL; *ptr = 42;

This may look stupid, but it somehow occurs when your code grows to have more than 100 lines. Therefore, you need to be very cautious when you allocate, access and free pointers. The problems below are good practices for you; think twice before going to the next one.

<strong>Problem 3-(a) </strong>Swaps two arrays using pointers.

<table width="651">

 <tbody>

  <tr>

   <td width="651"><strong>int </strong>fake_a[] = {1, 3}; <strong>int </strong>fake_b[] = {2, 4}; <strong>int </strong>*real_a = fake_a; <strong>int </strong>*real_b = fake_b;<strong>for </strong>(<strong>int </strong>i=0; i&lt;2; i++) printf(“%d “, *(real_a + i));<strong>for </strong>(<strong>int </strong>i=0; i&lt;2; i++) printf(“%d “, *(real_b + i));<strong>int </strong>*tmp = real_a; ___(1)___ = ___(2)___; ___(3)___ = ___(4)___;<strong>for </strong>(<strong>int </strong>i=0; i&lt;2; i++) printf(“%d “, *(real_a + i));<strong>for </strong>(<strong>int </strong>i=0; i&lt;2; i++) printf(“%d “, *(real_b + i));</td>

  </tr>

 </tbody>

</table>

The output should be “1 3 2 4 2 4 1 3”.

<strong>Problem 3-(b) </strong>An array supporting negative indices.

<table width="651">

 <tbody>

  <tr>

   <td width="651"><strong>#include </strong>&lt;stdio.h&gt;<strong>#define </strong>MINN -50 <em>// inclusive </em><strong>#define </strong>MAXN 50 <em>// inclusive</em><strong>int </strong>main(){ <strong>int </strong>storage[MAXN – MINN + 1]={0}; <strong>int </strong>*ary = ___(1)___;<strong>for </strong>(<strong>int </strong>i=MINN; i&lt;=MAXN; i++) ary[i] = i;<strong>for </strong>(<strong>int </strong>i=MINN; i&lt;=MAXN; i++) printf(“%d “, ary[i]);<strong>return </strong>0;}</td>

  </tr>

 </tbody>

</table>

The output should be “-50 -49 … -1 0 1 … 49 50 “.

<strong>Problem 3-(c) </strong>Traverses data nodes in a <em>linked list</em>. Please familiarize yourself with linked list in advance. Related topics are covered in Prof. Liu’s videos.

<table width="651">

 <tbody>

  <tr>

   <td width="651"><strong>#include </strong>&lt;stdio.h&gt;<strong>#include </strong>&lt;stdlib.h&gt; <em>// malloc / free </em><strong>#include </strong>&lt;memory.h&gt; <em>// memset</em><em>// Use typedef to define “struct node” as “node”. </em><strong>typedef struct </strong>node{ <strong>int </strong>data; <strong>struct </strong>node *nxt;} node;node *alloc(<strong>int </strong>data, node *nxt){ node *tmp = (node *)malloc(<strong>sizeof</strong>(node)); tmp-&gt;data = data; tmp-&gt;nxt = nxt;<strong>return </strong>tmp;}<strong>void </strong>destory(node *head){ <strong>if </strong>(___(1)___){ destory(head-&gt;nxt);<em>// clean sensitive data. </em>memset(head, 0, <strong>sizeof</strong>(head));free(head);}}<strong>int </strong>main(){<em>// create nodes [0, 1, 2, 4] </em>node *head = alloc(0, alloc(1, alloc(2, alloc(4, NULL)))); node *tmp = head;<em>// print the nodes subsequently </em><strong>while </strong>(tmp != NULL){ printf(“%d -&gt; “, ___(2)___); <em>// print the data in the node </em>tmp = ___(3)___;}printf(“NULL”);<em>// free the nodes subsequently to avoid memory leak </em>destory(head);<strong>return </strong>0;}</td>

  </tr>

 </tbody>

</table>

The output should be “0 -&gt; 1 -&gt; 2 -&gt; 4 -&gt; NULL”.

<strong>Problem 3-(d) </strong>Traverses data nodes in a <em>binary tree</em>. Please familiarize yourself with binary trees in advance. Related topics are covered in Prof. Liu’s videos.

<table width="651">

 <tbody>

  <tr>

   <td width="651"><strong>#include </strong>&lt;stdio.h&gt;<strong>#include </strong>&lt;stdlib.h&gt; <em>// malloc / free </em><strong>#include </strong>&lt;memory.h&gt; <em>// memset</em><em>// Use typedef to substitute “struct node” with “node”. </em><strong>typedef struct </strong>node { <strong>int </strong>data;<strong>struct </strong>node *left, *right;} node;<em>// creates a node filled with predefined values </em>node *alloc(<strong>int </strong>data, node *left, node *right){ node *tmp = (node*)malloc(<strong>sizeof</strong>(node)); tmp-&gt;data = data; tmp-&gt;left = left; tmp-&gt;right = right; <strong>return </strong>tmp;}<em>// traverses the nodes recursively </em><strong>void </strong>traverse(node *root){ <strong>if </strong>(___(1)___){ printf(“%d “, root-&gt;data); traverse(___(2)___); traverse(___(3)___);}}<em>// frees the nodes recursively </em><strong>void </strong>destory(node *root){ <strong>if </strong>(___(1)___){<em>// recursively destory nodes.</em>destory(___(2)___); destory(___(3)___);<em>// clean sensitive data.</em>memset(root, 0, <strong>sizeof</strong>(root));free(___(4)___);}}<strong>int </strong>main(){<em>// creates a hierarchical data structure</em>node *root = alloc(0, alloc(3, alloc(7, NULL, NULL), alloc(4, NULL, NULL)), alloc(2, alloc(1, NULL, NULL),alloc(9, NULL, NULL)));</td>

  </tr>

  <tr>

   <td width="651"><em>// traverses the nodes one by one </em>traverse(root);<em>// frees the nodes to avoid memory leak </em>destory(root);<strong>return </strong>0;}</td>

  </tr>

 </tbody>

</table>

The output should be “0 3 7 4 2 1 9”.