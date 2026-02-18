# Python-Network-Port-Scanner

* $$\color{red}{\text{Step-1: The set-up}}$$
  | 1. Open Any Linux Terminal | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/2#issue-3943769399) | |
  | :--- | :---: |:--- |
  | 2. <code>cat > portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/3#issue-3943797607) | |
  | 3. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/4#issue-3943813622) | |
  | 4. <code>Ctrl + C</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/5#issue-3943822231) | |
  | 5. <code>ls</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/6#issue-3943861328) | Here, you should see $$\color{white}{\text{portscan.py}}$$(file) not same color as as other $$\color{blue}{\text{directories}}$$ |
  | 6. <code>nano portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/7#issue-3943889557) | |
  | 7. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/8#issue-3943898199) | |

* $$\color{red}{\text{Step-2: The script}}$$
  <pre><code>                                                                            
    import socket
    import subprocess
    import sys
    
    from datetime import datetime
    
    subprocess.call('clear', shell = True)
    
    remoteServer = input("Enter a remote host to scan: ")
    remoteServerIP = socket.gethostbyname(remoteServer)
    
    print("-" * 60)
    print("Please wait, scanning remote host", remoteServerIP)
    print("-" * 60)
    
    t1 = datetime.now()
    
    try:
        for port in range(1,5000):
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(0.5)
            result = sock.connect_ex((remoteServerIP, port))
            if result == 0:
               print("Port{}:        Open".format(port))
            sock.close()
    
    except KeyboardInterrupt:
        print("You pressed Ctrl + C")
        sys.exit()
    
    except socket.gaierror:
        print("Hostname could not be resolved Exiting")
        sys.exit()
    
    except socket.error:
        print("Couldn't connect to server")
        sys.exit()
    
    t2 = datetime.now()
    
    total = t2 - t1
    
    print("Scanning Completed in", total)
  </code></pre>
  
* $$\color{red}{\text{Step-3: Explanation of script}}$$
  |  write this inside portscan.py(file) | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/8#issue-3943898199) | Same as $$\color{red}{\text{Step-1: The set-up}}$$, 7. <code>Enter</code> |
  | :--- | :--- | :--- |
  | 1. Using import in python<br><code>import socket</code><br><code>import subprocess</code><br><code>import sys</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/9#issue-3944124498) | these are things that someone else coded in the Python language<br> that allows us to automate some of the stuff that we're going to be doing |
  | 2. Using datetime in Python<br><code>from datetime import datetime</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/10#issue-3944134652) | 1. What we're doing here is<br>we want to be able to know what the current date & time is<br><br>2. The Reason for that is we're going to need to know,<br>here's when I Started, here's when I Ended |
  | 3. How to clear your screen in python<br><code>subprocess.call('clear', shell = True)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/11#issue-3944147958) | 1. Basically like <code>clear</code><br><br>$$\color{orange}{\text{2. Automatically clear the screen when we run this file}}$$<br><br>3. So that for next input we can see that on the wider screen |
  | 4. Asking for input in Python<br><code>remoteServer = input("Enter a remote host to scan: ")</code><br><code>remoteServerIP = socket.gethostbyname(remoteServer)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/12#issue-3944171652)<br>![*View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/13#issue-3944211197)  | 1. we're defining remoteServer here as this particular function,<br> & then we say, enter a remote host to scan.<br><br>2. The remoteServerIP is going to be the result of what<br>you enter when it asks you to enter the remote host to scan. |
  | 5. Printing information in Python <br><code>print("-" * 60)</code><br><code>print("Please wait, scanning remote host", remoteServerIP)</code><br><code>print("-" * 60)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/14#issue-3944320235) | Basically like a Banner<br><br>----------------------------------------------------------<br>Please wait, scanning remote host <your input's IP><br>---------------------------------------------------------- |
  | 6. Checking the date & time in Python<br><code>t1 = datetime.now()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/15#issue-3944344311) | 1. Check the date & time the scan was started.<br><br>2. we're defining t1 as the current date & time.<br><br>3. That way, at any point in our code we can say t1 & it will actually tell us what the current date & time is without us having to type out that long function(<code>datetime.now()</code>) again.<br><br>4. That's the purpose of doing that. |
  | 7. Using a function to specify ports in Python<br><code>try:</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/37#issue-3956651966) | You always use <code>try:</code> paired with <code>except:</code> <br> $$\color{orange}{\text{For Example:}}$$ <br> <code>try:</code> <br>     # 1. Python attempts to run this code first. <br>     # This is the "risky" part. <br> <code>    print(10 / 0)</code> <br> <code>except:</code> <br>     # 2. If (and ONLY if) an error happens above, <br>      #    Python jumps here immediately. <br> <code>    print("Oops! You can't divide by zero.")</code> |
  | <code>for port in range(1,5000):</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/16#issue-3944375510) | 1. we say, for port in range. This is What we call a for loop.<br><br>2. In other words, it's a way to repeat something 5000 times(instead of writing 5000 codes) over & over again.<br><br>3. What we're doing here is we're going to scan all ports between one & 5000.<br><br>4. So we're going to check that on each IP address we scan. |
  | <code>sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/17#issue-3944397518) | # Buying the Phone<br>1. <code>sock = </code><br>This is just a variable name.<br><br>2. <code>socket.socket(...)</code><br>$$\color{orange}{\text{What it is:}}$$ This is the command to $$\color{orange}{\text{create}}$$ the object. You are call the $$\color{orange}{\text{socket}}$$ Library(which you imported at the top) & asking it to build a new socket for you.<br>$$\color{orange}{\text{Analogy:}}$$ This is like walking into a store and saying, $$\color{orange}{\text{"I would like to buy a communication device please".}}$$<br><br>3. <code>socket.AF_INET</code><br>$$\color{orange}{\text{What it is:}}$$ This tells the socket what kind of $$\color{orange}{\text{address}}$$ you will be using<br>$$\color{orange}{\text{  AF}}$$ = Address Family<br>$$\color{orange}{\text{  INET}}$$ = Internet(specifically IPv4)<br>$$\color{orange}{\text{Translation:}}$$ "I will be using standard IP(like 192.168.1.5), not weird futuristic ones(IPv6) or local paths". <br> $$\color{orange}{\text{Analogy:}}$$ You are telling the store clerk, "I want a device that uses $$\color{orange}{\text{standard phone numbers}}$$(xxx-xxx-xxx) not email addresses". <br><br>4. <code>socket.SOCK_STREAM</code><br>$$\color{orange}{\text{What it is:}}$$ This tells the socket how to talk.<br><code>  SOCK_STREAM</code><br>means a "Stream" socket, which uses $$\color{orange}{\text{TCP}}$$(Transmission Control Protocol)<br>$$\color{orange}{\text{Why TCP?}}$$ TCP is reliable it creates a solid connection(like a phone call) where you say "Hello?" & wait for an aswer.<br>the other option is $$\color{orange}{\text{UDP}}$$(User Datagram Protocol), which is like throwing a letter in the mail-you don't know if it arrived.<br>$$\color{orange}{\text{Analogy:}}$$ You are telling the clerk, "I want to make a $$\color{orange}{\text{live phone call}}$$ where we stay on the line, not just send a text message". <br><br> # $$\color{orange}{\text{Putting it all together}}$$<br>When you write this line,<br><code>sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)</code><br>you are telling Python: "Create a new connection tool called <code>sock</code>. Make sure it uses $$\color{orange}{\text{IPv4 addresses}}$$(<code>AF_INET</code>) & communicates using a $$\color{orange}{\text{reliable TCP connection}}$$(<code>SOCK_STREAM</code>)". |
  | <code>sock.settimeout(0.5)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/38#issue-3956762513) | $$\color{orange}{\text{The "Patience Limit"}}$$ <br> $$\color{orange}{\text{Purpose:}}$$ Prevents the program from freezing (hanging) on a single port. <br> $$\color{orange}{\text{How it works:}}$$ It sets a timer of 0.5 seconds. If the server doesn't reply within that time (which happens often with firewalls), the script stops waiting and moves immediately to the next port. Without this, scanning 5,000 ports could take hours. |
  | <code>result = sock.connect_ex((remoteServerIP, port))</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/18#issue-3947604409) | 1. <code>sock.connect_ex(...)</code> <br> $$\color{orange}{\text{What it does:}}$$ This tells your "sock" (the phone) to try to connect to the target. <br> $$\color{orange}{\text{Why}} $$<code>_ex</code> $$\color{orange}{\text{?}}$$ This stands for $$\color{orange}{\text{connect extended}}$$ <br> i. A normal <code>.connect()</code> would cause your program to $$\color{orange}{\text{crash}}$$(stop working) immediately if the $$\color{orange}{\text{port is closed.}}$$ <br> ii. <code>.connect_ex()</code> is gentler. Instead of crashing, it simply $$\color{orange}{\text{gives you back a number}}$$(a code) telling you what happend. <br><br> 2. <code>((remoteServerIP, port))</code> <br> $$\color{orange}{\text{What it is:}}$$ This is the $$\color{orange}{\text{destination you are dialing.}}$$ <br> i. <code>remoteServerIP</code>: The streed address of the building(e.g., <code>192.168.1.1</code> ). <br> ii. <code>port</code>: The Specifically apartment number or door you are Knocking on(e.g, <code>80</code> ). <br> Why the double parentheses <code>((...))</code> ? <br> i. This is a strict Python rule. The socket requires $$\color{\text{one single package}}$$ containing both the IP & the Port. <br> ii. In Python, putting values inside <code>( )</code> creates a tuple(a fixed pair). So you are passing $$\color{orange}{\text{one tuple}}$$ (IP, port) into the function. <br><br> 3. <code>result =</code> <br> $$\color{orange}{\text{What it is:}}$$ This catches the answer from the server. <br> $$\color{orange}{\text{The secret code:}}$$ <code>connect_ex</code> returns a number: <br> i. $$\color{orange}{\text{if it returns}}$$ <code>0</code> $$\color{orange}{\text{:}}$$ $$\color{orange}{\text{Sucess!!}}$$ The connection was establised(The door is OPEN). <br> ii. $$\color{orange}{\text{if it returns anything else(like }}$$ <code>11</code> $$\color{orange}{\text{, }}$$ <code>10061</code> $$\color{orange}{\text{, etc):}}$$ <br> $$\color{orange}{\text{Failure!!}}$$ The port is closed or filtered. <br><br>  # $$\color{orange}{\text{Putting it all together}}$$ <br> Imagine you are a $$\color{orange}{\text{delivery driver}}$$ (the script): <br>  $$\color{orange}{\text{1. The Code: }}$$ <code>sock.connect_ex((remoteServerIP, port))</code> <br> i. $$\color{orange}{\text{you: }}$$ You walk up to the building( <code>IP</code> ) & Knock on apartment # 80( <code>port</code> ). <br> $$\color{orange}{\text{2. The Return: }}$$ <br> i. if someone opens the door, that is an <code>0</code> (Success). <br> ii. if nobody answer, or a guard yells "Go away!", that is an <code>Error Code</code> (Failure). <br> $$\color{orange}{\text{3. variable: }}$$ <code>result =</code> <br> i. You write that code(0 or Error) onto your clipboard( <code>result</code> ) so you can check it in the very next line of your code( <code>if result == 0</code> ). |
  | <code>if result == 0:</code> <br> <code>           print("Port{}:        Open".format(port))</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/19#issue-3950945182) | if the $$\color{orange}{\text{door opens}}$$ ( <code>result == 0</code> ), <br> it prints $$\color{orange}{\text{"Port Open".}}$$ |
  | <code>sock.close()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/20#issue-3950973572) | if the $$\color{orange}{\text{door is Locked,}}$$ <br> it just $$\color{orange}{\text{move to the next}}$$ number. |
  | 8. The Safety Net: <br> Error Handling(try...except) <br> <code>except KeyboardInterrupt:</code> <br> <code>    print("You pressed Ctrl + C")</code> <br> <code>    sys.exit()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/21#issue-3951021786) | i. These blocks wait for specific errors. $$\color{orange}{\text{KeyboardInerrupt}}$$ happens if you hit <code>Ctrl + C</code> on your keyboard. <br> ii. If you want to $$\color{orange}{\text{stop}}$$ the script early, or if the internet cuts out, you don't want the program to crash effectively. <br> iii. You want it to exit gratefully & tell you what happened. |
  | <code>except socket.gaierror:</code> <br> <code>    print("Hostname could not be resolved Exiting")</code> <br> <code>    sys.exit()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/22#issue-3951056900) | i. This stands for $$\color{orange}{\text{Get Address Info Error}}$$ it happens when the script $$\color{orange}{\text{cannot find the IP address}}$$ for the hostname you typed. <br> "I Looked in the $$\color{orange}{\text{phonebook(DNS)}}$$ for <code>gogle.com</code> but the name $$\color{orange}{\text{doesn't exist.}}$$ <br> iii. it prints <code>Hostname could not be resolved</code> & quits. <br> iv. $$\color{orange}{\text{Example: }}$$ You make a $$\color{orange}{\text{typo in the URL}}$$ or You \r Internet is disconnected, So the sript can't look up the IP.|
  | <code>except socket.error:</code> <br> <code>    print("Couldn't connect to server")</code> <br> <code>    sys.exit()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/23#issue-3951209133) | i. This ia a $$\color{orange}{\text{general error}}$$ for the socket tool itself. <br> ii. It cathes problems with the $$\color{orange}{\text{phisical}}$$ connection or the server. <br> iii. I know the address, but the server, $$\color{orange}{\text{isn't answering the phone}}$$ at all. <br> iv. It prints <code>Couldn't connect to server</code> & quits( <code>sys.exit()</code> ). <br> v. The server you are trying to scan is $$\color{orange}{\text{completely down}}$$ or a $$\color{orange}{\text{firewall is blocking}}$$ your computer from even talking to it. |
  | 9. Calculating time for the script to run in Python: <br> <code>t2 = datetime.now()</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/24#issue-3951249503) | # $$\color{orange}{\text{Checking time again}}$$ <br> we're defining date & time now as t2. |
  | <code>total = t2 - t1</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/25#issue-3951268406) | # $$\color{orange}{\text{Calculating the difference in time to now how long the scan took}}$$ <br> So we're going to call t1 & t2 & say, take t1, whatever the date & time was, then subtract that from t2, which is what the date & time is now, & that will tell us how long it took for the script to run. |
  | <code>print("Scanning Completed in", total)</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/26#issue-3951295983) | # $$\color{orange}{\text{Printing the information on the screen }}$$ <br> i. we're going to take that number & print that in a message that saya, scanning completed in however many seconds. <br> ii. That's the basic functionality of the script. |

* $$\color{red}{\text{Step-4: Saving script}}$$
  | 10. Exiting from the $$\color{orange}{\text{script}}$$ File. <br> <code>Ctrl + X</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/27#issue-3951318135) | |
  |:---|:---|:---|
  | 11. Saving $$\color{orange}{\text{script}}$$ File Before Exiting. <br> <code>Y</code> Yes| ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/28#issue-3951343868) | |
  | 12. Whant to Rename( <code>nano portscan.py</code> ) or name(if not given <code>nano</code> ). | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/29#issue-3951371192) | If Rename it will ask keep it <code>portscan.py</code> or change it. <br> If name it will ask for to give a name to your script file. |
  | 13. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/30#issue-3951384995) | |

* $$\color{red}{\text{Step-5: The execution}}$$
  | 1. <code>python portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/31#issue-3951541739) | |
  | :--- | :--- | :--- |
  | 2. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/32#issue-3951563676) | |
  | 3. Enter a remote host to scan: <code>scanme.nmap.org</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/33#issue-3951586007) | # $$\color{orange}{\text{target that we want to scan for open ports if any}}$$ <br> Nmap project provides a specific authorized target |
  | 4. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/34#issue-3951593865) | you can see <code>scanme.nmap.org</code> provide as with target IP address. <br> $$\color{orange}{\text{wait for few minutes}}$$ |
  | 5. found my first open port | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/35#issue-3951619804) | wait few more minutes for script to end |
  | 6 script Ended | ![View]( | Project Done !! |   
