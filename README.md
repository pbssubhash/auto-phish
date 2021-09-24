# Auto Phish

If you are a red teamer, you know Phishing is a very crucial and productive part of owning your target and you also known, it's a bit tideous process to setup various moving parts that are required for a phishing exercise. AutoPhish is intended for those time-concious, lazy and automation loving red teamers who wish to setup their phishing environment within 5-10 minutes.

## What does it do under the hood?
It just combines the following and frees you from boring `ctrl`+`c` and `ctrl`+`v`.
  1. It uses [iRedMail](https://www.iredmail.org/) for mailing infrastructure
  2. [GoPhish](https://getgophish.com/) for the phishing infrastructure
  3. LetsEncrypt for SSL certificates.

## Get Started

1. Edit `inventory.txt` with your red team server details.
  - Replace XXX.XXX.XXX.XXX with your server IP 
  - Replace SSH_Password with your real ssh password
```
[phishing_server]
XXX.XXX.XXX.XXX ansible_server=XXX.XXX.XXX.XXX ansible_connection=ssh ansible_user=root ansible_ssh_pass="SSH_PASSWORD"
```
P.S. Check [Ansible SSH Connection Options](https://docs.ansible.com/ansible/latest/user_guide/connection_details.html) for more information on how to use SSH keys, etc.

2.  Install ansible on your machine
    Ansible has a neat documentation about the same. [Please check here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
    
3. Run the playbook
Playbook can be executed using the following command (Don't forget to edit the below command):
```
ansible-playbook -i inventory.txt playbook.yaml --extra-vars="{'le_email':'admin@phishingdomain.com','le_domain':'phishingdomain.com','postmaster_password':'SuperGreatPassword'}"
```

Once executed, it'll setup iRedMail, GoPhish along with all required SSL certificates.

### Helpful links:
1. Creating more users in the mailing infrastructure: https://computingforgeeks.com/add-domain-and-user-account-on-iredmail-mail-server/
2. GoPhish Tutorial: https://www.youtube.com/watch?v=S6S5JF6Gou0

### Disclaimer: 
Built for educational purposes only. Author isn't responsible for any sort of misuse associated with the script. 
