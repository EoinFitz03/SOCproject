---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

So what I am doing is a making faces. The faces that I am goign to use are Shocked, Smiley , sad and shocked face. I thought this would be good because 
it is nice to look at all the faces changing. 



## **Template VGA Design**
### **Project Set-Up**
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.


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
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
In Vivado, synthesis translates your high-level HDL code into a low-level netlist of logic gates and connections. Implementation takes the netlist and maps it to the physical resources of the FPGA, optimizing placement and routing to meet timing and area requirements. 

# **My VGA Design Edit**

## **Faces**
For my actual projct I decided to do faces. The way it works is starts of with a normal face so just straigt line for the mouth. 
Then using the state machine it switches to a sad face then to a smiley face and finally to a shocked face. What gave me inspiration for this project was 
I looked up on youtube cool designs for VGA. A face came up which gave me the idea of doing faces. I then googles more and got a template smiley face code of stackoverflow.

I then got the circles formula from that code. This formula checks if each pixel on the screen lies inside or on the edge of a circle. From this formula then I could do the eyes and mouth by purely using circles. 
![image](https://github.com/user-attachments/assets/98903bd5-8f29-4296-85dc-861f125fa60a)

### **Code Adaptation**

![image](https://github.com/user-attachments/assets/5e3ca55e-ed3f-4a95-a898-9d677d3ee5a3)

This is my state machine the way it works is by cycles through four states in a loop. Each state represents a different face normal, shocked, smiley, and sad. When the state changes, it updates to the next face in the sequence, going back to the first face after the last one. The case statement defines the order of transitions. As I go down the code the you will see the formula above coming up alot. For this shocked face I use 3 circles. The hard part of this was trying to get the vircles in the right places but I figured that for the mouth especially to have it around the 300 mark which is close to the middle for the rows and columns. 
![image](https://github.com/user-attachments/assets/626a29c4-71a6-47ed-9089-186361ad8272)


Then simply for the for the sad face and the happy face it was a sake of cutting the shock mouth in half so for the sad face what I did was using this code.


![image](https://github.com/user-attachments/assets/4385068a-e967-49f5-85e8-f39287ffc40c)


To move it to make it look more like a sad face I moved the rows down.



This is my smiley face. 

![image](https://github.com/user-attachments/assets/e82134f5-c01a-479e-98d0-a6ba657bb0af)

As you can see in this code that the arcs are just going opposite ways. and instead of going - 320 its goign == 320 so that the arc goes the other way. 



### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">











This is a picture of my test bench as I simulated the VGA Colour Stripes. In this the rows and columns are taccing track of the picture 

<img src= https://github.com/EoinFitz03/SOCproject/blob/main/image.png>


This is a picture of my VGA top for the stripes. As you can see I had to call the colour stripes 
![image](https://github.com/user-attachments/assets/df084a9e-ee8c-4773-8cd4-a22ecb74ff15)


# **Faces**
For my actual projct I decided to do faces. The way it works is starts of with a normal face so just straigt line for the mouth. 
Then using the state machine it switches to a sad face then to a smiley face and finally to a shocked face. 
## **State machine**
![image](https://github.com/user-attachments/assets/5e3ca55e-ed3f-4a95-a898-9d677d3ee5a3)

This is my state machine the way it works is by cycles through four states in a loop. Each state represents a different face normal, shocked, smiley, and sad. When the state changes, it updates to the next face in the sequence, going back to the first face after the last one. The case statement defines the order of transitions.

![image](https://github.com/user-attachments/assets/7de1f6f3-2df9-4447-92a4-518fedd08eea)
This is my Shocked face. In this code you can see I have made 3 full circles for eyes and mouth 


## **Formula used to make circles for eyes mouth and faces**
![image](https://github.com/user-attachments/assets/98903bd5-8f29-4296-85dc-861f125fa60a)
![image](https://github.com/user-attachments/assets/e652a4e4-9894-4138-8533-6bcc0bb08617)


This formula checks if each pixel on the screen lies inside or on the edge of a circle. The center of the circle is at (240, 320), and it has a radius of 120. If a pixel satisfies this condition, it is colored yellow, creating a circular face on the display. 
