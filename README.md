Before running the playbook, you need to install a couple of ansible collections for supporting additional commands used. In the command line enter the following commands:

$ ansible-galaxy collection install ansible.posix
$ ansible-galaxy collection install community.general


By default the InsightVM agent will be installed. So you will need to have teh agent ZIP file in the same directory you are running the script from.

If you do not need the InsightVM agent installed with this script then you need to use the command example at the bottom. You need to add an extra variable in the command line called "needIVM" and set it to "False" or "false".

To run the play book, you need a hosts file like the one provided (input the non-root username and IP address of the machine).

-k  -- prompts for the SSH connection password.
-K  -- prompts for the sudo password (same one you get prompted for when using sudo normally, you should be able to just hit enter here).
-e [additional-variables] -- reads extra variables at the command line to pass through (any additional variables must match exactly what is in the playbook)

-----------------------------------------------
Run the play book with InsightVM Agent install:

ansible-playbook -i [host-filename] [playbook-name] -kKe '{"insightVMTag":"attributename"}'

Example:

ansible-playbook -i hosts UbuntuSecure.yml -kKe '{"insightVMTag":"SomeTagName"}'

--------------------------------------------------
Run the play book without InsightVM Agent install:

ansible-playbook -i [host-filename] [playbook-name] -kKe "needIVM=false"

Example:

ansible-playbook -i hosts UbuntuSecure.yml -kKe "needIVM=false"
