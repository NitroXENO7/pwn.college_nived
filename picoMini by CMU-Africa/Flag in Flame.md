# Description
The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log. Download the encoded data here: Logs Data. Be prepared—the file is large, and examining it thoroughly is crucial .

# Solve
Checked log file, seems very b64, after decoding saw a file with header png , saved as png saw a code in it, recognized as charcode, converted to get flag.


Flag : `picoCTF{forensics_analysis_is_amazing_2561a194}`
