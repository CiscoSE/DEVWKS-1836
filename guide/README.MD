# DEVWKS-1836 (Cisco Live US 2019) Workshop Guide

This is the workshop guide for Cisco Live US 2019 DevNet workshop DEVWKS-1836 - Hands-On with Cisco Python API on IOS
XE.

* Introduction
    * Using Python with IOS XE
        * Off-box vs. On-box
* Cisco IOS XE On-Box Python
    * IOS XE Guest Shell
    * IOS XE Python API
        * Python WebUI Sandbox
            * Navigate Configuration > Services > Python Sandbox
        * Python Interpreter
            * Running Python interactive interpreter
            * Running Python script from IOS XE
            * Running Python script from EEM
                
                ```
                configure terminal
                event manager applet CountdownPython
                  event timer countdown time 15
                  action 1.0 syslog msg "DEVWKS-1836 Python example"
                  action 1.1 cli command "enable"
                  action 1.2 cli command "guestshell run python ex02.py"
                  action 1.3 cli command "exit"
                  exit
                end
                ```
                
        * Python CLI Module Functions
* Example Hands-On Exercises
    * cli()
    
    ```
    import cli
    result=cli.cli('show clock')
    print(result)
    ```
    
    ```
    import cli
    result=cli.cli('show clock; show ip interface brief')
    print(result)
    ```
    
    ```
    import cli
    commands='''show clock
    sh ip interface brief
    '''
    result=cli.cli(commands)
    print(result)
    ```
    
    ```
    import cli
    result=cli.cli('configure terminal; interface Loopback100; description Configured by Python cli function; ip address 10.10.10.100 255.255.255.255; no shutdown; end')
    print(result)
    ```
    
    ```
    import cli
    commands = '''configure terminal
    interface Loopback101
    description Configured by Python cli function
    ip address 10.10.10.101 255.255.255.255
    no shutdown
    end
    '''
    result=cli.cli(commands)
    print(result)
    ```

* clip()
    
    ```
    import cli
    cli.clip('show clock')
    ```
    
    ```
    import cli
    cli.clip('show clock; show ip interface brief')
    ```
    
    ```
    import cli
    commands='''show clock
    sh ip interface brief
    '''
    cli.clip(commands)
    ```
    
    ```
    import cli
    cli.clip('configure terminal; interface Loopback102; description Configured by Python clip function; ip address 10.10.10.102 255.255.255.255; no shutdown; end')
    ```
    
    ```
    import cli
    commands = '''configure terminal
    interface Loopback103
    description Configured by Python clip function
    ip address 10.10.10.103 255.255.255.255
    no shutdown
    end
    '''
    cli.clip(commands)
    ```

* execute()
    
    ```
    import cli
    result=cli.execute('show clock')
    print(result)
    ```
    
    ```
    import cli
    result=cli.execute('show clock; show ip interface brief')
    ```
    
    ```
    import cli
    commands='''show clock
    sh ip interface brief
    '''
    result=cli.execute(commands)
    ```
    
    ```
    import cli
    
    commands = [
        "show clock",
        "show ip interface brief"
    ]
    
    for c in commands:
        cli.execute(c)
    ```

* executep()
    
    ```
    import cli
    cli.executep('show clock')
    ```
    
    ```
    import cli
    cli.executep('show clock; show ip interface brief')
    ```
    
    ```
    import cli
    commands='''show clock
    sh ip interface brief
    '''
    cli.executep(commands)
    ```
    
    ```
    import cli
    
    commands = [
        "show clock",
        "show ip interface brief"
    ]
    
    for c in commands:
        cli.executep(c)
    ```

* configure()
    
    ```
    import cli
    result=cli.configure('interface Loopback104; description Configured by Python configure function; ip address 10.10.10.104 255.255.255.255; no shutdown; end')
    print(result)
    ```
    
    ```
    import cli
    commands = '''interface Loopback105
    description Configured by Python configure function
    ip address 10.10.10.105 255.255.255.255
    no shutdown
    end
    '''
    result=cli.configure(commands)
    print(result)
    ```
    
    ```
    import cli
    result=cli.configure(['interface Loopback106', 'description Configured by Python configure function', 'ip address 10.10.10.106 255.255.255.255', 'no shutdown', 'end'])
    print(result)
    ```
    
    ```
    import cli
    commands=['interface Loopback107', 'description Configured by Python configure function', 'ip 10.10.10.107 255.255.255.255', 'no shutdown', 'end']
    try:
        result = cli.configure(commands)
        print("Success!")
    except cli.CLIConfigurationError as e:
        print "Failed configuration:"
        for failure in e.failed:
            print failure
    ```

* configurep()
    
    ```
    import cli
    commands = '''interface Loopback108
    description Configured by Python configurep function
    ip address 10.10.10.108 255.255.255.255
    no shutdown
    end
    '''
    cli.configurep(commands)
    ```
    
    ```
    import cli
    cli.configurep(['interface Loopback109', 'description Configured by Python configurep function', 'ip address 10.10.10.109 255.255.255.255', 'no shutdown', 'end'])
    ```
    
    ```
    import cli
    cli.configurep(['interface Loopback110', 'description Configured by Python configurep function', 'ip  10.10.10.110 255.255.255.255', 'no shutdown', 'end'])
    ```

* Summary

# Introduction

The title of this workshop is "Hands-On with Cisco Python API on IOS XE".  In this workshop , we will introduce the 
Python API on IOS XE for on-box network programmability.  With the Cisco Python CLI module packaged with Guest Shell,
you can access EXEC and configuration mode CLI commands programmatically.  Use cases include, but are not limited to 
device management and configuration, Zero Touch Provisioning (ZTP), and Embedded Event Manager (EEM) actions.  We 
will dig into the Cisco Python module with example hands-on exercises demonstrating real world use cases.

## Using Python with IOS XE

lorem ipsum

## Learning Objectives

Upon completion of this workshop, you will be able to:

* Understand what is the Cisco IOS XE Python API
* Learn how to use the Cisco Python CLI module packaged with Guest Shell in IOS XE
* Practice with the Cisco Python CLI module to meet real-world use cases

## Lab Topology

Lorem ipsum

## Table of Contents

Lorem ipsum

# Cisco IOS XE On-Box Python

* Introducing IOS XE On-Box Python
    * Guest Shell
    * Python API
        * Python API > CLI Python Module > CLI Module Functions
            * cli
            * clip
            * execute
            * executep
            * configure
            * configurep
        * Python WebUI Sandbox
        * Python Interpreter

#### 

Lorem ipsum

# Example Hands-On Exercises



# Summary