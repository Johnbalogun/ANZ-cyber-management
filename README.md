# ANZ-cyber-management/Data Forensics
<h1> </h1>

<h2>Description</h2>
In this project i Completed a simulation focused on identifying cybersecurity threats at ANZ.
Investigated e-mails reporting suspicious items.
Analysed a Packet Capture file using an open source tool to identify and investigate any potential threats.

<br />

<h2> walk-through:</h2>

<p align="center">

Packet Capture Analysis:
I analysed the provided packet capture file using Wireshark, a free network analysis tool. By applying the filter 'http' in the filter field, I focused on HTTP packets to uncover relevant information. Within this view, I discovered intriguing HTTP GET requests, indicating specific user requests for information. Notably, one of the requests was for 'anz-logo.jpg:
<br/>
<img src="https://i.imgur.com/OjGQoHc.jpeg" height="80%" width="80%" alt=""/>
<br /> In my investigation of the image download, I delved deeper by examining the TCP stream associated with the GET request. Upon inspecting the data within the TCP stream, I observed that the download encompassed two images, evident from the presence of two headers and two footers corresponding to a .jpg format (FFD8 – FFD9 in hex). Additionally, the ASCII representation revealed the string 'JFIF' near the beginning, confirming the recognizable nature of the images: 


<br />

<img src="https://i.imgur.com/J8oZzul.jpeg" height="80%" width="80%" alt=""/>

Further exploration involved extracting the images from the TCP stream. This process entailed selecting all the hex data between FFD8 and FFD9 and transferring it to the hex editor program HxD. Subsequently, I saved the file as a .jpg and opened it, revealing the image depicted below: 

<br/>

<div class="image-container">
 <img src="https://i.imgur.com/wFkS3Sc.jpeg" height="20%" width="20%" alt="">
 <img src="https://i.imgur.com/S8gH1Q5.jpeg" height="20%" width="20%" alt="">
 <br/>

 I followed the same process for the second image. 
  <br/>
  <img src="https://i.imgur.com/x8lhxB9.jpeg" height="20%" width="20%" alt="">
  <img src="https://i.imgur.com/kIgybhs.jpeg" height="20%" width="20%" alt="">
  
  <br/>  
A file titled “How to commit a crime.docx” is part of the uncovered files. I then opened the file in HxD to analyse its contents. after further analysis a paragraph stating “Step 1 find target, step 2 hack them...this is a suspicious document” was discovered within the file.

<br />SLIDE 2:
<br />
<img src="https://i.imgur.com/IY7wdfd.jpg" height="80%" width="80%" alt=""/>

<br /> SLIDE 3:
<br />
<img src="https://i.imgur.com/6Y16e7x.jpg" height="80%" width="80%" alt=""/>
<br /> SLIDE 4:
<br />
<img src="https://i.imgur.com/3aRH0GJ.jpg" height="80%" width="80%" alt=""/>
