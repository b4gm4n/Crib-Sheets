## Windows shortcuts

File Explorer

Shirt + F10  - Right click menu  
Ctrl + L to select address bar  
Users startup folder

`shell:startup`

Public Startup folder

`shell:Common Startup`

## Other useful
`shell:Profile`

`shell:PrintersFolder` - Control Panel > Printers

`shell:ProgramFiles`

- comprehensive [list](https://ss64.com/nt/shell.html) 


## Windows commands

Network
    `nslookup -type=mx mydomain.com`  
    `nslookup -type=txt mydomain.com`  
    `getmac /v`  
    `netsh wlan show wlanreport`  
    `netsh interface show interface`  
    `netsh interface ip show address | findstr “IP Address” `  
    `netsh interface ip show dnsservers`  
    `netsh advfirewall set allprofiles state off`  
    `netsh advfirewall set allprofiles state on`  
    `tracert mydomain.com` ~ -d to not resolve hostnames and speedup  
    `netstat`  
    `netstat -af`  
    `netstat -o` ~ which process is using the port  
    `route print` and `route add` and `route delete` to create defind routes  

### Windows system  
Run as administrator  
    `Powercfg /energy`  
    return html e.g. C:\Windows\system32\energy-report.html paste on commanf line to open default browser.  
    `powercfg /betteryreport`  
    Was not working for me, could not change or when change list not updated, need more testing  
        `assoc | clip`  
        `assoc .pdf=AcroExch.Document.DC`  
    `tasklist | findstr $string_to_search`  
    `taskkill /f /kill $pid`  
    `shutdown /r /fw /f /t 0` ~ /r restart /fw go into bios /t time out  


### System file checker

    `sfc /scannow` ~ will probably not fix anything until below dism is run to update the system image files.
Deployment Image Servicing and Management tool
    `dism /online /cleanup-image /checkhealth` ~ will check image for issues
    `dism /online /cleanup-image /scanhealth` ~ deeper scan
    `dism /online /cleanup-image /restorehealth` ~ yep restores it
    if image files cannot be used create iso download with windows media creation tool and run below example
    `dism /online /cleanup-image /restorehealth /source:e:\source\install.esd /limitaccess`
