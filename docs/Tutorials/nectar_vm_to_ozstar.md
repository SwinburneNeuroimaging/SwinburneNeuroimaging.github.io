# Creating a Nectar VM and connecting to the Ozstar filesystem

Ensure that you have an account on the ozstar computing system before proceeding. (See [here](https://supercomputing.swin.edu.au/docs/1-getting_started/Accounts.html) to apply for one). 

- Once you have an ozstar account, go to https://desktop.rc.nectar.org.au/home/

- Select '_Login VIA AAF (Australia)_' or '_Australia Access Federation_'

- Select your organisation

- Login (if necessary)

- Select '_Neurodesktop_' from the '_Desktop Library_' (you may have to scroll down to see it)

- Click '_+Create Desktop_'

- Keep the '_Default zone_' and click '_Create_'

...wait a few minutes....

- Click '_Open Desktop_'

( If you get a pop-up window '_See txt and images copied to the clipboard_', click '_Allow_'. )

- Once the VM has started, click on the '_LXTerminal_' icon at the bottom left corner of the browser window.

[[https://github.com/SwinburneNeuroimaging/swinburne_tools/blob/main/VM_terminal_screenshot.png]]

- Run the following line in the terminal (use _Ctrl-Shift-V_ to paste into the terminal), and enter your <ins>ozstar</ins> username and password when prompted:

```
curl -Ls https://raw.githubusercontent.com/SwinburneNeuroimaging/swinburne_tools/main/ozstar_setup.sh > /tmp/tmp.sh; bash /tmp/tmp.sh
```
This only has to be run once when the virtual machine is created. 

Sometimes the connection to the ozstar filesystem will get dropped (this will happen if the machine gets 'shelved' for instance). You can run the command 
```
reconnect_ozstar
```
in a terminal to reconnect to ozstar at any time.


### N.B. (from the [ARDC VM support page](https://support.ehelp.edu.au/support/solutions/articles/6000253856-nectar-virtual-desktop-service) )

_**Resources:** The default resourcing for a desktop is 8 virtual CPU Cores & 16GB RAM._
_Users will have the option to increase resources if the default is not sufficient for their computing needs. This can be done via the boost function, increasing resources to 16 virtual CPU Cores and 32GB RAM._


_**Time:** Once a user has started a Virtual Desktop, this desktop will be available for 14 days (with the ability to extend). After 14 days, the desktop will initiate an expiry process, with the instance shelved for 3 months, and then deleted. You will receive email reminders at each stage of the expiry process._

