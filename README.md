# hashing-analysis-exercise
Exploring SHA-256

![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![Tool](https://img.shields.io/badge/Tool-PowerShell-blue)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Focus](https://img.shields.io/badge/Focus-Data%20Integrity-red)
![Focus](https://img.shields.io/badge/Focus-Cryptographic%20Hashing-red)

# Lab: Cryptographic Hashing and the Avalanche Effect

## Overview
This lab demonstrates the concept of **Data Integrity** using the SHA-256 hashing algorithm. Inspired by the **Trivial** layer of the Pyramid of Pain (https://tryhackme.com/room/pyramidofpainax), I explored how even a minor change to a file's content results in a completely different hash value—known as the **Avalanche Effect**.

## Tools Used
* Windows PowerShell: Used the Get-FileHash cmdlet to generate hashes  
* Notepad: Used to create and modify the test data  

## Step-by-Step Procedure

### 1. Baseline Creation
I created a file named `lab.txt` with the following content:

> This is a secret file.

I then ran this PowerShell command:

Get-FileHash C:\Users\<username>\Desktop\secret.txt -Algorithm SHA256

Initial Hash:
D46AFF833CA01C4EA51DBCF47611A4ECED9885BB2AA2A734B3F3FAF5E9C7CCEE

## Modifying the Data
To test the sensitivity of the hash, I added a single period (.) to the end of the text file.

## Verification and Comparison
I re-ran the hashing command:

Get-FileHash C:\Users\<username>\Desktop\secret.txt -Algorithm SHA256

Modified Hash:
02CDAF962854DEB7E87A3CDDBC848BAA45DAC32C74A49C8E4DB51EDEDE161180

## Key Findings
The hash changed entirely despite a 99% identical file. This proves hashes are excellent for detecting unauthorized modifications.

This also reinforces why hashes sit at the bottom of the Pyramid of Pain—attackers can bypass hash-based detection (IOCs) by changing a single byte of their malware.
