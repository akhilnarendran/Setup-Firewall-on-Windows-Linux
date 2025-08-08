# Setup-Firewall-on-Windows and Linux
Introduction of Firewall in Computer Network
A firewall is a network security device either hardware or software-based which monitors all incoming and outgoing traffic and based on a defined set of security rules it accepts, rejects, or drops that specific traffic. It acts like a security guard that helps keep your digital world safe from unwanted visitors and potential threats

<img width="500" height="300" alt="Image" src="https://github.com/user-attachments/assets/5cc0d7f2-a3ff-48b1-a63e-d13cd220297a" /> <img width="500" height="300" alt="Image" src="https://github.com/user-attachments/assets/b2fe83e1-1b2f-417e-ad97-98b071151880" />



    Accept: allow the traffic
    Reject: block the traffic but reply with an “unreachable error”
    Drop: block the traffic with no reply 


A firewall is a type of network security device that filters incoming and outgoing network traffic with security policies that have previously been set up inside an organization. A firewall is essentially the wall that separates a private internal network from the open Internet at its very basic level.


<img width="905" height="462" alt="Image" src="https://github.com/user-attachments/assets/c2037b56-0b23-4b8c-8a2c-28ca4652b88f" />


Working of Firewall

<img width="905" height="462" alt="Image" src="https://github.com/user-attachments/assets/47b35e3b-3d91-41cb-9ab6-a019c8c56a4f" />

    *Firewall match the network traffic against the rule set defined in its table. Once the rule is matched, associate action is applied to the network traffic. For example, Rules are defined as any employee from Human Resources department cannot       access the data from code server and at the same time another rule is defined like system administrator can access the data from both Human Resource and technical department.
    *Rules can be defined on the firewall based on the necessity and security policies of the organization.
    *From the perspective of a server, network traffic can be either outgoing or incoming. Firewall maintains a distinct set of rules for both the cases. Mostly the outgoing traffic, originated from the server itself, allowed to pass. Still,            setting      a rule on outgoing traffic is always better in order to achieve more security and prevent unwanted communication. Incoming traffic is treated differently.
    *Most traffic which reaches on the firewall is one of these three major Transport Layer protocols- TCP, UDP or ICMP. All these types have a source address and destination address. Also, TCP and UDP have port numbers. ICMP uses type code             instead       of port number which identifies purpose of that packet
_____________________________________________________________________________________________________________________________________________________________________________

Windows Firewall Setup  (Windows Defender Firewall)

 "we can use"
   1. Windows Defender (Default firewall).
   2. Third-party firewalls.
<img width="922" height="483" alt="Image" src="https://github.com/user-attachments/assets/93a649b3-c458-4d4a-9be4-dfb978f3cf04" />


  1. Open Windows Firewall

    Press Win + R, type wf.msc and hit Enter to open Windows Defender Firewall with Advanced Security

   2. List Current Rules

    In the left pane, click on "Inbound Rules" or "Outbound Rules" to see existing configurations

   3. Block Telnet (Port 23)

    Right-click "Inbound Rules" and select "New Rule"
    Choose "Port" and click Next
    Select "TCP", enter "23" in "Specific local ports", click Next
    Select "Block the connection", click Next
    Keep all profiles checked (Domain, Private, Public), click Next
    Name it "Block Telnet" and click Finish

  4. Test the Block

    Open Command Prompt and try to connect to Telnet:
    text
    telnet localhost
    You should get a connection error

  5. Allow SSH (Port 22) - If Needed

    Follow same steps as above but:

        Specify port 22
        Choose "Allow the connection"

  6. Remove Test Rule

    Find your "Block Telnet" rule in Inbound Rules
    Right-click and select "Delete"


LINUX UFW (Uncomplicated Firewall) 

<img width="913" height="470" alt="Image" src="https://github.com/user-attachments/assets/05170b5f-7366-49b3-8d9d-39aa2ec3d996" />

you can install it by running the following linux command.
      
      # aptupdate && upgrade -y
      # apt-get install ufw -y  
      # sudo ufw status (if   not enabled)
      # sudo ufw enable
      # 
     
You can setup your own default policy with the following linux command

     # sudo ufw default allow outgoing 
     # sudo ufw default deny incoming 

You can add rules for allowing incoming and outgoing traffic in two ways, using the port number or using the service name. 

    # sudo ufw allow http 
    # sudo ufw allow 80 
    # sudo ufw allow 23

If you want to denying  incoming

    # sudo ufw deny 23
    # sudo ufw deny 22
    # sudo ufw deny http
If you want to filter packets based on TCP or UDP,

     sudo ufw allow 80/tcp 
     sudo ufw allow 21/udp   


<img width="710" height="228" alt="Image" src="https://github.com/user-attachments/assets/103f4bb8-7044-4a89-9718-fba5be78ae37" />





