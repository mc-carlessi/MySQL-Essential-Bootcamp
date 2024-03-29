[Summary](./index.md)

# Test lab connectivity and zoom Break Out Rooms

## Introduction

<details>
  <summary>Task 1 - SSH connection to app-srv server</summary> 

Check that you are able to connect to your app-srv server, required to execute labs. 

1.	Follow trainer instructions to download software material (with also this guide)

2.	Check which app-srv is assigned to you

    1.	Connect with your SSH client using the public IP and the provided ssh key.

    2.	As an example here there is the command for Linux, MAC and Windows Powershell

    ```shell
    ssh -i id_rsa_app-srv opc@your_public_ip
    ls -l /tmp
    ```

    3.	If you are using PuTTY, here some tips how to use it: [PuTTY configuration](./putty_instructions.md)
</details>

<details>
  <summary>Task 2 - Ask for help inside Zoom Break Out rooms</summary>

In many case, to make the lab execution more comfortable with many attendees,we use the Zoom break-out rooms features.
Break-out rooms are isolated each other, and to communicate with the trainer you need to use the button “Ask for help” in the zoom interface.
Please see pictures below as reference.

1. Press “Ask for help” button

![Ask for help button](../images/zoom-ask_for_help_button.png)

2. Press "Invite host"

![Invite host confirmation](../images/zoom-ask_for_help_confirm.png)

3. You see now a confirmation message (that disappear after a short time)
Please wait that one of the trainers join your session.

![Ask for help request sent](../images/zoom-ask_for_help_sent.png)
    
[Next](./mysql_architecture_and_installation.md)
</details>