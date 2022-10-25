# Lidl-SilverCrest-Zigbee-Gateway-TYGWZ-01-Root-and-Update-Notes-2022
This is a repo with updated instructions for 2022 in a single spot to root, add serial and update EZSP on your Lidl/Silvercrest zigbee gateway

<h2>Retrieve Root Password</h2>
Root instructions in - https://paulbanks.org/projects/lidl-zigbee/root/ by Paul Banks<br>
Instructions on how to remove cloud garbage - https://paulbanks.org/projects/lidl-zigbee/ha/ by Paul Banks<br>
Pictures and some instructions in - https://zigbee.blakadder.com/Lidl_TYGWZ-01.html as well<br>
<br>

Note: to decode the Root password I used <a href="https://paulbanks.org/download/files/lidl-zigbee/lidl_auskey_decode.py">lidl_auskey_decode.py</a> from Pauls website instead of the one from blakadder/git repo(did not work for me) 

<h2>To upgrade the EZSP Version to 6.7.8.0</h2>
1. get this firmware on your linux PC/VM https://github.com/grobasoz/zigbee-firmware/raw/master/EFR32%20Series%201/EFR32MG1B-256k/NCP/NCP_UHW_MG1B232_678_PA0-PA1-PB11_PA5-PA4.gbl <br>
2. Get this script on your linux PC/VM https://github.com/banksy-git/lidl-gateway-freedom/blob/master/scripts/upgrade_ncp.py <br>
3. Connect to Lidl box via SSH <br>
4. Run <code>killall serialgateway</code> on Lidl Box<br>
5. Run <code>/tuya/serialgateway -p 8888 -f</code> on Lidl Box and leave console open<br>
6. On your PC/VM if you dont have bellows installed run <code>pip3 install bellows</code><br>
7. Then <code>bellows -d socket://192.168.1.200:8888 bootloader</code> (dont forget to change IP to your Lidl BOX IP).<br>
8. Then on your PC/VM run <code>python3 upgrade_ncp.py --port 8888 192.168.1.200 NCP_UHW_MG1B232_678_PA0-PA1-PB11_PA5-PA4.gbl</code> (dont forget to change IP to your Lidl BOX IP).<br>

Hope this makes sense/helps someone like me.<br><br>

Have a good day

Note: Thanks to git user challs for the EZSP update sequence.
