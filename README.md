# ANZ-cyber-management/Network & Data Forensics
<h1> </h1>

<h2>Description</h2>
In this project i Completed a simulation focused on identifying cybersecurity threats at ANZ.
Investigated e-mails reporting suspicious items.
Analysed a Packet Capture file using an open source tool to identify and investigate any potential threats.

<br />
<h2>Tools and Utilities Used</h2>
WireShark <br />
HxD Editor <br />
Base64.guru <br />
Adobe Acrobat <br />

<h2> Walk-through:</h2>

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
<br />
<img src="https://i.imgur.com/5YbbGpX.jpeg" height="80%" width="80%" alt=""/>


<br />
<br />

A text file labelled "hiddenmessage2.txt" was discovered but when opened the content appeared to be scrambled and unreadable. I uploaded the file into HxD to decode and noticed that it identified the data as JFIF which would indicate that its originally a jpeg file and not a txt file. 
<br />
<img src="https://i.imgur.com/iKm4PBT.jpeg" height="80%" width="80%" alt=""/>
<br />
I then proceeded to save it with the correct extension .jpeg and the contents of the file was revealed.
<br />
<img src="https://i.imgur.com/NRX3MPy.jpeg" height="80%" width="80%" alt=""/>
<br />
<br />
<br />
Another Document named “secure.pdf” was found. I opened it in HxD for further analysis as the content weren’t viewable. 
After uploading it into HxD I noticed it identified the data as “PK” which would indicate it to be a Zip file.
<br />
<img src="https://i.imgur.com/3hAaBfj.jpg" height="80%" width="80%" alt=""/>
<br />
<img src="https://i.imgur.com/9LkeRjK.jpg" height="80%" width="80%" alt=""/>

Also, at the bottom of the decoded hex it stated, “Password is “secure”. 
I proceeded to fix the extension at the end of the file name to.zip. It then opened as a password protected zip file which I typed the “secure” password into. Below is a screenshot of the pdf content file called “rawpdf.pdf”.
<br />
<br />

<img src="https://i.imgur.com/XMM6iFw.jpg" height="80%" width="80%" alt=""/>
<img src="https://i.imgur.com/J80iOX7.jpg" height="80%" width="80%" alt=""/>
<br />

# CONCLUSION
<br /> 
When investigating packet capture files, I filtered the relevant traffic to only display Http. 
Once the downloaded items were identified, I proceeded to investigate them, and rebuild them forensically using a hex viewer. In order to rebuild the files i carved out just that file’s hex data, and deleted any other hex data surrounding it. Utilizing the files data signature, I was then able to further identify the files that were downloaded.

