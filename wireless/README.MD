#aircrack-ng

aircrack-ng -a2 -b [Target BSSID] -w /home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap'
-a is the technique used to crack the handshake, 2=WPA technique.
-b refers to bssid; replace with the BSSID of the target router.
-w stands for wordlist; provide the path to a wordlist.
