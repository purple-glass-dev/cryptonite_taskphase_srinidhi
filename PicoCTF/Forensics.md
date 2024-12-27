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
<br/>
It can't be directly opened, so I extract(-x mode is for that) using ar command the file contents.
```
srinidhia@srinidhis-mbp ~ % cd Desktop
srinidhia@srinidhis-mbp Desktop % ar -x program.deb
```
<img width="140" alt="Screenshot 2024-12-19 at 11 51 53 AM" src="https://github.com/user-attachments/assets/301170dc-a676-46f8-9ede-55b8de8e001b" />

Out of three, opening control first, to find two files called--control and ms5sums. Opening md5sums, I get the following:
```
71bdab1263ab4b8d28f34afa5f0ab121  usr/bin/steghide
11db80c2a5dbb9c6107853b08aeacc49  usr/share/doc/steghide/ABOUT-NLS.gz
57deb17212483b49f89587180d4d67d4  usr/share/doc/steghide/BUGS
72c7831222483f5c6d96ac2a8ca7ad48  usr/share/doc/steghide/CREDITS
adbb29f44a5e5eefda3c3d756cc15ab1  usr/share/doc/steghide/HISTORY
fe7cac39a1a1ef0975d24dfcf02f09b7  usr/share/doc/steghide/LEAME.gz
85587b9213ca2301eb450aad574d5f87  usr/share/doc/steghide/README.gz
a9e03fa8166b8fa918c81db1855b68d1  usr/share/doc/steghide/TODO
09d7710e276a06c4a3f3bc81b3b86a41  usr/share/doc/steghide/changelog.Debian.amd64.gz
e454b20fdc2208f8170e28b90b6d43f7  usr/share/doc/steghide/changelog.Debian.gz
1a2e10366a3a55d7a4cb5fc3c87a6bf7  usr/share/doc/steghide/changelog.gz
df8c0ea893b3f6f64a917824c6c9d224  usr/share/doc/steghide/copyright
fc53645374c583f11f628331be710d9a  usr/share/locale/de/LC_MESSAGES/steghide.mo
b8ceabc96f9bffd9157103e1a86be33f  usr/share/locale/es/LC_MESSAGES/steghide.mo
87ee9a19bb49b217dad67b5a889bb1d1  usr/share/locale/fr/LC_MESSAGES/steghide.mo  
dbc3a8e974ccf7e91da81aca4a5c1605  usr/share/locale/ro/LC_MESSAGES/steghide.mo
921a5afd279097e4ed359ce3767068f5  usr/share/man/man1/steghide.1.gz
```
On some research, I found that md5sum(Message-Digest algorithm 5 hash), is, in simple terms, a digital fingerprint which ensures that none of the data is manipulated during file tranfer.
<br/>
Since, I didnt get any useful information from md5sum, I next opened "contol" to get this
<img width="742" alt="Screenshot 2024-12-19 at 11 59 30 AM" src="https://github.com/user-attachments/assets/2674525d-4e78-430d-9ee4-329a5b2e865b" />
Reading this further, I noticed that the flag could potentially be encrypted within one of the three provided images in the challenge.
<br/>
And from the clue given about stegnography, I used MacPorts(package manager) to install the steghide library. After doing that, I used the prompts to extract the decoded message, which was stored in a txt file called "flag.txt", cat-ed it to get my final flag
<br/>
<br/>
NOTE : DUEDILIGENCE was the passphrase, as it was given in the "plan" file.
```
srinidhia@srinidhis-mbp Desktop % steghide extract -sf picture1.bmp -p DUEDILIGENCE
steghide: could not extract any data with that passphrase!
srinidhia@srinidhis-mbp Desktop % steghide extract -sf picture2.bmp -p DUEDILIGENCE
steghide: could not extract any data with that passphrase!
srinidhia@srinidhis-mbp Desktop % steghide extract -sf picture3.bmp -p DUEDILIGENCE
wrote extracted data to "flag.txt".
srinidhia@srinidhis-mbp Desktop % cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

The flag : picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919} 

****

## Tunn3l_v1s10n

The first thing I had to do in this challenge is to understand the file type of the particular file given, since it isnt apparent. 
So with the help of (https://hexed.it), I was able to find out the magic numbers which help in knowing the type of file it is.

<img width="1440" alt="Screenshot 2024-12-22 at 3 58 59 PM" src="https://github.com/user-attachments/assets/63ffdd2b-c9ff-43f2-b286-82ec084a6bbd" />

Using (https://en.wikipedia.org/wiki/List_of_file_signatures) , I was able to figure out that given file is a BMP file

<img width="913" alt="Screenshot 2024-12-22 at 4 01 13 PM" src="https://github.com/user-attachments/assets/237705d8-d42c-4849-87cf-b2a1e11811a4" />

So now I renamed the given file, with an extension of .bmp `tunn3l_v1s10n.bmp`
<br/>
Next thing I did was to find a txt to bmp converter and landed upon this after a quick google search (https://convertio.co/bmp-jpg/)
<br/>

Got this;

<img width="1125" alt="Screenshot 2024-12-22 at 4 05 09 PM" src="https://github.com/user-attachments/assets/31080d4b-7fa4-4413-a5b2-9e220acff680" />

Making this change:

<img width="1440" alt="Screenshot 2024-12-22 at 6 58 02 PM" src="https://github.com/user-attachments/assets/dadec010-61b0-4883-ae7e-7ae5dfd50d2a" />


The flag : picoCTF{qu1t3_a_v13w_2020}

****

## m00nwalk

Given was a .wav audio file. From the clues and after some research, I came to conclusion that I had to somehow find a way to convert this .wav file to a image file.

<br/>

My goal was to try and install a sstv decoder but I wasn't able to find any without having to install a linux environment or kali-linux environment. Any online sstv decoder did not yield a useful image. 

<br/>
<img width="699" alt="Screenshot 2024-12-24 at 11 10 57 AM" src="https://github.com/user-attachments/assets/a683184d-dfe7-4e97-a686-eda1689f3f52" />

Because of this, I had to go through various write-ups for this particular CTF challenge, to get the following flag;

<br/>
<br/>

The flag : picoCTF{beep_boop_im_in_space}















