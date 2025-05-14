# MyBlog Lab

This lab tests the student's ability to combine SMB enumeration techniques with web content analysis and apply logical reasoning to discover credentials. Through this workflow, students will understand:

- Using tools like `enum4linux` to enumerate users on Windows systems.
- Analyzing hints within web content to deduce passwords.
- Creating custom wordlists for targeted brute-force attacks.
- Accessing SMB shared resources.
- Logging into a WordPress site with discovered credentials.

## Machine Specifications 🖥️

- **System:** Windows Server 2016 or 2019
- **Active services:** SMB and Apache (via XAMPP)
- **Website:** WordPress located at `C:\xampp\htdocs\myblog`
- **SMB shared resource:** `\\<IP>\john`
- **Content of SMB folder:** `credentials_wp.txt`
- **Key WordPress post:** Entry where John mentions being born in a *“year of the dog”* (an indirect reference to 1994).
- **Valid SMB user:** `john`  
- **Expected password:** `1994`
- **WordPress user:** `john`  
- **WordPress password:** `j0hn_1994`  
- **Flag:** Visible upon logging in as `john` in the admin panel.

### Machine Credentials

```bash
name: myblog-lab
user: administrator
password: 4geeks-lab
```

## Expected Steps for the Student

1. **Perform network reconnaissance to identify the machine:** Use tools like `nmap`, `netdiscover`, or `enum4linux`. The student should identify that the host has **SMB active** and web services available.

2. **Enumerate users with `enum4linux`.** Run:

    ```bash
    enum4linux -a <IP>
    ```
3. **Explore the WordPress site.** Go to: `http://<IP>/myblog` and read the blog post where John mentions the "year of the dog".

4. **Create a custom wordlist.** Based on the hint, deduce that 1994 is the most likely year. Generate the file:

    ```bash
    echo 1994 > possible_password.txt
    ```
5. **Attack the SMB service.** Use `smbclient` or `hydra` to authenticate as **john** with the password 1994. Example:

    ```bash
    smbclient //192.168.X.X/john -U john
    ```
Access the shared resource and download `credentials_wp.txt`.

6. **Log in to WordPress with the credentials**

    ```text
    User: john
    Password: j0hn_1994
    ```

Go to:

```perl
http://<IP>/myblog/wp-login.php
```
7. **Find the flag.** The flag is automatically displayed in the admin panel as a visible message.
