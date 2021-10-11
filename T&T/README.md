<h1 align="center">Tips & Tricks</h1>

- Inverse contents.

    `echo $(ls -d -a /directory/!(x|y|z))`

- Show detail user password from current session.

    ```sh
    cat /etc/shadow | awk 'BEGIN{FS=":"} $1 ~ /^'$(whoami)'$/ {print $2} END{}' | \
    \
    sed 's/^\$1\$/(MD5)/;
    s/^\$2a\$/(Blowfish)/;
    s/^\$2y\$/(Eksblowfish)/;
    s/^\$5\$/(SHA-256)/;
    s/^\$6\$/(SHA-512)/;'
    ```

- Format drive.

    1. High level format.

        `mkfs.<fstype> /dev/sda?`

    3. Low level format.

        `dd if=/dev/zero|/dev/random|/dev/urandom of=/dev/sda? bs=1MB count=1024 status=progress`

- Generate random data from entropy.

    `cat /dev/random|/dev/urandom | base64 | head -c ?`

Author
---

- Hasby Maulana ([@hsbmaulana](https://linkedin.com/in/hsbmaulana))
