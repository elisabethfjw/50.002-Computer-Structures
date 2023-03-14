<h1> ALU_16_BIT </h1>
<h2> Team 25 </h2> 
<h3> Members </h3> 
<ul>
  <li>Florence Elizabeth Nguyen Shi Ky</li>
  <li>Fung Jing Wen Elisabeth</li>
  <li>Peh Yu Xiang</li>
  <li>Andrea Cheah Shiue Er</li>
  <li>Zachary Low Yang Kai</li>
  <li>Tan Zi Hui</li>
</ul>

<table>
  <tr>
    <th>ALUFN[5:0]</th>
    <th>Operation</th>
    <th>Module</th>
  </tr>
  <tr>
    <td>00 00X0 <sup><a href="#section1">[1]</a> </td></sup>
    <td>ADD</td>
    <td>adder16</td>
  </tr>
  <tr>
    <td>00 00X1 <sup><a href="#section1">[1]</a> </td></sup>
    <td>SUBTRACT</td>
    <td>adder16</td>
  </tr>
  <tr>
    <td>00 0100</td>
    <td>MULTIPLY</td>
    <td>multiplier16</td>
  </tr>
  <tr>
    <td>00 0101</td>
    <td>DIVISION</td>
    <td>multiplier16</td>
  </tr>
  <tr>
    <td>01 0001</td>
    <td>NOR</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>01 0110</td>
    <td>XOR</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>01 0111</td>
    <td>NAND</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>01 1000</td>
    <td>AND</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>01 1001</td>
    <td>XNOR</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>01 1110</td>
    <td>OR</td>
    <td>boolean16</td>
  </tr>
  <tr>
    <td>10 0000</td>
    <td>SHIFT LEFT</td>
    <td>shifter16</td>
  </tr>
  <tr>
    <td>10 0001</td>
    <td>SHIFT RIGHT</td>
    <td>shifter16</td>
  </tr>
  <tr>
    <td>10 0011</td>
    <td>SHIFT RIGHT ARITHMETIC</td>
    <td>shifter16</td>
  </tr>
  <tr>
    <td>11 001X <sup><a href="#section1">[1]</a> </td></sup>
    <td>CMPEQ</td>
    <td>comparator16</td>
  </tr>
  <tr>
    <td>11 010X <sup><a href="#section1">[1]</a> </td></sup>
    <td>CMPLT</td>
    <td>comparator16</td>
  </tr>
  <tr>
    <td>11 011X <sup><a href="#section1">[1]</a> </td></sup>
    <td>CMPLE</td>
    <td>comparator16</td>
  </tr>
</table>

<p id="section1">[1] :point_right: X represents an insignificant bit whose value does not affect the operation it carries out.</p>

<h3> Testing </h3> 
<ul>
  <li>To test the ALU, we use two modes: manual and automatic.</li>
  <li><code>io_button[2]</code>, the down button, switches between the automatic and manual testing modes.</li>
  <li><code>io_button[0]</code> is used to force an error during automatic/manual mode, resulting in an error-catching state for intentional error handling.</li>
</ul>

<h4>Manual testing</h4> 
<p>We used the <code>manual_tester.luc</code> module to manually test the ALU.<br>
<h5>Procedure</h5> 
<ol>
  <li>Press <code>io_dip[2][5:0]</code> to select OPCODE.</li>
  <li>Press <code>{io_dip[1], io_dip[0]}</code> to select X values.</li>
  <ul>
    <li><code>{io_dip[1], io_dip[0]}</code> concatenates 8 bits of <code>io_dip[1]</code> and <code>io_dip[0]</code> into a 16-bit vector.</li>
  </ul>
  <li>Press <code>io_button[1]</code> to confirm selected X input values.</li>
  <li>Repeat steps 2-3 for the Y input values.</li>
  <li>The values of <code>io_dip[2][7:6]</code> display the current state: 
    <ul>
      <li> X input: 10</li>
      <li> Y input: 01</li> 
      <li> OUTPUT: 11</li>
    </ul>
  <li>At OUTPUT state, i.e. when 7-segments display an "O", <code>{io_led[1], io_led[0]}</code> displays the resulting output of ALU.</li> 
  </ol>
  
<h4> Automatic testing </h4> 
<p>We used <code>auto_tester.luc</code> module to carry out automatic testing of ALU with its predefined test cases.</br>
<h5>Procedure</h5>
<p>The Finite State Machine continuously cycles through the predefined test cases in the <code>auto_tester.luc</code> module. During this:</br>
  <ol>
    <li>The 7-segments display shows "X", INPUT_X, "Y", INPUT_Y, "O" and EXPECTED_OUTPUT in this sequence.</li>
    <li><code>io_led[2][5:0]</code> displays the current OPCODE instruction that is tested.</li>
    <li>The 7-segments display shows "E" when an error is encountered, at the end of that test case. If there are no errors, the 7-segments display shows "d".</li>
  </ol>
  
  
