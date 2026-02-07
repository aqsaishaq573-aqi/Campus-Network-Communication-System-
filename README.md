🌐 Campus Network Communication System
🎯 Project Overview

The Campus Network Communication System is a client-server application that simulates inter-campus communication for a multi-campus university network using TCP and UDP protocols.

This project implements a distributed messaging system that connects multiple university campuses through a central server. The system enables:

Authenticated campus-to-campus communication

Real-time status monitoring using heartbeats

University-wide broadcast announcements

The project is designed as part of a Computer Networks Lab and demonstrates practical use of socket programming, multithreading, and networking protocols.

🏫 Supported Campuses

Lahore

Karachi

Peshawar

CFD (City Campus)

Multan

Islamabad

✨ Features
🔹 Client Features

Campus Authentication – Secure login using campus-specific credentials

Inter-Campus Messaging – Send messages to specific departments of other campuses

Real-time Message Reception – Instantly receive messages from other campuses

Heartbeat Monitoring – Automatic status updates sent every 10 seconds

Broadcast Announcements – Receive university-wide announcements

Multi-threaded Architecture – Concurrent handling of messaging, heartbeats, and announcements

🔹 Server Features

Multi-Client Support – Handles multiple campus connections simultaneously

Authentication System – Verifies campus credentials before access

Message Routing – Routes messages between authenticated campuses

Heartbeat Tracking – Monitors campus connection status in real time

Admin Console – Interactive console for server monitoring and management

Broadcast System – Sends announcements to all connected campuses

Connection Logging – Logs authentication attempts and message routing

🏗️ System Architecture

The system follows a client-server architecture:

🔸 Server (Central Hub)

TCP Server (Port 9000) – Client authentication & message routing

UDP Server (Port 9001) – Heartbeat reception

Admin Console – Status monitoring & broadcast messaging

🔸 Client (Campus Terminal)

Thread 1 – TCP listener for incoming messages

Thread 2 – UDP heartbeat sender (every 10 seconds)

Thread 3 – UDP announcement listener

Main Thread – User interface and message sending

┌─────────────┐     TCP/UDP      ┌──────────────┐     TCP/UDP      ┌─────────────┐
│   Campus    │ ◄─────────────► │    Central   │ ◄─────────────► │   Campus    │
│   Client    │                 │    Server    │                 │   Client    │
│  (Lahore)   │                 │              │                 │  (Karachi)  │
└─────────────┘                 └──────────────┘                 └─────────────┘
                                        ▲
                                        │
                                 ┌──────┴───────┐
                                 │ Admin Console│
                                 └──────────────┘

💻 Technologies Used

Language: C++11

Networking: POSIX Sockets (BSD sockets)

Threading: C++ Standard Library (<thread>)

Protocols:

TCP → Messaging & authentication

UDP → Heartbeats & broadcast announcements

Compiler: g++

Simulation Tool: Cisco Packet Tracer

📁 Project Structure
CN_Lab_Project/
│
├── server.cpp                      # Central server implementation
├── client.cpp                      # Campus client implementation
├── CN Lab Project Topology.pkt     # Cisco Packet Tracer topology
├── CN Lab Project.pdf              # Project documentation
└── README.md                       # Project README

🚀 Installation
🔧 Prerequisites

Linux / Unix environment (Ubuntu, Fedora, macOS, or WSL)

g++ compiler with C++11 support

POSIX-compliant operating system

🛠️ Compilation

Clone the repository:

git clone <repository-url>
cd CN_Lab_Project


Compile the server:

g++ -std=c++11 -pthread server.cpp -o server


Compile the client:

g++ -std=c++11 -pthread client.cpp -o client

📖 Usage
▶️ Running the Server
./server


Server output:

======================================
  SERVER STARTED
  TCP Port: 9000
  UDP Port: 9001
======================================

[UDP] Listening for heartbeats on port 9001
[ADMIN] Commands: status | announce <text> | exit

🧑‍💼 Admin Commands

status → View connection status of all campuses

announce <message> → Send broadcast message

exit → Exit admin console (server continues running)

▶️ Running a Client
./client


Enter campus name:

Enter Campus Name (Lahore/Karachi/Peshawar/CFD/Multan/Islamabad): Lahore


Successful authentication:

[CONNECTED] to server at 127.0.0.1:9000
[AUTHENTICATED] Welcome Lahore!


Menu:

===== Lahore Campus Menu =====
1. Send Message to Another Campus
2. Logout and Exit

✉️ Messaging Example
Lahore → Karachi
Target Campus: Karachi
Target Department: IT Department
Your Message: Server maintenance scheduled for tonight


Karachi receives:

[NEW MESSAGE] [From Lahore - IT Department] Server maintenance scheduled for tonight

🌐 Network Topology

The included Cisco Packet Tracer (.pkt) file demonstrates:

Campus network configuration

Routers and switches

IP addressing scheme

Server placement

Inter-campus connectivity

Open the .pkt file in Cisco Packet Tracer to simulate the network.

🔐 Campus Authentication
Campus	Password
Lahore	NU-LHR-123
Karachi	NU-KHI-123
Peshawar	NU-PSH-123
CFD	NU-CFD-123
Multan	NU-MTN-123
Islamabad	NU-ISB-123

⚠️ Credentials are hardcoded for demonstration purposes only.

📡 Protocol Details
🔹 TCP (Port 9000)

Purpose: Authentication & reliable messaging
Formats:

Authentication: Campus:<name>;Pass:<password>;
Message: FROM:<source>;TO:<destination>;DEPT:<department>;MSG:<text>
Logout: LOGOUT;

🔹 UDP (Port 9001)

Purpose: Heartbeats & broadcasts

Heartbeat: HEART|Campus:<name>|TS:<timestamp>
Broadcast: ANNOUNCEMENT:<message>


Heartbeat Interval: Every 10 seconds

🛠️ Troubleshooting
Common Issues

Cannot bind to port

Ensure ports 9000 and 9001 are free

Cannot connect to server

Verify server is running

Check IP address in client.cpp

Ensure firewall allows connections

Authentication fails

Campus name is case-sensitive

Verify correct password

Messages not received

Ensure both campuses are authenticated

Check server logs

🔮 Future Enhancements

Database-based authentication

Encrypted communication (TLS/SSL)

File transfer support

Web-based admin dashboard

Message history & persistence

Group messaging

Mobile clients

📄 License

This project is developed for educational purposes as part of a Computer Networks Lab assignment.

👥 Team Members

23F-0734

23F-0839

23F-0807

🙏 Acknowledgments

Course instructor for guidance

Team members for collaboration

POSIX socket programming references

C++ threading documentation
