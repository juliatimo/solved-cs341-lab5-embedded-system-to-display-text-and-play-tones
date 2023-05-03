Download Link: https://assignmentchef.com/product/solved-cs341-lab5-embedded-system-to-display-text-and-play-tones
<br>
In this lab, you will learn about interfacing I/O devices to the Arduino computer. In particular, you will program them to display text and time to a Liquid Crystal Display (LCD)  and play tones on the piezoelectric speaker. The starter code can be found on GitHub under Lab 5.

<h1>Some Background Info</h1>

You can display 2 lines (16 characters per line) of text using the LCD Display in the Arduino library. It has a parallel interface that allows the computer to manipulate in order to display the desired characters. In addition to showing alphanumeric characters, the Arduino can also control the display contrast, and turn on and off the LED backlight. You can find a good description of the functions of the LCD interface pins, diagrams on how to connecting them and programming snippets <a href="https://www.arduino.cc/en/Tutorial/LibraryExamples/HelloWorld">here</a><a href="https://www.arduino.cc/en/Tutorial/LibraryExamples/HelloWorld">.</a>

A piezoelectric speaker (buzzer) is made out of a certain crystal. It generates sounds when electricity is applied to it. These speakers are cheap and they are commonly used in alarm devices, computers and timers. They produce tone frequency ranging from 20 – 20,000 Hz. As a reference, human speech signals are around 3,000 – 4,000 Hz and music instruments (e.g. violins) can generate notes as high as 16,000 Hz (<a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">https://gomixing.com/sound</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">theory/music</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">equalizer</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">how</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">to</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">use</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">audio</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">equalizers</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">and</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">everything</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">else</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">about</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">equalization</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">in</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">–</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">music/</a><a href="https://gomixing.com/sound-theory/music-equalizer-how-to-use-audio-equalizers-and-everything-else-about-equalization-in-music/">)</a>. You can find a description on how to hook up the speaker and programming snippets <a href="https://www.ardumotive.com/how-to-use-a-buzzer-en.html">here</a><a href="https://www.ardumotive.com/how-to-use-a-buzzer-en.html">.</a>







<h1>Program the LCD display and Piezo Speaker</h1>

To begin the lab, connect the LCD display and piezoelectric speaker to Arduino computer using the provided bread board as shown in the diagram<em>. </em>Specifically, you will be connecting the following Arduino interface pins:

<strong><u>Arduino Digital pin</u>                                       <u>LCD or Speaker Function</u> </strong>

2,3,4,5                                             (D7,D6,D5,D4) control what character to display

<ul>

 <li>(E) enable writing to the registers</li>

 <li>(R/S) select writing to either the Data register or the</li>

</ul>

Control Register     8                                           control the speaker










Use the provided starter code to verify the correctness of your circuit connection. When the program is running, you should see the first 16 characters of the string “Welcome CS341 Students! ” displayed on line 1 and the time elapsed in seconds displayed at the middle of line 2. You should also hear an intermittent tone of 1500 Hz. The LCD’s display contrast pin (V<sub>0</sub>) is connected to the wiper of a 10K potentiometer (variable resistor). You can change the contrast of the display by moving the center dial of the potentiometer. The leftmost position setting results in the highest contrast.

For this lab, you are asked to write a program to show a ticker tape display of the string p[ ] using the LCD display:

char p[ ]= “Welcome CS341 Students! ”;

When the program is running, the string p[ ] will appear to scroll along the LCD display. To achieve this effect, your program has to:

<ul>

 <li>Display a different section of the string at a time in a circular fashion (Remember the tail program in CS240). Initially, you show:</li>

</ul>




“Welcome CS341 Students! ”  Then you show:

“elcome CS341 Students! W”.  Then you show:

“lcome CS341 Students! We”   and so on.

<ul>

 <li>Since the LCD can only display 16 (DISPLAY_LEN) characters at a time and the length of the string is 24, the best way is to save the appropriate 16 characters from the string p[] into a temporary buffer for display and then output it using:</li>

</ul>




char buffer[DISPLAY_LEN + 1];

load 16 bytes of p[] in a circular fashion into buffer[]

lcd.setCursor(0, LINE_1);

lcd.print(buffer);

You can write some code in the loop function if you want to experiment with that capability.  If you do, it would be a good idea to include one or more delay() calls in the loop function so that you have time to see or hear the results of each pass before the next pass is made.

As a team, write your lab report to explain what you did, how you did it, and what you learned about interfacing hardware to a microprocessor and its software (the “sketch”).  Turn in your report including a copy of your team’s final code at your next lab session.