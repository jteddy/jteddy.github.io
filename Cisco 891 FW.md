# Cisco C891 FW 

## Password Recovery

Using OSX the break key is "Command-A then Command-B"

1. In the first 60 seconds send a break command 

2. You will enter rommon mode

3. Issue the below command

4. ```
  rommon 1 > confreg 0x2142

  You must reset or power cycle for new config to take effect
  rommon 2 > reset```

5. Type `no` after each setup question, or press `Ctrl-C` in order to skip the initial setup procedure.

6. Type `enable` at the `Router>` prompt.

7. Type `configure memory` or `copy startup-config running-config` in order to copy the nonvolatile RAM (NVRAM) into memory.

8. Type `show running-config`.

9. Type `configure terminal`.

10. Type `enable secret <password>` in order to change the enable secret password. For example: `hostname(config)#enable secret cisco`

11. Issue the `no shutdown` command on every interface that you use.

12. `config-register 0x2102`

13. `end`

14. Type `write memory` or `copy running-config startup-config` in order to commit the changes.



What if AAA is enabled?

1. After issuing `configure terminal` in step 9 above

2. Create a user with a password `username cisco password cisco`

3. `aaa authentication login default local`

4. Configure local auth on console port

   ```
   line con 0
   login authentication local
   ```
