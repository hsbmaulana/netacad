<h1 align="center">Lab D</h1>

**Case**

![Lab_D-Scenario](https://user-images.githubusercontent.com/38196994/136649787-d4b4eda1-2020-45c9-b743-0b9eaf63169d.png)

**Problem Solve**

![Lab_D-Objective](https://user-images.githubusercontent.com/38196994/136649785-2b20bc44-4f28-4e31-986f-03a8781b611d.png)

`su - root` with password *netlab123*

`cat /etc/services | awk '$2 ~ /^[0-9]+\/(tcp|udp)$/ {print $1}' | sort | uniq 1> ~/uniqueservices.txt && wc -l ~/uniqueservices.txt`

Author
---

- Hasby Maulana ([@hsbmaulana](https://linkedin.com/in/hsbmaulana))
