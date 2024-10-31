

**Remote Browsing**



​    :e [protocol]://[user]@hostname/path/ 

​    :Nread [protocol]://[user]@hostname/path/ 



​	--



​    :e dav://machine[:port]/path           uses cadaver 

​    :e fetch://[user@]machine/path         uses fetch 

​    :e ftp://[user@]machine[[:#]port]/path     uses ftp  autodetects <.netrc> 

​    :e http://[user@]machine/path          uses http uses wget 

​    :e rcp://[user@]machine/path         	uses rcp 

​    :e rsync://[user@]machine[:port]/path   	uses rsync 

​    :e scp://[user@]machine[[:#]port]/path    uses scp 

​    :e sftp://[user@]machine/path          uses sftp 



**Remote Reading**



​    :Nread ?                         	give help 

​    :Nread "machine:path"               	uses rcp 

​    :Nread "machine path"               	uses ftp  with <.netrc> 

​    :Nread "machine id password path"       uses ftp 

​    :Nread "dav://machine[:port]/path"        uses cadaver 

​    :Nread "fetch://[user@]machine/path"      uses fetch 

​    :Nread "ftp://[user@]machine[[:#]port]/path"  uses ftp  autodetects <.netrc> 

​    :Nread "http://[user@]machine/path"       uses http uses wget 

​    :Nread "rcp://[user@]machine/path"      	uses rcp 

​    :Nread "rsync://[user@]machine[:port]/path"  uses rsync 

​    :Nread "scp://[user@]machine[[:#]port]/path" uses scp 

​    :Nread "sftp://[user@]machine/path"     	uses sftp 



**REMOTE WRITING** 



​    :Nwrite ?                           give help 

​    :Nwrite "machine:path"                 uses rcp 

​    :Nwrite "machine path"                 uses ftp  with <.netrc> 

​    :Nwrite "machine id password path"      	uses ftp 

​    :Nwrite "dav://machine[:port]/path"         uses cadaver 

​    :Nwrite "ftp://[user@]machine[[:#]port]/path" 	uses ftp  autodetects <.netrc> 

​    :Nwrite "rcp://[user@]machine/path"        uses rcp 

​    :Nwrite "rsync://[user@]machine[:port]/path"  uses rsync 

​    :Nwrite "scp://[user@]machine[[:#]port]/path"  uses scp 

​    :Nwrite "sftp://[user@]machine/path"      	uses sftp 

​    http: not supported! 



