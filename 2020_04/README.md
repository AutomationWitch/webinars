# Directions
## Prepare your Environment
### These steps are optional and only needed if your system is not ready for the hands-on

- Install a RHEL 7 or RHEL 8 system (directions will cover RHEL 8)
- Register it with subscription-manager
```
sudo subscription-manager register --auto-attach
```
- Install Ansible and Insights agent
```
sudo yum install ansible insights-client
```
- Register your system to Insights
```
sudo insights-client --register
```


## Ensure your system is ready
### This is mandatory
### If your system shows errors you will not be able to do the hands-on

- Launch the setup_validation.yml playbook with the following command (you need ansible)
```
ansible-playbook setup_validation.yml
```
You should get 1 OK statement and no errors at the end of the playbook execution.


## Follow the hands on during the Webinar

Watch the webinar and start the manipulations when I prompt you to do so.


## Send feedback

If you enjoyed this virtual hands-on, feel free to send feedback !
(contact information is displayed at the end of the webinar)
