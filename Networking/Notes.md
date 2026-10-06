# NetworkChuck New  
- Initially made on Remnote, but, later transferred to here.
- Extracurricular understanding  

# Networking — Subnet ep1  

- Ansar are like Hosts... In IP address, we have the last set (host) 192.168.1.0  
- IP Address is like street, Home is like Host.  
- When device wants to communicate outside street/ IP address (outside network), has to talk with Router/ Default Gateway  
- Network portion 192.168.1 (first 3 no's)—— constant does not change., like if you live at the same address, but different rooms in your house
- Host— last number, eg .0 — can change — Variable (like the rooms in your house)  
> I use the Same House, different Room analogy, makes more sense in a Local Area Network (where we live at the same location, but, different devices are different hosts.)  
> Eg. I live at this address (x street), in this room (7). Eg, laptop is 192.168.1.48, PS5, 192.168.1.60, phone 192.168.1.30  
> Can hand data packets at the same address/ network, different Room  
> BUT, if you have to discuss data packets across different parts of the world/ networks, gotta go through router.  

Initial understanding, subnet mask is locked with the first 3 numbers of IP address. — ie. Locked with subnet mask (255.255.255.0)  
- in IP Address, the last part of octet (.0) in, 192.168.1.0, can't touch/ configure a device to it — Network address/ Subnet ID  
- 192.168.1.255 — broadcast address — loudmouth  
- 192.168.1.1 — Default Gateway — Router  
- Last portion of IP address, host, can assign a number, 0-255 range. 0 can't, 1 can't, 256, can't. So 256-3=253 devices can have their own host.  

Subnet Mask tells us what our House Address is — IP address.  
> Number with IP Address is Locked, when there's a corresponding  255 in Subnet (eg, 1 and 255, 1.0.0.0; 255.0.0.0) — same octet/set in IP address,  They're locked basically — can't assign devices.  
> 3 255s = locking in first 3 (IP) numbers  
   
**> If a company has a IP address (combos big), eg. 4.0.0.0 and 255.0.0.0 — they can shorten it into 4.5.6.0; 255.255.255.0 — reducing their combos (from like millions to just 0–255, 256.) Turning a large network into smaller/ sub net-works. (Subnet= smaller pool of combos.)  
> If my IP is 10.0.0.0 and subnet is 255.255.0.0 then the first two sets, in the IP address, are locked (with those 255s in Subnet)  

We all have only 1 Public IP Address + we have the private IP address (eg. 192.168.1.0) at home, but, to access the internet, a NAT is used to translate that to a public IP address.  
- They (IANA) took a chunk/ range of Public IP Addresses and designated it as Private (eg. 192.168.0.0–192.168.255.255, subnet 255.255.255.0)  

- Our network leaves our bubble/ LAN, with one identity/ public ip  

Subnet Mask trick  
> At the end right, there's the host part, first part (on left) is network..to calc, how many hosts we can have, we do 2^(no.Zeroes)-2  
- how many zeroes there are, eg. In subnet mask, 255.255.255.0, there's 2⁸^(-2) = 254 (subnet ID, broadcasting address removed)  

*>>  If Subnet Mask= 255.255.254.0, we have 11111111.11111111.11111110.00000000 (9, zeroes, 2⁹(-2) =512-2 bits), which translates to 510 available hosts ↓↓  
> - 510 devices can connect, 510 usable IP Addresses on network.  
> - Subnet Mask tells us how *big* our network is.  
> - Subnet Mask is Contiguous (row of ones, row of zeroes.)  

# Networking  
- Zone Files — Stores info. about Domain  
> - Easier to read DNS records  
> - dig +short ns google.com — short version of name servers  

Networking DNS how?  
Initial Trial&Error — for understanding  
> - So I wanna go to a website (iA Islamqa.org)  
> Computer Checks Cache, if IP Address found, good, if not, time to take to DNS Resolver  
> - We know Cloudflare is islamqa.org's TLD (providing the .org)  &later understood this to be incorrect.  
> - The ANSh (Authoritative Name Server Host) gives the islamqa NS &later understood this to be Cloudflare.  
> - Thedomain  (islamqa.org) contains the zone files/ metadata  
- Client/ DNS Resolver, always check Cache first. Otherwise, RTA — Root, TLD, ANSh  
> - Resolver caches result, after getting the islamqa.org IP address.  

- Turns out, Cloudflare IS NOT A TLD. IT IS A NAME SERVER, eg. *.ns.cloudflare.com Cloudflare operates Authoritative Name servers.  
- So .com, .org, would be TLDs.  
- Authoritative name serves store domains (store and serve DNS records for domains)   
 
Recap:  
1. Client asks for islamqa.org.. checks local cache, nope. Goes to DNS Resolver.  
2. Resolver checks cache, nope. Goes to Root server (tryna get the IP address)  
3. Root server has no knowledge of IP address, but, can help with .org part (TLD part), sends that as a response  
4. Resolver checks TLD for Authoritative Name Server (ie. sends back Cloudflare part, ie. bayan.ns.cloudflare.com)  
5. Resolver uses this, asks cloudlfare (AName Server) for IP address.. Cloudflare sends back the DNS records/ IP address for islamqa.org, to, DNS Resolver  
6. DNS Resolver shares it to Client (here's the IP ADDRESS 104.21.41.97, for islamqa.org)  
 
- DNS debugging tools (nslookup <domain>, dig <domain>)  

Convert Binary into Decimal: Use 2⁰, 2¹, 2².. — for each binary digit, counting from the right — as, each Binary digit, in  8bits, represents 2^to the power of something.. the Power/ value increases the more left across you go  
> - 11111111, is the same as, 128 (2⁷) + 64 (2⁶) + 32 (2⁵) + 16 (2⁴) + 8 (2³) + 4 (2²) + 2 (2¹) + 1 (2⁰) = 255.  

Convert a Decimal into Binary: Divide that Number by 2, noting down If there's any Remainder (.5, if using a calc.), that .5/ remainder= a 1, in Binary.  
> - if, after dividing the decimal by 2, no remainder (no .5), then this in Binary= 0.  
> - If one gets a remainder ( or .5), the remainder part, is ignored, when dividing again (the ÷2 continues, without, the .5), until the division= 0 (which is also 0 in Binary!)  

In application:  
- To convert IP address, eg. 192.168.0.1 to Binary, Divide each set, by 2, noting the Remainder (if Calc.. gives an answer with .5 etc., then you don't take into consideration anything after the decimal point cos that's just a remainder and we make note of that, as 1.)  
> - We also, could use the old school short division table (bus stop method) SubhanAllah — to help visualise the remainder.  
> - and again, We could use the calculator, but, ignoring whatever is after the point.  

Practical ex. (IPv4/ subnet to binary):  
- 10.0.0.1 = (10)   00001010.00000000.00000000.00000001 ✓ Alhamdulillah Correct 💯, other than those extra 2 zeroes missing (for 8bit), and the Missing Dot between sets  
- 255.0.0.0 = (255) 011111111 & then 0 0 0  ✓ Alhamdulillah, correct, just a missing dot and the 3 sets of 8 zeroes missing and the extra 0 at the start of Binary 255 (it's lit. just 8 1's.)  
> ANSWERS show I needed to have 8 binary bits & Dot  

- 255.255.255.0 (remember each set represents 8 bits, eg. 11111111.11111111.....  
- The end / is the subnet mask, eg. 192.168.0.1/26.. /26 is subnet mask  

NAT: Translator of private and (ltd) public IPs. internet doesn't understand Private IPs, only Public IPs.. static IP- eg. Website. Dynamic IP; pool, PAT; same public IP, different port no's  
> - protect your private/ local IP address   
  
Internet is basically a bunch companies talking/ communicating with each other. Bro, capitalism surrounded.  

- traceroute shows path taken to reach a destination/ website.  
  

Tld has a authoritative server where it pulls the name server for the domain (which would be sent to resolver, to query the ANSh; Authoritative Name Servers Host)  

> Slight modification to what I previously knew (user, cache, resolve cache, Resolver root, root tld, Resolver tld, tld has a Authoritative DNS Server that holds the delegations/ NS list, tld pulls NS, sends to Resolver, Resolver queries ANSh, ANSh goes ah yep, there you go, provides the IP address, resolver remembers it in cache, sends to User.)  

Other Bits.:  
- Bits in a MAC Address: 48  
- TCP= Transmission Control Protocol  
- CIDR= Classless InterDomain Routing  
- CIDR notation? /24 = 24 network bits.  
- Standard streams in networking? *= TCP, UDP, ICMP  
- Layers of TCP/IP = 4  

- Switch knows where to create dedicated point to point connection in LAN (based on porting)  

Empty directories do not get pushed to GitHub  



MaShaAllahu LaQuwataIlaBillah — This is What The God, Allah, has Willed, There is No Power Except with Allah.