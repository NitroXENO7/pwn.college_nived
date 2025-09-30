# Description
There is some interesting information hidden around this site http://mercury.picoctf.net:5080/. Can you find it?

# My solve
found first part in html
2nd part was in the mycss.css file
found "How can I keep Google from indexing my website?" in the js file, knew that robots.txt is used to do that and found 3rd part
in robots.txt found that this is a apache server so checked the default hidden files of apache and found 4th part in .htaccess
last it said about doing things in mac and there's a file that generates when done in mac called .DS_Store so found that got 5th part.


`flag: picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_35844447}`
