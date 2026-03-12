# V-server setup
## 1. Create public/private key pair 
    use command ssh ssh-keygen -t ed25519

## 2. Login using the IP and credentials provided by DA:
    ssh userName@serverIpAddress
    
## 3. Establish ssh Connection:
    ssh-copy-id -i ~/.ssh/your-key userName@serverIpAddress
    enter the password to V-Server
    press enter button
## 4. Login using the ssh-tunnel
     ssh -i ~/.ssh/your-key userName@serverIpAddress
   
## 5. Remove Password authentication from the Server
    Important!!! recheck if ssh Login works properly before the Password authentication is deactiviert!
    than run the command:
        sudo nano etc/ssh/sshd_config   to open the configuration file
           -> find the commented line: #PasswordAuthentication no
           -> uncomment this line und replace 'yes' with 'no'
           -> save and Exit
## 6. Restart ssh service: 
     sudo systemctl restart ssh.service
    
## 7. Check if password authentication is disabled
    ssh -o PubkeyAuthentication=no userName@serverIpAddress
    expectet result:
        Permission denied (publickey).
        