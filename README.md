# ansible-tips
Tips and tricks for ansible 

Filtering hosts:
ansible 'appservers:&aws' -m ping => Performs ping module on server belonging in appservers and aws groups (cross-section)

ansible 'appservers:&aws' -m ping --check => Dry run, only shows what will happen, without actually performing tasks

