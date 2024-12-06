# Ldapuser

Simple shell script to manage posixUser accounts in OpenLDAP.

To get started change the DOMDN to match with your domain. By default the user OU is people and group OU is group. These can be modified by changing PEOPLEDN and GROUPDN.

Execute ldapuser help
> Usage: ldapuser [cmd]
> 
> where cmd is
> 
> help               This help
> addgroup           Add group to LDAP (requires LDAP admin password)
> adduser            Add user to LDAP (requires LDAP admin password)
> addusergroup       Add user to group in LDAP (requires LDAP admin password)
> chsh               Change login shell
> delgroup           Delete group from LDAP (requires LDAP admin password)
> deluser            Delete user from LDAP (requires LDAP admin password)
> delusergroup       Remove user from group in LDAP (requires LDAP admin password)
> fullname           Change fullname
> passwd             Change password

## Add user

Add user will create SSHA passwords generated with help of openssl
> salt=`head -c 4 /dev/random`
> ssha=`echo -n "${np1}${salt}" | openssl dgst -binary -sha1`
> encpw=`echo -n "${ssha}${salt}" | openssl enc -base64`

