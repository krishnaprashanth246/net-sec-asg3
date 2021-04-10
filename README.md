# Network Security Assignment 3

## Team
    G Vishal Siva Kumar     CS18BTECH11013
    P V Asish               CS18BTECH11037
    T Krishna Prashanth     CS18BTECH11045
----

## Files
    README.md                   # this file
    secure_chat_app             # Original app
    secure_chat_interceptor     # Trudy's program
    dump1.pcap                  # tcpdump for task 1
    dump2a-bob.pcap             # tcpdump for task 2
    keylog-2a                   # SSL Key Log file for decrypting dump2a-bob.pcap
    dump3-trudy.pcap            # tcpdump for task 3
    dump4-trudy.pcap            # tcpdump for task 4
    Report.pdf                  
    alice/alice.csr
    alice/alice-key.pem         # Alice's key file
    alice/alice.crt             # Certificate issued to Alice by rootCA
    bob/bob-key.pem             # Bob's key file
    bob/bob.csr                 
    bob/bob.crt                 # Certificate issued to Bob by rootCA
    rootca/root.crt             # Root CA's self issued certificate
    root/root-privatekey.pem    # RootCA's key file
    trudy/fakealice.csr         # trudy's fake files
    trudy/fakealice.crt         # .
    trudy/fakealice-key.pem     # .
    trudy/fakebob.csr           # .
    trudy/fakebob.crt           # .
    trudy/fakebob-key.pem       # .
    
----

## How to run

#### <ins>Task 2</ins> :

    Bob's container : To run secure_chat_app
            $ ./secure_chat_app -s 
    Alice's container :  To run secure_chat_app
            $ ./secure_chat_app -c bob1
    
#### <ins>Task 3</ins> :

##### Host VM :

    Running poison file to change the dest ip of Alice msgs in host VM
            $ bash ~/poison-dns-alice1-bob1.sh
    To unpoison
            $ bash ~/unpoison-dns-alice1-bob1.sh

##### Trudy's container : 
    Eavesdropping messages 
            $ ./secure_chat_interceptor -d alice1 bob1
##### Bob's container : 
    To run secure_chat_app
            $ ./secure_chat_app -s
##### Alice's container :
    To run secure_chat_app
            $ ./secure_chat_app -c bob1
            
#### <ins>Task 4</ins> :

##### Host VM :  

    Running poison file to change the dest ip of Alice msgs in host VM
            $ bash ~/poison-dns-alice1-bob1.sh
    To unpoison
            $ bash ~/unpoison-dns-alice1-bob1.sh

##### Trudy's container : 
    Eavesdropping messages 
            $ ./secure_chat_interceptor -m alice1 bob1
##### Bob's container : 
    To run secure_chat_app
            $ ./secure_chat_app -s
##### Alice's container :
    To run secure_chat_app
            $ ./secure_chat_app -c bob1
---
            
## Message exchange

*  In any task, after establishment of connection, either alice or bob can send messages whose input is taken from the standard input.
* Received messages are directly printed onto the standard output with client/server label.
* Trudy gets the messages along with sender's labels.
