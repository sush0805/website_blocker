# website_blocker

This code snippet demonstrates a simple website blocker script that blocks access to specific websites by modifying the hosts file on a Windows system.

## Usage

1. Make sure you have Python installed on your system.
2. Modify the `site_block` list to include the websites you want to block.
3. Run the script using the Python interpreter.

## Code

```python
import datetime
import time

end_time = datetime.datetime(2023, 5, 23)
site_block = ["www.flipkart.com", "www.facebook.com"]
host_path = "C:/Windows/System32/drivers/etc/hosts"
redirect = "127.0.0.1"

while True:
    if datetime.datetime.now() < end_time:
        print("Start Blocking")
        with open(host_path, "r+") as host_file:
            content = host_file.read()
            for website in site_block:
                if website not in content:
                    host_file.write(redirect + " " + website + "\n")
                else:
                    pass
    else:
        with open(host_path, "r+") as host_file:
            content = host_file.readline()
            host_file.seek(0)
            for line in content():
                if not any(website in line for website in site_block):
                    host_file.write(line)

            host_file.truncate()
        time.sleep(10)
