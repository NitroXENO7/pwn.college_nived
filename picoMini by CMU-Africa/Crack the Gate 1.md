# Description
We’re in the middle of an investigation. One of our persons of interest, ctf player, is believed to be hiding sensitive data inside a restricted web portal. We’ve uncovered the email address he uses to log in: ctf-player@picoctf.org. Unfortunately, we don’t know the password, and the usual guessing techniques haven’t worked. But something feels off... it’s almost like the developer left a secret way in. Can you figure it out? The website is running here. Can you try to log in?

# Solve

Checked the html saw a ciphered text, looked like rot13 , after rot13 got ` NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes" ` used burpsuite to add the header and send the post request. got the flag.

Flag : `picoCTF{brut4_f0rc4_125f752d}`
