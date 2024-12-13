---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: Project
---

# **Project**
## **Eoin Fitzpatrick**
## **Group B** 


I am creating different facial expressions, including shocked, smiley, sad, and shocked faces. I think this will be visually appealing, as it's nice to watch the faces change.



## **Template VGA Design**
### **Project Set-Up**

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSum.png">

A VGA interface works by sending signals to a display to control the color and position of each pixel on the screen. It uses horizontal and vertical synchronization signals to draw the image line by line, starting from the top-left corner and finishing at the bottom-right. This process repeats quickly to create a stable image.
For the template code that I was given it was colour stripes s it was different colours across the screen below is when I sumulated it. Some interesting things that I have seen is 
how the colours go from high to low which is very interesting.

The way this code works is by using rows and columns so in this example one full column is black and another is blue and yellow. This gave me the idea to make flags so I
made the french flag just so I could understand the code better. Which then helped me come up with an idea for my actual project.


This is a picture of my test bench as I simulated the VGA Colour Stripes.

<img src= https://github.com/EoinFitz03/SOCproject/blob/main/image.png>
This is me running the simulation. 

### **Synthesis**
 ![thumbnail_image](https://github.com/user-attachments/assets/11eb8677-9ef0-455a-8794-ebe00249ac00)
Synthesis in Vivado converts your HDL design into a hardware implementation that the FPGA can use. It translates your code into a netlist, which represents the design as logic gates, flip-flops, and connections, and optimizes it for speed, size, or power. This step prepares your design for placement and routing on the FPGA hardware.

So For my synthesis for my Colour stripes sythesis it is not as visually appealing as the faces but as you can see from the picture above it is only stripes going through a page so my sythesis looks better for my faces because there is more going on in the code. I show it better in my synthesis fir my faces. It makes more sense and it more appealing what is going on.  


# **My VGA Design Edit**

## **Faces**
My project focuses on creating faces displayed on a VGA screen that change using a state machine. It starts with a neutral face a straight line for the mouth transitions to a sad face, then a smiley face, and finally a shocked face. I was inspired by YouTube videos showing creative VGA designs. One video featured a face, which sparked the idea for this project, and I found a smiley face template code on Stack Overflow to help me get started. 

I then got the circles formula from that code. This formula checks if each pixel on the screen lies inside or on the edge of a circle. From this formula then I could do the eyes and mouth by purely using circles. 
![image](https://github.com/user-attachments/assets/98903bd5-8f29-4296-85dc-861f125fa60a)

### **Code Adaptation**

![image](https://github.com/user-attachments/assets/5e3ca55e-ed3f-4a95-a898-9d677d3ee5a3)

This is my state machine the way it works is by cycles through four states in a loop. Each state represents a different face normal, shocked, smiley, and sad. When the state changes, it updates to the next face in the sequence, going back to the first face after the last one. The case statement defines the order of transitions. As I go down the code the you will see the formula above coming up alot. For this shocked face I use 3 circles. The hard part of this was trying to get the vircles in the right places but I figured that for the mouth especially to have it around the 300 mark which is close to the middle for the rows and columns. 
![image](https://github.com/user-attachments/assets/626a29c4-71a6-47ed-9089-186361ad8272)


Then simply for the for the sad face and the happy face it was a sake of cutting the shock mouth in half so for the sad face what I did was using this code.
This code is checking if a pixel is inside a circular area to create the bottom half of a shocked mouth expression. It uses the formula for a circle to determine if the pixel is defined by its row and column lies within a circle with a radius of 40 and centered at 300, 320. If the pixel is in the upper half of the circle where row <= 300.


![image](https://github.com/user-attachments/assets/4385068a-e967-49f5-85e8-f39287ffc40c)


To move it to make it look more like a sad face I moved the rows down. So it made it a bit more realistic being a sad face.



This is my smiley face and 
This code is creating the bottom half of a shocked mouth. It checks if a pixel is inside a circular area with a radius of 40, centered at 300, 320. If the pixel is in the lower half of the circle where row >= 300, it sets the color to black.

 ![image](https://github.com/user-attachments/assets/ff0183cb-c34a-4ba9-bbb6-0f654fcd215e)



As you can see in this code that the arcs are just going opposite ways. and instead of going - 320 its goign == 320 so that the arc goes the other way. 



### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.

![image](https://github.com/user-attachments/assets/bd087f62-75a4-4963-a149-9d51d8d3c9f1)


Simulation in Vivado tests your design by running it in a virtual environment before programming the FPGA. It checks how your code behaves with different inputs and ensures the logic works as expected, helping you find and fix errors early. It also gives out a graph like this that shows you when certain parts are high and low like the clock and the colours that are in the VGA. 

This is an image of what is hppening in a schematic and what is being used to produce the smiley faces. 


![image](https://github.com/user-attachments/assets/87b7cbea-eb12-442d-9ee4-7249985be41d)

You can see alot of things going on here but as you move in it makes more sense. 
![image](https://github.com/user-attachments/assets/95231cf8-cb13-4441-b642-8c636c93a107)

Here you can see a muxer and a counter clock working. 

![image](https://github.com/user-attachments/assets/11bf292d-6d95-4d18-ae12-977f088d5ccb)

Here you can see an Adder and a and gate working to create the image. This shows the amount of background work that has to go in for hardware for not a large amount of code which I find very Interesting 



### **Synthesis**
Synthesis in Vivado takes your design, written in a language like Verilog or VHDL, and turns it into a list of logic gates and components that an FPGA can use. It checks your code, makes it more efficient, and prepares it for the next steps in programming the FPGA. 

![image](https://github.com/user-attachments/assets/e117b58f-d1e0-4747-b91a-664e450cb6c5)

This image shows how the design is mapped onto the FPGA after implementation in Vivado. The colored blocks represent different parts of the FPGA, like logic units or memory, and the lines show how they are connected. This view helps you see if the design fits well on the FPGA and how resources are being used. This is interesting because When I looked at the schematic for this it was very large and confusing with the amount lines goign through things this picture makes it alot easier to inderstand what is going on in the synthesis. 

### **Demonstration**
These are the faces. So what happens is starts on the next one and depending on the clock cycle it will move to the next state. 

![IMG_1694](https://github.com/user-attachments/assets/ddf32adc-10ac-4466-bde1-a4094a56494c)
Normal face 
![IMG_1695](https://github.com/user-attachments/assets/0b264119-fce7-482a-9143-09ebbb4fe7c9)
Happy face
![IMG_1696](https://github.com/user-attachments/assets/ecbfd63f-d525-495c-82f9-59bb82c6fd5a)
Shocked face or the ohhhh face 
![IMG_1693](https://github.com/user-attachments/assets/35c30334-c6de-4dac-b5f3-75426c4446c2)
Sad face 

### **Conclusion **
This FPGA VGA Driver project has been a great learning experience in using Verilog to create visual displays. The project that I created focused on creating different facial expressions normal, sad, smiley, and shocked that change on the screen using a state machine. By using simple circle-based formulas, I was able to create faces that transition from one expression to another.

Throughout the project, I learned a lot about how to test and use designs in Vivado, and how to translate the design into hardware on the FPGA. Working with components like counters, multiplexers, and logic gates helped me understand how everything came together to create a working project.

One thing that I founf most difficult in the project was trying to get teh sad face correct. Eventually I got there but this made me learn more about the code and it works when I ran into to problems like this so it was actually beneficial. 

Overall, this project was a valuable experience that thought me a lot about FPGA design, and Hopefully the skills that I learned doing this project will help me in the furure.
