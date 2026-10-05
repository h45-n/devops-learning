# Networking
- Compared which Instance was cheapest on Free tier (although it is defaulted to t3.micro, I found t4g.micro, compared with the known on-demand prices, to be the cheapest and decided to use this — had to select x64 Arm)
<img width="700" height="auto" alt="Screenshot_2026-10-04-23-44-28-73_ef634ab0a744fd035b88627414f28d5e" src="https://github.com/user-attachments/assets/c9597da9-e352-4a41-a586-8900763abeef" />  

- Launched a new EC2 Instance, to run NGinx — used bash Scripting (eg. Shebang and yum) to install NGinx on this AWS web server.  

Script was:  
"#!/bin/bash  
sudo yum update -y && sudo yum install nginx -y  
sudo systemctl enable nginx  
sudo systemctl start nginx" 

- Script entered into User data.
(the -y flag for yum, auto-answers, yes, to any confirmation prompts )
- Had to allow HTTP for NGinx
<img width="857" height="5704" alt="Screenshot_2026-10-04-22-02-12-80" src="https://github.com/user-attachments/assets/06d9fccd-3071-4774-a1ef-b5e97802b69e" />  

- HTTP port running (80) 👍
<img width="360" height="auto" alt="IMG_20261004_220532" src="https://github.com/user-attachments/assets/bc247ebc-ac9a-4423-a0cd-653d36afc25b" />  
  
- Needed to copy Public IPv4 to Cloudflare (add A record) to point Domain to EC2 server
<img width="440" height="auto" alt="Screenshot_2026-10-04-22-11-14-65" src="https://github.com/user-attachments/assets/7fe628f5-6eda-4f11-91cc-b2b6287d235b" />

Alhamdulillah, http://hasandev.co.uk/works — DNS propagated, loads Nginx default page.

<img width="450" height="auto" alt="Screenshot_2026-10-04-22-13-55-98_cbf47468f7ecfbd8ebcc46bf9cc626da" src="https://github.com/user-attachments/assets/ea3616a2-41f8-4a5d-959b-21cd6ea29154" />  

MaShaAllahu LaQuwataIlaBillah (This is what The God has willed. There is no power except with The God.)
