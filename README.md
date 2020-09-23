<div align="center">

## DMA in VB


</div>

### Description

DMA, create DMA emulation In vb.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Qages](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/qages.md)
**Level**          |Intermediate
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[VB function enhancement](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/vb-function-enhancement__1-25.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/qages-dma-in-vb__1-30802/archive/master.zip)





### Source Code

<html>DMA. Dynamic Memory Allocation.
vb is non-dma, this means that the memory address for a varable will be the same when the user reopens your program (will change if you add lots of new code).<br> this is bad because h4x0rs can steal or modify your program.<br> to make a emulation of DMA in vb, just redim a Array varable by random numbers and use whats in the middle. its simple.<br>
ill give a example below <br>
<br><p>
25682 ' this is a random number, really doesnt have any importance,<br>
redim stack((25682 - 6) To (25682 + 8)) ' the RAMDOM numbers 6,8 are the impornant<br><p>
[memory address] [place in our array]<br>
00000000     1 (-6)<br>
00000002     2 (-5)<br>
00000004     3 (-4)<br>
00000008     4 (-3)<br>
0000000A     5 (-2)<br>
0000000C     6 (-1)<br>
0000000E     7 (+0) '- Our middle numbers, this is what we want to use<br>
00000010     8 (+1)<br>
00000012     9 (+2)<br>
00000014     10 (+3)<br>
00000018     11 (+4)<br>
0000001A     12 (+5)<br>
0000001C     13 (+6)<br>
0000001E     14 (+7)<br>
00000020     15 (+8)<br>
<br><br>
ok the user closed the programan reloads it now creats new random numbers.<br>
<br><br>
ReDim stack((55431 - 2) To (55431 + 10)) ' the RANDOM numbers 2,10 are the impornant<br><p>
[memory address][place in our array]<br>
00000000     1 (-2)<br>
00000002     2 (-1)<br>
00000004     3 (+0) '- Our middle numbers, this is what we want to use<br>
00000008     4 (+1)<br>
0000000A     5 (+2)<br>
0000000C     6 (+3)<br>
0000000E     7 (+4) <br>
00000010     8 (+5)<br>
00000012     9 (+6)<br>
00000014     10 (+7)<br>
00000018     11 (+8)<br>
0000001A     12 (+9)<br>
0000001C     13 (+10)<br><br>
ok the first time the user opend the program the memory address for the middle (+0) is 0000000E, the next time its 00000004, <br>there its diffrent memory address! DMA<br>
Heres the Complete code to use:<br><p>
<br>
<FONT COLOR="#00008000">'globals</font><br>
<FONT COLOR="#0000ff">dim</font> stack() <FONT COLOR="#0000ff">as single</font> <FONT COLOR="#00008000">' we need tomake this a array! important</font><br>
<FONT COLOR="#0000ff">dim</font> STACKNUM <FONT COLOR="#0000ff">as long</font><br>
<br>
<FONT COLOR="#00008000">' thecode</font><br>
<FONT COLOR="#0000ff">dim</font> STACKNUMfrom <FONT COLOR="#0000ff">as byte</font><br>
<FONT COLOR="#0000ff">dim</font> STACKNUMto <FONT COLOR="#0000ff">as byte</font><br>
STartR:<br>
Randomize<br>
STACKNUM = Int(((999999) * Rnd) + 3000) <FONT COLOR="#00008000">' + 3000 - TO make sure were not 0 or some low number</font><br>
STACKNUMfrom = Int(((99) * Rnd)) <FONT COLOR="#00008000">' increase 99 for more randomness, decrese for less memory useage</font><br>
STACKNUMto = Int(((99) * Rnd)) <FONT COLOR="#00008000">' increase 99 for more randomness, decrese for less memory useage</font><br>
<br>
<FONT COLOR="#0000ff">ReDim</font> stack((STACKNUM - STACKNUMfrom) <FONT COLOR="#0000ff">To</font> (STACKNUM + STACKNUMto)) <FONT COLOR="#0000ff">As Single</font><br>
<br>
<FONT COLOR="#00008000">'you canuse more that just the middle number(STACKNUM), to use more use STACKNUM + whatever and STACKNUM - Whatever,<br> and use the code below tomake sure you have enuf spacein the array</font><br>
<br>
<FONT COLOR="#0000ff">If</font> STACKNUMto < 2 <FONT COLOR="#0000ff">Then</font> <FONT COLOR="#00008000">' STACKNUMto this is for our + STACKNUM, the number 2 is howmuch we want to use. can be used for<br> - STACKNUM too.</font><br>
<FONT COLOR="#0000ff">GoTo</font> STartR<br>
<FONT COLOR="#0000ff">End If</font><br>
<br>
<br>
<b>to use this just use:</b>
stack(STACKNUM) <b> or </b> <br>
stack(STACKNUM + 1)
<br><br><br><br>
</html>

