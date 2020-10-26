# WordPress Setup & Migration using Easy Engine

## Task

Deploy a (or Transfer in an existing) WordPress Site onto an Easy Engine managed machine.

## Resources

[Easy Engine](https://easyengine.io/)<sup>1</sup>

## Process
1. Create a Digital Ocean Droplet 

2. Droplet Settings: 
	* SSH Key
	* Frankfurt 
	* 5$
	* Monitoring

3. SSH into the Droplet  
	`ssh root@IP_ADDR`

4. Download Easy Engine  
	`wget -qO ee rt.cx/ee4 && sudo bash ee `
5. Create Site using command:  
	`ee site create www.DOMAIN.com --type=wp --admin-user=julian --admin-pass=Temporary123 --ssl=le --cache`  
> 	--ssl=le can be removed and enabled later

	> To enable SSL later, run the command:  
	>`ee site update example.com --letsencrypt`
 
## EXISTINIG SITE

1. Navigate to `https://www.DOMAIN.com/wp-admin`
2. **Log in** using: `julian` & `Temporary123`
3. Navigate to **Plugins** 
4. **Add New**
5. Install:
	* All In One WP Migration
	* All In One WP Migration DO Extension (From Mac)
6. Navigate to `All-In-One WP Migration` -> `DO Spaces Settings`
7. Open [`https://cloud.digitalocean.com/account/api/tokens`](https://cloud.digitalocean.com/account/api/tokens)
8. **Generate or Copy** `Key` & `Secret`
9. Fill in
10. Complete Settings: 

	| Region Name       | Frankfurt 1            |
	|-------------------|------------------------|
	| Bucket Name       | wordpress-backups-2020 |
	| Folder Name       | CLIENT                 |
	| Transfer Settings | Fastest                |

11. Click on `Import`
12. Select Correct Folder (as above)
13. Click Proceed
14. Log in with existing credentials
14. Save Permalinks 2x
15. Install Helper Plugins
	* WP Redis (WordPress Object Cache using Redis. | Pantheon)
	* NGINX Helper ( rtCamp) 
	
<br>

## NEW SITE

1. Navigate to `https://www.DOMAIN.com/wp-admin`
2. **Log in** using: `julian` & `Temporary123`
3. Navigate to **Users**
4. Select `julian` and click `edit`
5. Generate `Password`
6. Store in **1Password**
3. Navigate to **Plugins** 
4. **Add New**
5. Install:
	* All In One WP Migration
	* All In One WP Migration DO Extension (From Mac)
6. Navigate to `All-In-One WP Migration` -> `DO Spaces Settings`
7. Open [`https://cloud.digitalocean.com/account/api/tokens`](https://cloud.digitalocean.com/account/api/tokens)
8. **Generate or Copy** `Key` & `Secret`
9. Fill in
10. Complete Settings: 

	| Region Name       | Frankfurt 1            |
	|-------------------|------------------------|
	| Bucket Name       | wordpress-backups-2020 |
	| Folder Name       | CLIENT                 |
	| Transfer Settings | Fastest                |

15. Ensure Helper Plugins Installed
	* WP Redis (WordPress Object Cache using Redis. | Pantheon)
	* NGINX Helper (rtCamp)

		### 	**OPTIONALLY**

16. Download **Divi** from [here](https://www.elegantthemes.com/members-area/index.php).
17. Upload **Divi** 
18. Add **`API Key`** from [`Account/Username & API Keys`](https://www.elegantthemes.com/members-area/api/)
19. Start Building :)

<br>
<br>
**Last Updated:** 30.03.2020  
**Created:** 30.03.2020

<br>
<hr>
<sup>1</sup> https://easyengine.io/


	