## Trivial Flag transfer protocol

The file given in the challenge is in 'PcapNG' format which stands for Packet CAPture Next Generation file. In simple terms, it is the file format which captures packets(smallest unit of data that is transferred through a network).

<br/>
<br/>
 The first step, is to intall a third party application to be able to open and support the PCAPNG format. 
 <br/>
 Used Wireshark to gauge the network traffic and got something like this
 
<img width="1440" alt="Screenshot 2024-12-18 at 6 54 27 PM" src="https://github.com/user-attachments/assets/00369a78-a4ea-4c45-b117-96613946ca2e" />

Now I filtered out the TFTP traffic;

<img width="1440" alt="Screenshot 2024-12-18 at 6 55 34 PM" src="https://github.com/user-attachments/assets/33a49199-ac80-45a9-9560-eea57c9179f6" />

From here, I can variety of informations about the different packets--Some are Acknowledgment, Data packets etc; But what I require is only the information files with which I can find out the flag. So I exported only the TFTP files, like I did below:


<img width="1440" alt="Screenshot 2024-12-18 at 6 59 52 PM" src="https://github.com/user-attachments/assets/9588d8c5-c7e9-43df-b175-9bfa2fb70afa" />

I got this:

<img width="1440" alt="Screenshot 2024-12-18 at 7 00 55 PM" src="https://github.com/user-attachments/assets/a76ea7ad-0f63-48e6-9491-d761c1d65b87" />

Saving all the files, I first opened the instructions.txt file, hoping to gather some information but I had only this:
<img width="642" alt="Screenshot 2024-12-18 at 7 02 33 PM" src="https://github.com/user-attachments/assets/d2919065-c4d8-4fb2-9c4f-86e0c06dc80e"/>

 I then opened plan file, hoping to find someother working point, also to deal with the same dead end:
 <img width="640" alt="Screenshot 2024-12-18 at 7 06 01 PM" src="https://github.com/user-attachments/assets/87934e52-2e31-41d2-9755-ba27a1b09649" />

 After a quick google search, I landed on a Multi Decoder by CacheSlueth (https://www.cachesleuth.com/multidecoder/), which when I pasted the encypted message of instructions.txt, gave me the following
 
<img width="1438" alt="Screenshot 2024-12-18 at 7 10 15 PM" src="https://github.com/user-attachments/assets/f3adb425-3aba-4624-ad92-5c01978d3fbb" />

<img width="1440" alt="Screenshot 2024-12-18 at 7 10 44 PM" src="https://github.com/user-attachments/assets/492cda04-efb9-4ebd-b703-1be87c1bab76" />

The message which was decypted, made sense after proper spaces;

```
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER.FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN
```

So, I attempted to decrypt the message of plan file, using the same platform to get this;
```
I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE.CHECK OUT THE PHOTOS
```
Opening the program.deb file,(deb--Debian linux extension file--Software package format)






