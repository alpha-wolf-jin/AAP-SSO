# AAP-SSO

## CONFIGURE RED HAT SSO

```
echo "# AAP-SSO" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/alpha-wolf-jin/AAP-SSO.git
git config --global credential.helper 'cache --timeout 72000'
git push -u origin main

git add . ; git commit -a -m "update README" ; git push -u origin main
```


## Start RED HAT SSO in container

```
[root@aap-eda ~]# podman login  registry.redhat.io
Username: 
Password: 
Login Succeeded!
[root@aap-eda ~]# podman run --detach \
>     -e VIRTUAL_HOST=sso.int.shifti.us \
>     -e VIRTUAL_PROTO=http \
>     -e VIRTUAL_PORT=8080 \
>     -e SSO_HOSTNAME=sso.int.shifti.us \
>     -e SSO_ADMIN_USERNAME=admin \
>     -e SSO_ADMIN_PASSWORD=admin \
>     --hostname sso.int.shifti.us \
>     --publish 8080:8080 \
>     --name rhsso \
>     --restart always \
>     registry.redhat.io/rh-sso-7/sso74-openshift-rhel8
```


## CONFIGURE RED HAT SSO

http://sso.int.shifti.us:8080/auth/admin

You’ll land in the Master realm by default.
![SSO](images/sso-01.png)

Click the **Master** realm name on top left  
![SSO](images/sso-02.png)

click the **Add Realm** buttom from the dropdown menu
Type your new realm name (e.g. “Tower”) and click the **Create** button

![SSO](images/sso-03.png)
