# Directions

## Ensure you have a RHEL subscription available
- You can use a 30 Day Red Hat Enterprise Linux Server Self-Supported Evaluation available [here](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/try-it)

## Prepare your environment
**These steps are mandatory**

- Install a RHEL 7.8 system
- If you are using a RHEL on a public cloud provider make sure you disable the RHUI first
```
sudo yum -y remove rh-amazon-rhui-client* rhui-azure-rhel* google-rhui-client-rhel*
sudo bash -c 'cat << EOF > /etc/yum/pluginconf.d/product-id.conf
[main]
enabled=1
EOF'
```
- Register it with subscription-manager
```
sudo subscription-manager register --auto-attach
```
- Enable required repositories
```
sudo subscription-manager repos --enable rhel-7-server-rpms --enable rhel-7-server-extras-rpms
```
- Install LEAPP graphical toolkit (leapp + web console)
```
sudo yum -y install leapp leapp-repository cockpit cockpit-leapp
```
- Enable the web console
```
- sudo systemctl enable --now cockpit.socket
```
- Fix permissions to allow reports display in the Web Console
```
sudo chown root:adm /var/log/leapp && chmod 750 /var/log/leapp
```
- Download repo mapping and rpm change files
```
sudo curl -o /etc/leapp/files/pes-events.json https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_09/leapp-data8/pes-events.json
sudo curl -o /etc/leapp/files/repomap.csv https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_09/leapp-data8/repomap.csv
```
- Reboot your system
```
sudo reboot
```

## Ensure your system is ready

- Reach your system with a web browser on the :9090 HTTPS port
*Example : https://1.2.3.4:9090*
- Log in with the handson user in privileged mode
**Check *Reuse my password for privileged tasks* on the login page**
- Make sure the **In-Place Upgrade Report** tab is visible on the left

## Follow the hands-on during the Webinar

- Watch the webinar and start the manipulations when I prompt you to do so.


## Send feedback :)

If you enjoyed this virtual hands-on, feel free to send feedback !
(contact information is displayed at the end of the webinar)
