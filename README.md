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
