# eBPF eCapture

## Installation

Download the latest version of eBPF eCapture from the following link.  

`https://github.com/gojue/ecapture/releases`  

Note: Linux kernel version >= 4.18 is required.  

Find `ecapture-v0.5.3-linux-x86_64.tar.gz` and download the same.  

Extract the contents and execute `./ecapture`.  

![11](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/50b5b904-e576-4433-abd9-61b270aeeec2)

## TLS Command

Capture tls text content.  

`./ecapture tls --hex`  

`curl https://github.com`  

![12](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/b1aa4358-b16c-4a6e-aaf7-cd9e28f78217)


## Using eCapture  

Any authentic website has a valid CA certificate. The same can be checked by clicking the padlock icon before the URL on any modern web browser.  

Run the following command in a terminal window to start capturing text content.  

`sudo ./ecapture tls`  

![11](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/8726c955-b0ea-4176-990c-781be52795de)

Open a new terminal window and use the `wget` command for any website.  

`wget https://www.google.com`  

![wget](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/561a9c00-4335-4768-97d0-54158f46cfab)

You will see the eCapture tool capturing the web text content in its terminal window.  

![x1](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/185acc82-4a7c-46ed-887e-66ec71a81889)

![x2](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/905195ee-7b1e-4b87-a494-29b0dc80b8e4)

To capture the hex code model, run the following command in a terminal window.  

`sudo ./ecapture tls --hex`  

Open a new terminal window and use the `curl` command for any website.  

`curl https://www.google.com`  

You will see the eCapture tool capturing the hex model in its terminal window.

![hex](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/7526993d-788c-4868-9d95-4dc10e9421db)


# Capturing the Contents of a Web Browswer

Firefox is used in this case. Use the `ps` command to list the currently running processes.  

`ps -ef grep|firefox`  

![1ps](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/39eb669b-ae59-4ff8-a786-525e65de72f7)

Now, run the following `ldd` command after finding Firefox in the running processes list.  

`ldd /snap/firefox/2356/usr/lib/firefox/firefox |grep -E "tls|ssl|nspr|nss"`  

Find the process ID of Firefox as given by the `ps` command and run the following command.  

`sudo pldd 1729 |grep -E "nss|nspr|tls|ssl`  

![2pldd](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/07eca30a-203c-441f-92e0-385a1d17d55c)

libnspr4.so is not the default as used by eCapture. Copy the first path as given by the `pldd` command.  

Use the `nspr` flag in eCapture in a new terminal window.  

`sudo ./ecapture tls --hex --nspr /snap/firefox/2356/usr/lib/firefox/libnspr4.so`  

![3nspr1](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/a28eedc3-aa03-45de-ac7c-2f03e2fc3b9f)

Open any webpage in Firefox and you will see eCapture capturing the contents in its terminal window.  

![4cap](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/53b54b83-f2aa-4c2c-a4c3-0796ce76d34a)


# Capturing Bash Module Commands

Run the following command.  

`sudo ./ecapture bash`  

eCapture will now capture all the commands that are executed in any terminal window.   

Try running some commands in a new terminal window. eCapture will record the commands executed.  

![bash](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/10174bd0-67a7-482d-9a72-4f13c8f622b5)


# Capturing SQL Queries

Run the following command to capture the SQL queries, assuming you have MariaDB installed.  

`sudo ./ecapture mysqld`  

Try executing some SQL queries and eCapture will capture the same queries.  

![1sql](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/07a50976-94c0-4c5a-920f-95fd60392499)

![2sqlCap](https://github.com/samareshbera/eBPF_eCapture/assets/96954630/61eee42a-bb10-4b1a-9f60-d641c13b944d)


