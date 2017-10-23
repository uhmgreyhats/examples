# File Extensions Cheatsheet

|Extension|Description|Useful Tools|Example Commands|
|---	|---	|---	|---	|
|.py<br>.pyc<br>.pyo|Python Language File|uncompyle|python *.py|
|.tar.gz<br>.tgz||tar|tar -xvf *.tar.gz|
|.zip<br>.gzip||(g)unzip|unzip *.zip<br>gunzip *.gzip|
|.png<br>.jp(e)g|Imagex   File|pnginfo<br>jpeginfo<br>exifprobe<br>Digital Ink Toolkit<br>Stegsolve|pnginfo *.png<br>jpeginfo -cCi *.jp(e)g<br>exifprobe *.png|
|.pcap<br>.pcapng|Network Traffic File|aircrack-ng<br>pcapfix<br>tcpflow<br>Wireshark||
|.js|||node *.js|
|.git||git<br>[rip-git](https://github.com/kost/dvcs-ripper/blob/master/rip-git.pl)|git log|
|.sh||edb<br>gdb<br>ida<br>ltrace<br>strace||
|.jar|Essentially zip files for java|jar<br>java|`mv *.jar *.jar.zip && unzip *.jar.zip`<br>`java -jar *.jar`
|.pem||openssl|`openssl rsa -in *.pem -pubin -text -modulus`
|.enc|Some encoded file|||
|.nes|Emulated Rom File|bsnes||
|.mp3|Audio File|Audacity||
|.bin|Binary File|xxd|xxd *.bin > output.txt (Converts the .bin file to a hex format)|
