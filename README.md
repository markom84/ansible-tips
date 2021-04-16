# ansible-tips
Tips and tricks for ansible 


**ansible 'appservers:&aws' -m ping**   => Performs ping module on server belonging in appservers and aws groups (cross-section)

**ansible 'appservers:&aws' -m ping --check** => Dry run, only shows what will happen, without actually performing tasks

--check = dry run 
--list-hosts = only list hosts
 ansible-playbook --limit '!ogpay-prod.softmetrixgroup.com:!adxpay*' add_line_catalina.yaml --check


Multiple groups	
webservers:dbservers - all hosts in webservers plus all hosts in dbservers

Excluding groups	
webservers:!atlanta - all hosts in webservers except those in atlanta

Intersection of groups	
webservers:&staging - any hosts in webservers that are also in staging


# Run ansible on Windows client

[Complete guide](https://www.thomaspreischl.de/manage-windows-with-ansible-pt1/)

**On linux install:**

```
sudo apt-get install libkrb5-dev
pip install pywinrm
pip install pywinrm[kerberos]
```

**/etc/ansible/hosts**:

```
[windows]
10.3.4.179 ansible_python_interpreter=/usr/bin/python3 ansible_connection=winrm ansible_user=usersible_password=password ansible_port=5986 ansible_winrm_server_cert_validation=ignore
```


**On Windows in powershell run:**
```
$url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
$file = "$env:temp\ConfigureRemotingForAnsible.ps1"
(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
powershell.exe -ExecutionPolicy ByPass -File $file
```
