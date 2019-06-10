# DEVWKS-1836 (Cisco Live US 2019) Live Workshop Guide

This is the live Workshop Guide for Cisco Live US 2019 DevNet Workshop DEVWKS-1836 - Hands-On with Cisco Python API on
IOS XE.

If you are an attendee at Cisco Live US 2019 in the DevNet Zone participating in this Workshop, follow along with the 
presentation and copy and paste the commands or code snippets as demonstrated by the session speaker.

# Exercise 1

1. Navigate and login to the IOS XE device [Python WebUI Sandbox](https://198.18.134.11/webui/#/python) at 
`https://198.18.134.11/webui/#/python`.
    
    * Username: `admin`
    * Password: `C1sco12345`

# Exercise 2

1. Connect and login to the IOS XE device with the following Bash CLI command in macOS `Terminal.app`:
    
    ```
    ssh admin@198.18.134.11
    ```
    
    * Username: `admin`
    * Password: `C1sco12345`

2.  Copy and paste the following IOS XE EXEC mode CLI command:
    
    ```
    guestshell run python
    ```
    
3. Copy and paste the following Python code snippet into the Python interactive interpreter:
    
    ```
    import cli
    
    commands = [
        "show version",
    ]
    
    for c in commands:
        cli.executep(c)
    ```
    
    Copy and paste the following Python code snippet into the Python interactive interpreter:
    
    ```
    quit()
    ```

# Exercise 3

1. Copy and paste the following IOS XE EXEC mode CLI command:
    
    ```
    guestshell run wget https://raw.githubusercontent.com/CiscoSE/DEVWKS-1836/master/code/ex01.py
    ```

2. Copy and paste the following IOS XE EXEC mode CLI command:
    
    ```
    guestshell run python ex01.py
    ```

# Exercise 4

1. Copy and paste the following IOS XE EXEC mode CLI command:
    
    ```
    guestshell run wget https://raw.githubusercontent.com/CiscoSE/DEVWKS-1836/master/code/ex02.py
    ```

2. Copy and paste the following IOS XE configuration mode CLI commands:
    
    ```
    configure terminal
    event manager applet CountdownPython
      event timer countdown time 5
      action 1.0 syslog msg "DEVWKS-1836 Python example"
      action 1.1 cli command "enable"
      action 1.2 cli command "guestshell run python ex02.py"
      action 1.3 cli command "exit"
      exit
    end
    ```

# Exercise 5

1. Copy and paste the following IOS XE EXEC mode CLI command:
    
    ```
    guestshell run python
    ```
    
2. Copy and paste the following Python code snippets into the Python interactive interpreter:
    
    1. `cli()` Examples:
        
        1. Get and print to screen the result from a `cli()` function call with one IOS XE EXEC mode CLI command:
            
            ```
            import cli
            result=cli.cli("show clock")
            print(result)
            ```
        
        2. Get and print to screen the result from a `cli()` function call with multiple IOS XE EXEC mode CLI commands 
        delimited by semicolon:
            
            ```
            import cli
            result=cli.cli("show clock; show ip interface brief")
            print(result)
            ```
        
        3. Get and print to screen the result from a `cli()` function call with multiple IOS XE EXEC mode CLI commands 
        delimited by newline:
            
            ```
            import cli        
            commands='''show clock
            sh ip interface brief
            '''
            result=cli.cli(commands)
            print(result)
            ```
        
        4. Get and print to screen the result from a `cli()` function call with multiple IOS XE configuration mode CLI 
        commands delimited by semicolon:
            
            ```
            import cli
            result=cli.cli("configure terminal; interface Loopback100; description Configured by Python cli function; ip address 10.10.10.100 255.255.255.255; no shutdown; end")
            print(result)
            ```
        
        5.  Get and print to screen the result from a `cli()` function call with one malformed IOS XE EXEc mode CLI 
        command (raises Python exception):
            
            ```
            import cli
            result=cli.cli("show clck")
            print(result)
            ```
    
    2. `clip()` Examples:
        
        1. Get and print to screen the result from a `clip()` function call with one IOS XE EXEC mode CLI command:
            
            ```
            import cli
            cli.clip("show clock")
            ```
        
        2. Get and print to screen the result from a `clip()` function call with multiple IOS XE EXEC mode CLI commands 
        delimited by semicolon:
            
            ```
            import cli
            cli.clip("show clock; show ip interface brief")
            ```
        
        3. Get and print to screen the result from a `clip()` function call with multiple IOS XE EXEC mode CLI commands 
        delimited by newline:
            
            ```
            import cli
            commands='''show clock
            sh ip interface brief
            '''
            cli.clip(commands)
            ```
        
        4. Get and print to screen the result from a `clip()` function call with multiple IOS XE configuration mode CLI 
        commands delimited by semicolon:
            
            ```
            import cli
            cli.clip("configure terminal; interface Loopback101; description Configured by Python clip function; ip address 10.10.10.101  255.255.255.255; no shutdown; end")
            ```
        
        5.  Get and print to screen the result from a `clip()` function call with one malformed IOS XE EXEc mode CLI 
        command (prints to screen error message):
            
            ```
            import cli
            cli.clip("show clck")
            ```
    
    3. `execute()` Examples:
        
        1. Get and print to screen the result from an `execute()` function call with one IOS XE EXEC mode CLI command:
            
            ```
            import cli
            result=cli.execute("show clock")
            print(result)
            ```
        
        2. Get and print to screen the result from an `execute()` function call with multiple malformed IOS XE EXEC 
        mode CLI commands delimited by semicolon (raises Python exception):
            
            ```
            import cli
            result=cli.execute("show clock; show ip interface brief")
            ```
        
        3. Get and print to screen the result from multiple `execute()` function calls in a Python for loop with 
        multiple IOS XE EXEC mode CLI commands:
            
            ```
            import cli
            commands = ["show clock", "show ip interface brief"]
            for c in commands:
                result=cli.execute(c)
                print(result)
            ```
        
        5.  Get and print to screen the result from an `execute()` function call with one malformed IOS XE EXEc mode 
        CLI command (raises Python exception):
            
            ```
            import cli
            result=cli.execute("show clck")
            ```
    
    4. `executep()` Examples:
        
        1. Get and print to screen the result from an `executep()` function call with one IOS XE EXEC mode CLI command:
            
            ```
            import cli
            cli.executep("show clock")
            ```
        
        2. Get and print to screen the result from an `executep()` function call with multiple IOS XE EXEC mode 
        CLI commands delimited by semicolon (prints to screen error message):
            
            ```
            import cli
            cli.executep("show clock; show ip interface brief")
            ```
        
        3. Get and print to screen the result from multiple `executep()` function calls in a Python `for` loop with 
        multiple IOS XE EXEC mode CLI commands:
            
            ```
            import cli
            commands = ["show clock", "show ip interface brief"]
            for c in commands:
                cli.executep(c)
            ```
        
        5.  Get and print to screen the result from an `executep()` function call with one malformed IOS XE EXEc mode 
        CLI command (prints to screen error message):
            
            ```
            import cli
            cli.executep("show clck")
            ```
    
    5. `configure()` Examples:
        
        1. Get and print to screen the result from a `configure()` function call with multiple IOS XE configuration 
        mode CLI commands delimited by newline:
            
            ```
            import cli
            commands = '''interface Loopback102
            description Configured by Python configure function
            ip address 10.10.10.102 255.255.255.255
            no shutdown
            end
            '''
            result=cli.configure(commands)
            print(result)
            ```
        
        2. Get and print to screen the result from a `configure()` function call with multiple IOS XE configuration 
        mode CLI commands passed as a Python list:
            
            ```
            import cli
            result=cli.configure(["interface Loopback103",
                                  "description Configured by Python configure function",
                                  "ip address 10.10.10.103 255.255.255.255",
                                  "no shutdown",
                                  "end"])
            print(result)
            ```
        
        3. Get and print to screen the result from a `configure()` function call with multiple malformed IOS XE 
        configuration mode CLI commands passed as a Python list (raises Python exception, with example error handling):
            
            ```
            import cli
            commands=["interface Loopback104",
                      "description Configured by Python configure function",
                      "ip 10.10.10.104 255.255.255.255",
                      "no shutdown",
                      "end"]
            try:
                result = cli.configure(commands)
                print("Success:\n")
                print(result)
            except cli.CLIConfigurationError as e:
                print "Failed configuration:\n"
                for failure in e.failed:
                    print(failure)
            ```
    
    6. `configurep()` Examples:
        
        1. Get and print to screen the result from a `configurep()` function call with multiple IOS XE configuration 
        mode CLI commands delimited by newline:
            
            ```
            import cli
            commands = '''interface Loopback105
            description Configured by Python configurep function
            ip address 10.10.10.105 255.255.255.255
            no shutdown
            end
            '''
            cli.configurep(commands)
            ```
        
        2. Get and print to screen the result from a `configurep()` function call with multiple IOS XE configuration 
        mode CLI commands passed as a Python list:
            
            ```
            import cli
            cli.configurep(["interface Loopback106",
                            "description Configured by Python configurep function",
                            "ip address 10.10.10.106 255.255.255.255",
                            "no shutdown",
                            "end"])
            ```
        
        3. Get and print to screen the result from a `configurep()` function call with multiple malformed IOS XE 
        configuration mode CLI commands passed as a Python list (prints to screen error message):
            
            ```
            import cli
            commands=["interface Loopback107",
                      "description Configured by Python configurep function",
                      "ip 10.10.10.107 255.255.255.255",
                      "no shutdown",
                      "end"]
            cli.configurep(commands)
            ```
3. Copy and paste the following Python code snippet into the Python interactive interpreter:
    
    ```
    quit()
    ```
