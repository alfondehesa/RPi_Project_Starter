# 2 - Connect Trough SSH

## Table of contents

- [ ] [Summary](2%20-%20Connect%20Through%20SSH.md#summary)
- [ ] [Connect through SSH](2%20-%20Connect%20Through%20SSH.md#connect-through-ssh)
- [ ] [Next Steps](2%20-%20Connect%20Through%20SSH.md#next-steps)

## Summary

Once you have installed your **OS**, you will need to **interface with your Pi**. In a **headless setup** (no monitor or keyboard), this can be done **remotely through `ssh`**. **SSH** stands for "**secure shell**", and is a method of essentially **sending and receiving commands remotely to the Pi from your terminal window in your own computer**. It is equivalent to typing commands through keyboard directly to the **Pi**.
> [!IMPORTANT]
> *For this step you will need to be connected to the same network as your Pi.*

## Connect through SSH

- [ ] Find the **IP address of the Pi**.
    > [!NOTE]
    >
    > - *To do this, access your router (usually by typing in `192.168.1.1` or `10.0.0.1` in a browser) and see the IP addresses of devices connected to your network. Most routers also show the network name, so if you used the RPi imager and you gave your Pi a unique network name you will be able to identify your Pi.*
    > - *Alternatively, you can run: `nmap -sn 192.168.1.0/24` in a UNIX terminal to scan your network for every IP address connected to it. If you do this once with the Pi unpowered, and once with the Pi plugged in (allow some time for booting up), you might be able to notice new IP addresses that weren't there before. One of those is likely to be your Pi.*

- [ ] Once you have found the IP address of your Pi, with your Pi on, **open a terminal in your computer and run**: `shh [YOUR_USER_NAME]@[THE_PI_IP_ADDRESS]`. **Don't** include the crochets (`[]`).
    > [!NOTE]
    > *If you used the RPi imager, the username will be the one you set up for ssh. Otherwise, it will be the default `pi`.*

- [ ] If your **Pi is online** and the **IP address is correct**, it will ask you for a **password** (might also ask you for a confirmation that the device you are connecting to is safe if it's the first time you connect to it). **Type in your password and hit enter**.
    > [!WARNING]
    > **If you used the RPi imager, the password will be whatever password you set up. If you didn't, then it will be the default `raspberry`. Note that the defaults might not work (will show up as access denied) if you didn't use the RPi imager, and you will need to set up a user account manually by connecting a keyboard and monitor to the RPi before connecting through SSH.**

- [ ] The Pi will then **boot up** in your home directory. You will see your username and path on the left of your cursor. You can run `clear` and hit enter to clear previous commands.

## Next Steps

- Although optional, it is **highly recommended** setting up a permanent IP address for your Pi to not have to repeat these steps every time the Pi reconnects to your network.

  - For instructions on how to do so, visit [2.1 - Set up a permanent IP Address](2.1%20-%20Set%20up%20a%20permanent%20IP%20Address.md)

- After setting up a static IP address, you might want to access your Pi from **outside your network**.

  - For instructions on how to do so, visit [2.2 - Remote SSH (from anywhere)](2.2%20-%20Remote%20SSH%20(from%20anywhere).md)

- Alternatively, you can skip the two previous sections.

  - Go straight to [3 - Installing Packages](3%20-%20Install%20Necessary%20Packages.md)

- [Back to README](README.md)
