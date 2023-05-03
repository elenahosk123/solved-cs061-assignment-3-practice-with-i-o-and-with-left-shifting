Download Link: https://assignmentchef.com/product/solved-cs061-assignment-3-practice-with-i-o-and-with-left-shifting
<br>
ObjectiveThe purpose of this assignment is to give you more practice with I/O, and with left-shifting, aka multiplying by 2, and useful 2’s complement logic.

<strong>High Level Description </strong>

Store a number to the <strong>memory address specified in your assn 3 template</strong>​      . In your program, load​      that number in a register, and display it to the console as 16-bit two’s complement binary (i.e. display the binary value stored in the register, as a sequence of 16 ascii ‘1’ and ‘0’ characters). <strong>Note</strong>​: Valid numbers are [#-32768, #32767] (decimal) or [x0000, xFFFF] (hex)

<strong>Your Tasks </strong>

You do not yet know how to take a multi-digit decimal number from user input and convert it to binary, so for this assignment you are going to let the assembler to do that part for you:  you will use the .FILL pseudo-op to take a literal (decimal or hex, as you wish) and translate it into 16-bit two’s complement binary, which will be stored in the indicated memory location; and then you will Load that value from memory into a register.

You ​<strong>MUST</strong>​ use the provided assn3.asm template to set this up: it ensures that the number to be converted is always stored in the same location (the ​<strong>memory address specified in your template</strong>​) so we can test your work; make sure you fully understand the code fragment we provide.

At this point, your value will be stored in, say, R1: it is now your job to identify the 1’s and 0’s from the number and print them out to the console one by one, ​<u>from left</u> ​ <em>(</em>​ <em>the leading bit, aka the leftmost bit, aka bit 15, aka the most significant bit)</em>​ <u>​to right</u>​ ​<em>(the trailing bit, aka the rightmost bit, aka bit 0, aka the least significant bit)</em>​.

Important things to consider:

<ul>

 <li>Recall the difference between a positive number and a negative number in 2’s complement binary: if the most significant bit (MSB) is 0, the number is considered positive (or perhaps zero); if it is 1, the number is negative.</li>

 <li>The ​<strong>BR</strong>​anch instruction has parameters (n, z, p) which tell it to check whether a value is <strong>n</strong>​egative, ​<strong>z</strong>​ero, or ​<strong>p</strong>​ositive (or any combination thereof).</li>

</ul>

<strong><em>Hint</em></strong>​<em>: what can you say about the msb of the LMR if the n branch is taken?</em>

<em>Review the workings of the NZP condition codes and the BR instruction </em><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit#bookmark=id.xve3xutg9b3g">​</a><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit#bookmark=id.xve3xutg9b3g"><em>here</em></a><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit#bookmark=id.xve3xutg9b3g">​</a><em> . </em>

<ul>

 <li>Once you are done inspecting the MSB and printing the corresponding ascii ‘0’ or ‘1’, how would you <em>shift</em>​ ​ the next bit into its place so you could perform the next iteration?</li>

</ul>

<strong><em>Hint</em></strong>​<em>: the answer is in the objectives!</em>

<strong><em>Pseudocode:</em></strong>

for(i = 15 downto 0):           if (msb is a 1):                print a 1           else:                print a 0           shift left

<strong>Expected/ Sample output </strong>

In this assignment, your output will simply be the contents of R1, printed out as 16 ascii 1’s and 0’s, grouped into packets of 4, separated by spaces ​<em>(as always, newline terminated, but with </em><u>​<em>NO</em></u><em> terminating space!) </em>

<em> </em>

So if the hard coded value was xABCD, your output will be:

1010 1011 1100 1101

(The value stored to memory with .FILL was xABCD)




<strong>Note: </strong>

<ol>

 <li><em>There are </em>​<strong><em>spaces</em></strong>​<em> after the first three “packets” of 4 bits (but </em>​<em><u>no</u></em>​<em> space character at end!) </em></li>

 <li><em>There is a </em>​<strong><em>newline </em></strong>​<em>after the output – again, there is </em>​<strong><em>NO</em></strong>​<em> space before the </em>​<strong><em>newline </em></strong></li>

 <li>You ​<strong>must </strong>​use the memory address specified in your template to hold the value to be output</li>

</ol>




Your code will obviously be tested with a range of different values:  Make sure you test your code likewise!<strong>        </strong>

<strong>Uh</strong><u>…</u><strong>help? </strong>

<ul>

 <li><strong>MSB</strong></li>

</ul>

○ Stands for Most Significant Bit

■ aka “left most bit” or “leading bit” or bit 15 ○ When MSB is 0:

■ Means that the number is <strong>Not Negative</strong>​         (Positive or Zero)​      ○ When MSB is 1:

■ Means that the number is <strong>Negative</strong>​

<strong>○ Further Reading </strong>

■ <a href="https://en.wikipedia.org/wiki/Most_significant_bit">https://en.wikipedia.org/wiki/Most_significant_bit</a>




<ul>

 <li><strong>Left Shifting </strong></li>

</ul>

Left shifting means that you shift all the bits to the left by 1: so the MSB is lost, and is replaced by the bit on its right. A 0 is “shifted in” on the right to replace the previous LSB.




4-bit Example:

0101 ; #5

When Left Shifted, with 0 shifted in to LSB:

1010 &lt;—- 0101

1010 ; #10

What happened when we left shifted? How did the number change?

When left shifting, the number gets multiplied by 2? Why 2?

Well, what happens when you shift a <em><u>decimal</u></em>​          <u>​</u> number one place to the left? Why? <em>(Practical differences between decimal and binary numbers are that we don’t usually limit decimal numbers to a specific number of places, nor do we usually pad them with leading zeros). </em>




<strong>Further Reading </strong>

<ul>

 <li><a href="https://en.wikipedia.org/wiki/Logical_shift"><strong>https://en.wikipedia.org/wiki/Logical_shift</strong></a></li>

</ul>


