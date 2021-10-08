<h1 align="center">Lab A</h1>

**Case**

![Lab_A-Scenario](https://user-images.githubusercontent.com/38196994/136551670-45d0b904-b3b0-4ff7-b4b8-5c9807f4062a.png)

**Problem Solve**

`su - root` with password *netlab123*

1. Create a directory at the root (/) of the file system for each department.<br/>This name should reflect the department name that will use the directory.

    `mkdir -p /{home_engineer,home_sales,home_is}`

2. Create a group for each department.<br/>This name should reflect the department name that the group will be assigned.

    `groupadd staff_engineer`<br/>
    `groupadd staff_sales`<br/>
    `groupadd staff_is`<br/>

3. Create an administrative user for each of the departments.<br/>The user will have a bash login shell.<br/>The user will belong to the respective group for each department. This will need to be the user’s primary group.

    `useradd -g staff_engineer -s /bin/bash -M -d /home_engineer/ admin_engineer`<br/>
    `useradd -g staff_sales -s /bin/bash -M -d /home_sales/ admin_sales`<br/>
    `useradd -g staff_is -s /bin/bash -M -d /home_is/ admin_is`<br/>

4. Create two additional users for each department.<br/>The users will have a bash login shell.<br/>The users will belong to their respective group for each department. This will need to be the user’s primary group.

    `useradd -g staff_engineer -s /bin/bash -M -d /home_engineer/ user1_engineer`<br/>
    `useradd -g staff_engineer -s /bin/bash -M -d /home_engineer/ user2_engineer`<br/>

    `useradd -g staff_sales -s /bin/bash -M -d /home_sales/ user1_sales`<br/>
    `useradd -g staff_sales -s /bin/bash -M -d /home_sales/ user2_sales`<br/>

    `useradd -g staff_is -s /bin/bash -M -d /home_is/ user1_is`<br/>
    `useradd -g staff_is -s /bin/bash -M -d /home_is/ user2_is`<br/>

5. For security reasons, the following modifications will need to be made to each of the departments' respective directories.<br/>

    - Ensure that the owner of each of the directories is the department administrator and the group ownership is the group for each department.
    <br/>`chown admin_engineer:staff_engineer /home_engineer/`
    <br/>`chown admin_sales:staff_sales /home_sales/`
    <br/>`chown admin_is:staff_is /home_is/`
    - The department administrator will have full access to their respective department directories.
    <br/>`chmod 0700 /home_engineer/`
    <br/>`chmod 0700 /home_sales/`
    <br/>`chmod 0700 /home_is/`
    - Ensure that only the owner of a file in the department’s directory can delete the file. The user will also have ownership of their respective department folders.
    <br/>`chmod u+s /home_engineer/`
    <br/>`chmod u+s /home_sales/`
    <br/>`chmod u+s /home_is/`
    - Normal users in each department will have full access (read, write and execute) to their respective department folders.
    <br/>`chmod g+rwx /home_engineer/`
    <br/>`chmod g+rwx /home_sales/`
    <br/>`chmod g+rwx /home_is/`
    - The department folders will ONLY be accessible by users/administrators in each of the respective departments. Ensure that no one else will have permissions to the folders.
    <br/>`chmod o= /home_engineer/`
    <br/>`chmod o= /home_sales/`
    <br/>`chmod o= /home_is/`

6. Create a document in each of the department directories.<br/>

    - The ownerships on this file will be the same as the directory it is located in.
    <br/>`touch /home_engineer/text.txt && chown admin_engineer:staff_engineer /home_engineer/text.txt`
    <br/>`touch /home_sales/text.txt && chown admin_sales:staff_sales /home_sales/text.txt`
    <br/>`touch /home_is/text.txt && chown admin_is:staff_is /home_is/text.txt`
    - The document should contain only one line of text that states, “This file contains confidential information for the department.”
    <br/>`echo "This file contains confidential information for the department." 1> /home_engineer/text.txt`
    <br/>`echo "This file contains confidential information for the department." 1> /home_sales/text.txt`
    <br/>`echo "This file contains confidential information for the department." 1> /home_is/text.txt`
    - This file can be read by any user in the department, but can only be modified by the department administrator. No one else has permissions to this file.
    <br/>`chmod 0640 /home_engineer/text.txt`
    <br/>`chmod 0640 /home_sales/text.txt`
    <br/>`chmod 0640 /home_is/text.txt`

Author
---

- Hasby Maulana ([@hsbmaulana](https://linkedin.com/in/hsbmaulana))
