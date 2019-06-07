This is the hands-on workshop guide for Cisco Live US 2019 attendees.  Follow along with the presentation and copy 
and paste the commands or code snippets.

---

TODO:

* [ ] Download ex01.py and ex02.py to each csr1.

---

1. Login and navigate to the [Python WebUI Sandbox](https://198.18.134.11/webui/#/python) at `https://198.18.134.11/webui/#/python`.
    
    * Username: `admin`
    * Password: `C1sco12345`

2. Login to the IOS XE device `csr1` with the following Bash CLI command in macOS `Terminal.app`:
    
    ```
    ssh admin@198.18.134.11
    ```
    
    * Username: `admin`
    * Password: `C1sco12345`
    
    Copy and paste the following IOS XE EXEC mode command:
    
    ```
    guestshell run python
    ```
    
    Copy and paste the following Python code snippet into the Python interactive interpreter:
    
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

3. Copy and paste the following IOS XE EXEC mode command:
    
    ```
    guestshell run python ex01.py
    ```

4. Copy and paste the following IOS configuration mode commands:
    
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

5. Copy and paste the following IOS XE EXEC mode command:
    
    ```
    guestshell run python
    ```
    
    Copy and paste the following Python code snippet into the Python interactive interpreter: 
        
    * `cli()` Examples
        
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
    * `clip()` Examples:
        
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
    * `execute()` Examples:
        
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
    * `executep()` Examples:
        
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
    * `configure()` Examples
        
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
    * `configurep()` Examples:
        
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
