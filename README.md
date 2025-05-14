# Enumeration and Access to Exposed Credentials

In this lab, you will explore a Windows server hosting a personal WordPress site and exposing a vulnerable SMB service. Your task is to enumerate users using specific tools, analyze clues within the blog, build your own password dictionary, access shared resources, and obtain a secret flag. In this lab you will learn:

- SMB service enumeration
- Analyzing clues in web content
- Creating custom dictionaries
- Accessing shared resources on Windows
- Remotely accessing WordPress with discovered credentials

## 🌱 How to Start This Lab

Follow these instructions to get started:

1. **Download the virtual machine** from this [link](https://storage.googleapis.com/cybersecurity-machines/blog-lab.ova).
2. **Import the machine** into your preferred virtualization manager (VirtualBox, VMware, etc.).
3. Once the machine is running, you can start the lab!

## 📄 Instructions

You are facing the personal site of a photographer named **John Wilson**. In addition to the blog, the server exposes SMB shared resources in a Windows environment. You must apply enumeration techniques and reasoning to access sensitive information.

1. **Discover the IP address of the MyBlog machine.** Use tools like `nmap`, `netdiscover`, or `enum4linux` to find the IP address and active services.

2. **Enumerate system users.** Use `enum4linux` against the IP to find possible SMB users.

3. **Explore the personal blog.** Access `http://<IP>/myblog` from your browser.

4. **Deduce the password.**

5. **Perform an SMB authentication attack.** Use `hydra` or `smbclient` with your dictionary to try to authenticate.

6. **Access the shared resource.**

7. **Access WordPress with the credentials.**

8. **Capture the flag.** The flag will be displayed directly in the admin panel after logging in.

**Tip:** Not everything is solved by brute force. Sometimes, a well-placed clue is the key.

Happy hacking!
