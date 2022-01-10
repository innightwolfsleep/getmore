# getmore
getmore is GEt Managed Object Regular Expressions (desined for E/// OSS)

extended help: getmore h 

regular syntax help: getmore r 

usage: getmore [Subnet1:]<MOtype1>[=MOfilter1](,...) <Attribute1>[=Value1](,...) [key] [fileDirectory]
      
where: <> is mandatory value, [] is optional value, () is optional repeat
      
Script parsing data from BCGtool,CNAI,BSM,BSM_HARDWARE; check data and output to terminal or file. Use standart OSS tools. 
      
--- Subnet - list of subnetworks (BSC/RNC/eNodeBarea/IPRANarea). Case-sensitive.
      
Recommended to use subnet filter for faster response. Accelerate working
      
--- MOtype - full name of parsed MO (UtranCell, IPInterface,ExternalGsmCell,icell,RXOTG...).
      
--- MOfilter - regular expression filters for MO name values. 
      
--- Attribute - regular expression filter for attribute name. "all" reserved for output all attributes.
      
--- Value - regular expression filter for attributes value. Use logical "and" between filters. Dont accelerate working.
      
"band=1800,dchno=600" mean that only MO with band=1800 and dchno=600 will be printed. Exist reverse mode, where use negative comparsion (only MO where band not equal 1800 and dchno not equal 600 will be printed).
      
--- fileDirectory - directory, where result file will be saved. By default file saved to current user directory. Use with "f" key.
keys: "f" will save result to file.
      
"r" reverse attribute value comparison mode. It is mean, will be printed only MO where attribute value not equal to input value.
      
"R" reverse MOfilter comparison mode. It is mean, will be printed only MO with name not equal to MOfilter.
      
"b" will not ignore case in regular expression.
      
"p" will switch off printing result to terminal.
      
"v" verbose information mode, show additional info.

"m" mute mode, output only result.  
      
"c" CSV mode, output with ";" as delimeter.  
      
"n" attribute name mode, each printed attribute value have attrbute name.
      
1 example: getmore RNCE-SPB031:UtranCell,RNCE-SPB032:UtranCell qRxLevMin,maximumTransmissionPower,lac,cId,uarfcnUl,uarfcnDl,primaryScramblingCode s
will get seven parameters from all UtranCell in RNCE-SPB031 and RNCE-SPB032, strong mode.

2 example: getmore IPInterface primaryIP_Address,primarySubNetMask ps
will get mask and IPaddress from all interfaces in all TCU, strongmode without terminal printout.

3 example: getmore ExternalGsmCell lac,bcc,ncc,bcchFrequency,cellIdentity 
will get lac,ncc,bcc,cId from ExternalGsmCell in OSS, .

4 example: getmore M3uAssociation=iur remote nf
will get remoteIpAddress1,remoteIpAddress1,remotePortNumber from M3uAssociation with name, contained "iur" in OSS without attribute caption with file output.

5 example: getmore EKT328:icell BCCHNO,BCC,NCC,LAC,CI
will get all BCCHNO,BCC,NCC,LAC,CI from all GSM internal cell on EKT328.
      
6 example: getmore chgr band=1800,dchno
will get DCHNO for CHGR with BAND=1800 in OSS.
      
7 example: getmore hardware type=mctr,mo=665
will find hardware data for MCTR in TG=665
      
8 example: getmore RXOTG scgr,site,swveract,cell,chgr
will find data about RXOTG, including connected cell and software
      
9 example: getmore SCGR mode,scgrss.scgr,pstuname
will get info about SCGR
      
10 example: getmore TCU02:ARNE ipAddress
will get info about OaM ipaddress from all TCU
