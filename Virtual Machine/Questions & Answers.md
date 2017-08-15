### Enable copy & paste in VMWare

**Procedure**  
1
Log into a vCenter Server system using the vSphere Client and select the virtual machine.  

2
On the Summary tab, click Edit Settings.  

3
Select Options > Advanced > General and click Configuration Parameters.  

4
Click Add Row and type the following values in the Name and Value columns.  

**Name**  isolation.tools.copy.disable

**Value**  false

**Name**  isolation.tools.paste.disable

**Value**  false

Note  
These options override any settings made in the guest operating system’s VMware Tools control panel.  

5
Click OK to close the Configuration Parameters dialog box, and click OK again to close the Virtual Machine Properties dialog box.  

6
Restart the virtual machine.  

### Why I can't use browser to visit 80 port of my VM?

    Try stop and disable the firewall of the VM.
    e.g. systemctl stop firewalld.service              systemctl disable firewalld.service
