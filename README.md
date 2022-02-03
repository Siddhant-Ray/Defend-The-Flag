# NetworkSecurity-DTF-Project

Contains my solution for the DTF project for the course Network Security HS 2021 at ETH Zurich.

## Tasks : 
In this project, you are given a virtual machine and are supposed to analyze and
implement common security measures you have seen in this course. Your task is to
create a program which fixes all of these issues automatically. We assume some
enough familiarity with Linux systems[^1] to navigate the shell and execute
basic commands.

Below you are given a list of tasks, either consisting of problems or issues
with the current setup. Some of these might not be resolvable before you solved
related problems, it is up to you to figure out these depedencies yourself.

You are permitted (and even encouraged) to install new packages on the machine,
inspect and change configuration files, and so on. See the "Tips" section for
some helpful hints.

Your solution repository is automatically cloned into your student's home
directory for your convenience.

### 2.1 | Internet connectivity

The VM has issues reaching the internet. Find out why this is the case and
resolve the issue.

> Tip: Try pinging the VM from your end. What do you see? Why might that happen?

### 2.2 | Secure the database server
Your VM is running a "database server" which is listening for TCP connections on
port 5432. Ensure that only the grading server running at
`grader.dtf.netsec.inf.ethz.ch` is able to access the database server from the
internet.

### 2.3 | You have been pwned!
There have been reports that malicious actors exfiltrated secure passwords from
your VM via HTTP. Find out how this happened and fix it.

> Your VM is running the well known and widely deployed
> [nginx](https://nginx.org) webserver, you can use `systemctl status nginx` to
> view its status.

### 2.4 | TLS certificate via ACME
Currently the VM serves HTTPS traffic using a self-signed certificate. From the
course you recall that while the data exchanged is still encrypted, a proper
chain of trust would be preferable. The first project dealt with you
implementing a client for the ACME protocol, while this one requires you to use
an ACME client to acquire a TLS certificate.

The ACME directory from which you should order the certificate is located at
`acme.dtf.netsec.inf.ethz.ch`. The ACME server directory is at
`/acme/default/directory`. Your task is to request a certificates for the domain name
`nethz.student.dtf.netsec.inf.ethz.ch` where `nethz` is your ETH username and
configure TLS traffic in the nginx web server.

> This domain only resolves internally, do not worry if you can't see the DNS
> records from your client machine.

### 2.5 | TLS configuration
Inspect the webserver's TLS configuration. Is it secure? If not fix the
identified issues and make it secure.
