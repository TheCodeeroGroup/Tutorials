# Enabling SFTP on Easy Engine v4

## Task
Enable SFTP access to WordPress Files on an EE installed server.

## Resources

[Easy Engine SFTP Tutorial](https://easyengine.io/docs/chroot-sftp-easyengine/)<sup>1</sup>

[Support Forum Post PWD Authtentication](https://community.easyengine.io/t/sftp-no-supported-authentication-methods-available-server-sent-publickey/7711/3) <sup>2</sup>

## Process

1. SSH as root user, or user with root permissions.
2. Create `ee-user` User:
	3. 	`useradd -G www-data -ms /bin/false ee-user`
	4. `passwd ee-user`
5. Create Home Directory for new User:
	6. `mkdir -p /home/ee-user/SITENAME/htdocs`
7. Set up correct permissions:
	8. `chown ee-user:www-data /home/ee-user/example.com `
	9. `chown root:root /home/ee-user/`
	10. `chown root:root /home/`
11. Nano `/etc/ssh/sshd_config` file:
	12. Find `Subsystem sftp /usr/lib/openssh/sftp-server`
	13. Replace with `Subsystem sftp internal-sftp`
	14. Add at the end of file: 

		``` Match group www-data 
		X11Forwarding no 
		ChrootDirectory %h 
		AllowTcpForwarding no 
		ForceCommand internal-sftp```  
		
15. Restart SSH service using `service ssh restart`
16. Set correct permissions on web root 
> **NOTE**: This is docker in v4, so `/opt/easyengine/sites/SITENAME/app/htdocs ` 
	17. ` chmod g+s /opt/easyengine/sites/SITENAME/app/htdocs -R`
	18. ` chmod 775 /opt/easyengine/sites/SITENAME/app/htdocs -R`
19. Mount the web root:
	20. `mount --bind /opt/easyengine/sites/SITENAME/app/htdocs /home/ee-user/SITENAME/htdocs`
	21. *OPTIONALLY* Add to end of file: `/etc/rc.local`
22. Enable Password Auth for `ee-user` user:
	23. Edit (nano) into `/etc/ssh/sshd_config`
	24. Change `PasswordAuthentication` to `yes`  
		Final line should look like this: `PasswordAuthentication yes`
	25. Restart SSH using `service ssh restart`
26. **SFTP** using **FileZilla** or other client.  
<br>
<br>
**Last Updated:** 30.03.2020  
**Created:** 28.03.2020

<br>
<hr>
<sup>1</sup> https://easyengine.io/docs/chroot-sftp-easyengine/  
<sup>2</sup> https://community.easyengine.io/t/sftp-no-supported-authentication-methods-available-server-sent-publickey/7711/3