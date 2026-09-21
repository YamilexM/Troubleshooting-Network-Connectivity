# Troubleshooting Network Connectivity

## Project Overview

In this lab, I practiced basic network troubleshooting inside a Windows 11 virtual machine hosted in Microsoft Azure.

I reviewed the VM's network configuration, tested connectivity to the configured default gateway, and used DNS lookup tools to verify name resolution.

The goal was to become more comfortable using built-in Windows networking commands to gather information and troubleshoot connectivity issues in an IT support environment.

## Technologies Used

- Windows 11
- Microsoft Azure Virtual Machine
- Command Prompt
- TCP/IP Networking
- DNS
- Remote Desktop Protocol (RDP)

## What I Practiced

- Reviewing Windows IP configuration
- Identifying an IPv4 address
- Identifying the subnet mask
- Identifying the default gateway
- Testing network connectivity with `ping`
- Reviewing packet-loss results
- Testing DNS resolution with `nslookup`
- Comparing results from different troubleshooting tools
- Documenting network troubleshooting steps

## Step 1: Review the Network Configuration

I opened Command Prompt inside the Windows virtual machine and ran:

```cmd
ipconfig
```

The command displayed the network configuration for the VM's Ethernet adapter.

I identified the following information:

- **IPv4 Address:** 10.0.0.4
- **Subnet Mask:** 255.255.255.0
- **Default Gateway:** 10.0.0.1

Reviewing this information helped establish a baseline before performing additional connectivity tests.

![IP Configuration Baseline](images/01-ipconfig-baseline.png)

## Step 2: Test Connectivity to the Default Gateway

Next, I tested connectivity to the configured default gateway by running:

```cmd
ping 10.0.0.1
```

The requests timed out and the test returned:

- **Packets Sent:** 4
- **Packets Received:** 0
- **Packet Loss:** 100%

Because this virtual machine was running in Microsoft Azure, I learned that a failed ICMP ping to the Azure-provided gateway does not automatically mean the VM has lost network connectivity.

This reinforced the importance of using more than one troubleshooting tool before determining the cause of a network issue.

![Default Gateway Ping Test](images/02-default-gateway-ping-test.png)

## Step 3: Test DNS Resolution

To continue troubleshooting, I used `nslookup` to determine whether the VM could resolve a domain name.

I ran:

```cmd
nslookup microsoft.com
```

The lookup successfully returned IPv4 and IPv6 addresses for `microsoft.com`.

This confirmed that DNS resolution was functioning even though the previous gateway ping timed out.

![DNS Resolution Test](images/03-dns-resolution-test.png)

## Troubleshooting Summary

During this lab, I used multiple commands to review different parts of the network configuration.

The troubleshooting process included:

1. Reviewing the VM's IP configuration with `ipconfig`
2. Identifying the IPv4 address, subnet mask, and default gateway
3. Testing the configured gateway with `ping`
4. Reviewing the timeout and packet-loss results
5. Testing name resolution with `nslookup`
6. Confirming that DNS resolution was functioning

This helped me understand why troubleshooting should not rely on the result of a single test.

## Skills Practiced

- Network Troubleshooting
- Windows Command Prompt
- TCP/IP Fundamentals
- IPv4 Addressing
- Subnet Identification
- Default Gateway Identification
- DNS Troubleshooting
- `ipconfig`
- `ping`
- `nslookup`
- Azure Virtual Machines
- Windows Administration
- Technical Documentation

## What I Learned

This lab helped me better understand how to approach basic network troubleshooting in Windows.

I practiced reviewing IP configuration, testing connectivity, and checking DNS resolution using built-in command-line tools.

One of my main takeaways was that a failed ping does not always mean the entire network connection is down. Additional testing can help determine whether other network services, such as DNS, are still functioning.

This project gave me more hands-on experience with the type of basic network troubleshooting commonly performed in IT support and help desk environments.
