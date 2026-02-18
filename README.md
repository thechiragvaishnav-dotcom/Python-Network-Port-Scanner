# Python-Network-Port-Scanner

* $$\color{red}{\text{Step-1: The Set-up}}$$
  | 1. Open Any Linux Terminal | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/2#issue-3943769399) | |
  | :--- | :---: |:--- |
  | 2. <code>cat > portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/3#issue-3943797607) | |
  | 3. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/4#issue-3943813622) | |
  | 4. <code>Ctrl + C</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/5#issue-3943822231) | |
  | 5. <code>ls</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/6#issue-3943861328) | Here, you should see $$\color{white}{\text{portscan.py}}$$(file) not same color as as other $$\color{blue}{\text{directories}}$$ |
  | 6. <code>nano portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/7#issue-3943889557) | |
  | 7. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/8#issue-3943898199) | |
  | 8. **Copy & Paste:** <br> $$\color{orange}{\text{Copy}}$$ <code>Ctrl</code> + <code>C</code> for windows <br> Below $$\color{red}{\text{Step-2: The script}}$$ <br> $$\color{orange}{\text{Paste}}$$ <code>Ctrl</code> + <code>Shift</code> + <code>V</code> for Linux <br> in your terminal file(portscan.py) | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/39#issue-3957477479) | in your linux terminal <br> **Zoom out:** <code>Ctrl</code> + <code>-</code> <br> **Zoom in:** <code>Ctrl</code> + <code>Shift</code> + <code>+</code> |
  
* $$\color{red}{\text{Step-2: The Script}}$$
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

* $$\color{red}{\text{Step-3: Saving The Script}}$$
  | 9. Exiting from the $$\color{orange}{\text{script}}$$ File. <br> <code>Ctrl + X</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/27#issue-3951318135) | |
  |:---|:---|:---|
  | 10. Saving $$\color{orange}{\text{script}}$$ File Before Exiting. <br> <code>Y</code> Yes| ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/28#issue-3951343868) | |
  | 11. Want to Rename( <code>nano portscan.py</code> ) <br> or name( if not given <code>nano</code> only ). | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/29#issue-3951371192) | If already name it will ask keep it <code>portscan.py</code> or change it. <br> If not named( <code>nano</code> only ) it will ask for to give a name to your script file. |
  | 12. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/30#issue-3951384995) | |

* $$\color{red}{\text{Step-4: Running The Script}}$$
  | 13. <code>python portscan.py</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/31#issue-3951541739) | You are telling your computer, <br> "Use the Python program to read and run <br> the instructions inside the file portscan.py". |
  | :--- | :--- | :--- |
  | 14. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/32#issue-3951563676) | |
  | 15. Enter a remote host to scan: <code>scanme.nmap.org</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/33#issue-3951586007) | # $$\color{orange}{\text{target that we want to scan for open ports if any}}$$ <br> Nmap project provides a specific authorized target |
  | 16. <code>Enter</code> | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/34#issue-3951593865) | you can see <code>scanme.nmap.org</code> provided as with target IP address. <br> $$\color{orange}{\text{wait for few minutes}}$$ |
  | 17. found my first open port | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/35#issue-3951619804) | wait few more minutes for script to end |
  | 18. script Ended | ![View](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/36#issue-3952417083) | After waiting for $$\color{orange}{\text{41 minutes}}$$ Project Done !! |   

# Explanation of The Script

* Importing Tools (Libraries)
  | <code>import socket</code> | Loads the $$\color{orange}{\text{networking}}$$ tool. It allows Python to talk to other computers over the internet (create connections, send data, etc.). |
  | :--- | :--- |
  | <code>import subprocess</code> | Loads the $$\color{orange}{\text{command line}}$$ tool. It allows Python to run shell commands (like clearing the screen) just as if you typed them into the terminal yourself. |
  | <code>import sys</code> | Loads $$\color{orange}{\text{system}}$$ tools. We mainly use this to exit the program cleanly ( <code>sys.exit()</code> ) if an error happens. |
  | <code>from datetime import datetime</code> | Imports a specific tool to handle time. We need this to check the clock before and after the scan to see how long it took. |

* Clearing the Screen  
  | <code>subprocess.call('clear', shell = True)</code> | 1. What it does: It tells the operating system to run the command <code>clear</code> . <br> 2. Example: Imagine your terminal screen is full of old text. This line wipes it clean so your scanner looks professional. <br> 3. Note: <code>clear</code> works on Linux and Mac. On Windows, the command is <code>cls</code>. |
  | :--- | :--- |
  
* Getting User Input & Finding the IP
  | <code>remoteServer = input("Enter a remote host to scan: ")</code> | 1. <code>input(...)</code>: pauses the program and waits for you to type something. <br> 2. Example: You type google.com. The variable remoteServer now holds the text "https://www.google.com/url?sa=E&source=gmail&q=google.com" |
  | :--- | :--- |
  | <code>remoteServerIP = socket.gethostbyname(remoteServer)</code> | 1. <code>socket.gethostbyname(...)</code>: This is the Phonebook lookup. Computers don't know what "https://www.google.com/url?sa=E&source=gmail&q=google.com" is; they only know IP addresses. This line converts the name into an IP address. <br> 2. Example: It turns <code>google.com</code> into <code>142.250.183.46</code>.|

* Printing the "Banner"
  | <code>print("-" * 60)</code> <br> <code>print("Please wait, scanning remote host", remoteServerIP)</code> <br> <code>print("-" * 60)</code> | 1. print("-" * 60): Prints the hyphen character 60 times. It creates a neat horizontal divider line. <br> 2. The result looks like this: <br> ------------------------------------------------------------------ <br> Please wait, scanning remote host (your_remoteServerIP) <br> ------------------------------------------------------------------ |
  | :--- | :--- |

* Starting the Stopwatch
  | <code>t1 = datetime.now()</code> | What it does: It looks at the clock right now and saves that exact time into the variable <code>t1</code>. We will use this later to calculate the total time taken. |
  | :--- | :--- |

* The Main Loop (The Scanner)
  | <code>try:</code> | The $$\color{orange}{\text{safety net.}}$$ It starts a block of code where we expect errors might happen (like the user pressing <code>Ctrl</code> + <code>C</code> ). |
  | :--- | :--- |
  | <code>for port in range(1,5000):</code> | 1. This creates a loop. The variable <code>port</code> will start at 1 and go up to $$\color{orange}{\text{4999}}$$ (Python ranges stop before the last number). <br> 2. Analogy: $$\color{orange}{\text{Go to houses numbered 1 through 4999.}}$$ |
  | <code>sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)</code> | 1. What it does: Creates a new socket (a connection endpoint). <br> 2. <code>AF_INET</code>: Says $$\color{orange}{\text{We are using IPv4}}$$ (standard IP addresses). <br> 3. <code>SOCK_STREAM</code> : Says $$\color{orange}{\text{We are using TCP}}$$ (the reliable protocol used for web browsing). <br> 4. Analogy: You are picking up the phone to make a call. |
  | <code>sock.settimeout(0.5)</code> | What it does: Sets the patience limit to 0.5 seconds. If the server doesn't answer in that time, we give up. |
  | <code>result = sock.connect_ex((remoteServerIP, port))</code> | <code>sock.connect_ex(...)</code>: Tries to connect to the specific IP and Port. <br> Unlike the normal <code>.connect()</code> , this $$\color{orange}{\text{returns a number}}$$ instead of crashing if it fails. <br> Returns <code>0</code> : Success! The port is open. <br> Returns <code>11</code> (or others): Failure. The port is closed or blocked. |
  | <code>if result == 0:</code> | Checks if the connection was successful. |
  | <code>print(...)</code> | If yes, tell the user the port is open.|
  | <code>sock.close()</code> | Hang up the phone. This is $$\color{red}{\text{crucial;}}$$ if you don't close sockets, your computer will run out of resources. |

* Handling Errors (The Safety Nets)
  | <code>except KeyboardInterrupt:</code><br><code>    print("You pressed Ctrl + C")</code><br><code>    sys.exit()</code> | 1. Scenario: You get bored waiting and press <code>Ctrl</code> + <code>C</code> to stop the script. <br> 2. Action: Python catches that signal, prints a message, and exits cleanly instead of showing a scary error trace. |
  | :--- | :--- |
  | <code>except socket.gaierror:</code><br><code>    print("Hostname could not be resolved Exiting")</code><br<code>    sys.exit()</code> | 1. Scenario: You typed a nonsense website name (e.g., <code>sadfjsaldkfjas.com</code> ) that doesn't exist in the DNS phonebook. <br> Action: Prints an error and exits. <code>gaierror</code> stands for $$\color{\text{Get Address Info Error.}}$$ |
  | <code>except socket.error:</code><br><code>    print("Couldn't connect to server")</code><br><code>    sys.exit() | 1. Scenario: The server exists, but it's completely down or refusing to talk to you entirely. <br> 2. Action: Prints an error and exits.

* Finishing Up
  | <code>t2 = datetime.now()</code> | Checks the clock again when the loop finishes. |
  | :--- | :--- |
  | <code>total = t2 - t1</code> | Calculates the difference (End Time - Start Time). |
  | <code>print(...)</code> | Shows you exactly how long the scan took (e.g., <code>Scanning Completed in 0:02:15.402</code> ). |
