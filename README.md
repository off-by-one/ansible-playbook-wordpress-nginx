# WordPress + Nginx Ansible Playbook
Ansible playbook and roles for installing WordPress + Nginx + PHP

The changes in this fork feature an updated mySQL config, with no need to set
the root password. It also uses the more recent PHP 8.2, and by default assumes
it is running on a host pointed to by a URL from which it can fetch certbot
certificates.

### Requirements
- Ansible 2.0.0 or newer
- Ubuntu 22.04 (installed on your web server or virtual machine)

### Instructions:

### 1. Configure your web server for ssh

Allow connections from your development machine to the web server over ssh. This is essential for ansible to work, so make sure to configure your remote or local server to allow connections via ssh. You may find `ssh-copy-id` helpful. 

### 2. Clone the repository

```
$ git clone https://github.com/off-by-one/ansible-wordpress-nginx-playbook.git
$ cd /wordpress-nginx
```

### 3. Set the required values

Change the contents of `inventory.ini` to the URL of your website.

Modify `playbook.yml`:
  * Change `hosts: example.com` to `hosts: YOURWEBSITE.URL`
  * Insert your password or ansible-vault fetch into `    wp_db_password: "CHANGEME"`
  * Insert your sysadmin email into `    certbot_email: "CHANGEME"`


### 4. Run the playbook

```
$ ansible-playbook playbook.yml
```

### 5. Finish the install

Open your web browser and navigate to your hostname to complete the wordpress installation.
