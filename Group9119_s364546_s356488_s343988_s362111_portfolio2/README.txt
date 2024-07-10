DATA2410 Reliable Transport Protocol (DRTP):

This Python application is a simple implementation of the DATA2410 Reliable Transport Protocol (DRTP) over UDP. This protocol is designed to ensure reliable, in-order delivery of data without any missing pieces or duplicates.

Overview
The DRTP application can be run in two modes: as a server or as a client. The server waits for incoming connections and handles incoming data, while the client sends data to a specified server.

The application supports three different reliable transport methods:

Stop-and-wait: The sender sends one packet and waits for an acknowledgement from the receiver before sending the next packet.

Go-Back-N (gbn): The sender sends multiple packets without waiting for acknowledgements, but if a packet is lost, all packets sent after the lost one are resent.

Selective Repeat (sr): The sender sends multiple packets without waiting for acknowledgements, but if a packet is lost, only the lost packet is resent.

The application also supports optional test cases to simulate packet loss, skipped acknowledgements, or duplicate packets.

Requirements:
Python 3.11 or later
Standard Python libraries: argparse, socket, os

Usage:
To run the DRTP application, use the following command:

	# python application.py [arguments]

Here are the arguments you can use:

-s or --server: Run as a server.
-c or --client: Run as a client.
-i or --ip: The server's IP address. This is required.
-p or --port: The server's port number. This is required.
-f or --file: The file to transfer. This is required when running as a client.
-r or --reliable: The reliable transport method to use. This is required and must be one of stop_and_wait, gbn, or sr.
-t or --test: The test case to simulate. This is optional and can be one of lose, skip_ack, double, or None.

Here is an example of how to run the application as a server:

	# python application.py -s -i 192.168.1.2 -p 12345 -r stop_and_wait

And here is an example of how to run the application as a client:

	# python application.py -c -i 192.168.1.2 -p 12345 -f mydata.txt -r stop_and_wait

Please note that the 'lose' test case can only be used with the client and the 'skip_ack' test case can only be used with the server.

Troubleshooting
If you get an error about an invalid reliable method or test case, make sure you are using one of the valid options.

If you are running as a server and specify a file, you will get an error because the server does not need to specify a file.

If you are running as a client and do not specify a file, you will get an error because the client needs a file to send.

For any other issues, please check your network connection and make sure the server is running before you try to connect as a client.
