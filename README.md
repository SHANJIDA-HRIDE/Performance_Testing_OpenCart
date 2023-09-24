# Performance Testing OpenCart Website
## Table of Content
- [Introduction](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#introduction)
- [Install](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#install)
- [Prerequisites](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Prerequisites)
- [Elements of a minimal test plan](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Elements-of-a-minimal-test-plan)
- [Test Plan](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Test-Plan)
- [Load Testing Report](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Load-Testing-Report)
- [Summary Load Testing](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Summary-Load-Testing)
## Introduction
- This report provides an overview of the load testing, stress testing, and spike testing conducted on the Opencart website. The objective of this testing was to evaluate the system's performance under various load conditions and ensure it meets the specified requirements.
## Install
- **Java**  
https://www.oracle.com/java/technologies/downloads/

- **JMeter**  
https://jmeter.apache.org/download_jmeter.cgi     
- =>**apache-jmeter-5.5.zip**

- **We use BlazeMeter to generate JMX files**    
https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en

## Prerequisites
- As of JMeter 4.0, Java 8 and above are supported.
- we suggest  multicore CPUs with 4 or more cores.
- Memory 16GB RAM is a good value.

## Elements of a minimal test plan
- Thread Group

    The root element of every test plan. Simulates the (concurrent) users and then runs all requests. Each thread simulates a single user.

- HTTP Request Default (Configuration Element)

- HTTP Request (Sampler)

- Summary Report (Listener)

## Test Plan

Testplan > Add > Threads (Users) > Thread Group (this might vary depending on the JMeter version you are using)
- Name: Users
- Number of Threads (users): 1 to 6
- Ramp-Up Period (in seconds): 10
- Loop Count: 1  

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.
 ## Collection of API

- Run BlazeMeter  
- Collect Frequently used API  
- Save the JMX file then paste => **apache-jmeter-5.5\bin**

    ### List of API 

    - [https://www.opencart.com/index.php?route=common/home](https://www.opencart.com/index.php?route=common/home)
    - [https://www.opencart.com/index.php?route=cms/feature](https://www.opencart.com/index.php?route=cms/feature)
    - [https://www.opencart.com/index.php?route=marketplace/extension](https://www.opencart.com/index.php?route=marketplace/extension)
    - [https://www.opencart.com/index.php?route=cms/company](https://www.opencart.com/index.php?route=cms/company)
    - [https://www.opencart.com/index.php?route=account/login](https://www.opencart.com/index.php?route=account/login)
    - 

![image](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/9c184ed5-3c34-4d0f-ab3f-39d712b1acbf)

## Load Testing Report

| Concurrent Request  | Loop Count | Avg TPS for Total Samples  | Error Rate | Total Concurrent API request |
|               :---: |      :---: |                      :---: |                        :---: |      :---: |
| 1  | 1  | 3.350  | 0%      | 212   |
| 2  | 1  |  7     | 0%      | 424   |
| 3  | 1  |  11    | 0%      | 636   |
| 4  | 1  |  14.1  | 0%      | 848   |
| 5  | 1  |  17.6  | 4%      | 1060  |
| 6  | 1  |  20    | 26%     | 1272  |

## Summary Load Testing
- While executing 3 concurrent requests, 848 requests got connection timeout and the error rate is 0%.
- Server can handle almost concurrent 900 API calls with almost zero (0) error rate.

## Stress Testing
- Stress testing is a type of performance testing that evaluates how a system or application behaves and performs under extreme conditions or at the limits of its intended capacity. The goal of stress testing is to uncover the system's vulnerabilities, identify performance bottlenecks, determine the system's breaking point, and understand its behavior in stressful scenarios.

**Number of Threads 7 ; Ramp-Up Period 10s**

Requests Summary             |  Errors
:-------------------------:|:-------------------------:
![a](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/e5072515-33e3-472f-8c3d-b005b7284672) |  ![b](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/e931ab40-e6a5-4121-abbe-afc24693e931)

**Number of Threads 8 ; Ramp-Up Period 10s**
Requests Summary             |  Errors
:-------------------------:|:-------------------------:
![a](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/18de8016-5291-4edd-bc21-2611e9e9d3b3) |  ![b](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/8bca7a38-d0c4-4714-86fe-f65c13ac8659)

**Number of Threads 9 ; Ramp-Up Period 10s**
Requests Summary             |  Errors
:-------------------------:|:-------------------------:
![a](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/86da5e01-8e85-40af-9de9-f8199552875a) |  ![b](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart/assets/62147630/3e6149e1-4ad0-474a-8af6-813c5dc54704)

