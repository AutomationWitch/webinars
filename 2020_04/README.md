# Directions

## Ensure you have a RHEL subscription available
- You can use a 30 Day Red Hat Enterprise Linux Server Self-Supported Evaluation available [here](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/try-it)
- Red Hat Developer accounts may not work with Insights

## Prepare your environment
**These steps are optional and only needed if your system is not ready for the hands-on**

- Install a RHEL 7 or RHEL 8 system (directions will cover RHEL 8)
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
- Install Ansible and Insights agent
```
sudo yum -y install ansible insights-client --enablerepo=ansible-2-for-rhel-8-x86_64-rpms
```
- Register your system to Insights
```
sudo insights-client --register
```


## Ensure your system is ready
**This is mandatory**
If your system shows errors you will not be able to do the hands-on.
Go back to preparation steps if needed.

- Clone this repository or download both playbooks from this directory :
```
curl -O https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_04/setup_validation.yml
curl -O https://raw.githubusercontent.com/AutomationWitch/webinars/master/2020_04/fetch_remediations.yml
```

- Launch the setup_validation.yml playbook with the following command (you need ansible)
```
ansible-playbook setup_validation.yml -K
```
The playbook will prompt for a sudo password and then for your Red Hat credentials
You should get 4 OK statement and no errors at the end of the playbook execution.


## Follow the hands-on during the Webinar

- Watch the webinar and start the manipulations when I prompt you to do so.


## Send feedback :)

If you enjoyed this virtual hands-on, feel free to send feedback !
(contact information is displayed at the end of the webinar)
