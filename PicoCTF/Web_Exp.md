## Cookies

When I click on the URL, I'm taken to this page:


<img width="1440" alt="Screenshot 2024-12-22 at 7 16 24 PM" src="https://github.com/user-attachments/assets/2cf360c3-8b49-4fe9-a47d-514d1c37fc14" />

I start by seeing how the search bar actually relays messages by inspecting element >> storage

<img width="1440" alt="Screenshot 2024-12-22 at 7 29 45 PM" src="https://github.com/user-attachments/assets/83cdc01f-31ba-4071-b039-c1f9cc5ba527" />

After this, I tried not putting a viable cookie name;

<img width="1440" alt="Screenshot 2024-12-22 at 7 30 58 PM" src="https://github.com/user-attachments/assets/b9d60e4b-8f81-4f7b-bed9-95b6f89a2fea" />

Value =-1
<br/>
So I tried, trial and error way to increment the value by 1, until I landed on value =18; I got the flag
<img width="1440" alt="Screenshot 2024-12-22 at 7 33 22 PM" src="https://github.com/user-attachments/assets/1c165542-1dcf-4a24-b273-f3ae1b09a960" />



NOTE : AFTER WATCHING MULTIPLE VIDEOS AND RESEARCHING, I HAD TO USE TRIAL AND ERROR. I WANT TO KNOW SHORTER WAYS TO SOLVE THIS.
<br/>
<br/>
The flag : picoCTF{3v3ry1_l0v3s_c00k135_a1f5bdb7}

## Forbidden Paths

On clicking the link, I got the following page:
<img width="1440" alt="Screenshot 2024-12-23 at 9 17 05 PM" src="https://github.com/user-attachments/assets/a322785d-8841-4682-b5f4-74cc60fc0e8a" />

Since the challenge said that all the files are residing within (/usr/share/nginx/html/) and is a file belonging to this. 
<br/>

Trying only flag.txt, did not not give me the flag.
<br/>
And since the website is filtering absolute path, I had to use relative path which we know is ../../../../flag.txt (Each ".." representing a directory)

<img width="1440" alt="Screenshot 2024-12-23 at 9 20 30 PM" src="https://github.com/user-attachments/assets/af03a03e-320a-46a8-a8d9-09c3ad09c184" />

I got the flag.
<br/>
<br/>

The flag : picoCTF{7h3_p47h_70_5ucc355_e5a6fcbc}

****

## SOAP 

On launching the instance, I got the link for the web portal.


<img width="1435" alt="Screenshot 2024-12-24 at 10 38 45 PM" src="https://github.com/user-attachments/assets/0a513677-e369-4472-b1e4-bba94bc5deee" />

<img width="1440" alt="Screenshot 2024-12-24 at 10 55 10 PM" src="https://github.com/user-attachments/assets/43f4f46d-648b-4bcc-acd3-08c8f43c4d3d" />


Upon finding the response, I got the flag;

The flag : picoCTF{XML_3xtern@l_3nt1t1ty_55662c16}






