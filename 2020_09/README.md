# [Webinar link](https://www.redhat.com/fr/events/webinar/red-hat-enterprise-linux-tout-savoir-sur-les-montees-de-version-2020)

# Directions

## Ensure you have a RHEL subscription available
- You can use a 30 Day Red Hat Enterprise Linux Server Self-Supported Evaluation available [here](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/try-it)

## Prepare your environment
### Installation
**These steps are mandatory**

- Install a RHEL 7.8 system
> For reference, I will be using the following AMI on AWS : RHEL-7.8_HVM_GA-20200225-x86_64-1-Hourly2-GP2
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
### LEAPP setup
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
sudo systemctl enable --now cockpit.socket
```
- Fix permissions to allow reports display in the Web Console
```
sudo chown root:adm /var/log/leapp && sudo chmod 750 /var/log/leapp
```
- Download repo mapping and rpm change files
```
sudo curl -o /etc/leapp/files/pes-events.json https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_09/leapp-data8/pes-events.json
sudo curl -o /etc/leapp/files/repomap.csv https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_09/leapp-data8/repomap.csv
```
- Create the demo user or make sure you have a system user with similar privileges
```
sudo useradd -G wheel,adm demo
echo "demo" | sudo passwd --stdin demo
```
- Reboot your system
```
sudo reboot
```

### Customization
**These steps are all optional and designed to make a more realistic system before the hands-on**
- Install packages on the machine such as an Apache server
```
sudo yum -y install httpd
sudo systemctl enable --now httpd
sudo bash -c 'echo "Hello World" > /var/www/html/index.html'
```
- Change some configuration files as you usually would on your systems

## Ensure your system is ready

- Reach your system with a web browser on the :9090 HTTPS port
> *Example : https://1.2.3.4:9090*

- Log in with the **demo** user (password: demo)

- Make sure the **In-Place Upgrade Report** tab is visible on the left

## Follow the hands-on during the Webinar

- Watch the webinar and start the manipulations when I prompt you to do so.


## Send feedback :)

If you enjoyed this virtual hands-on, feel free to send feedback !
(contact information is displayed at the end of the webinar)
