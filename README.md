# Performance Testing OpenCart Website
## Table of Content
- [Introduction](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#introduction)
- [Install](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#install)
- [Prerequisites](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Prerequisites)
- [Elements of a minimal test plan](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#Elements_of_a_minimal_test_plan)
- [Test Plan](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#install)
- [Load Testing Report](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#install)
- [Summary Load Testing](https://github.com/SHANJIDA-HRIDE/Performance_Testing_OpenCart#install)
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
