# Openrazer installation - ERRORS

If you posses razer device(s), and proceeded to install openrazer-daemon and dependencies to customise later on, via front-end GUI applications such as:
- Polychromatic
- RazerGenie
- Snake
- RazerCommander

OR the CLI front-end *razer-cli*.

---

[I'll do *Polychromatic* in this instance - (This was my front-end app of choice for openrazer)]
---

You will find there is no communication or errors in the communication between the application and *OpenRazer*.

You will click on the troubleshoot, and get directed to a window full of steps and some of them will be on green  coloured "passed", hinting it passes some test.
Whilst others may have a "Failed" on red. For me it was the step involving the module `openrazer-driver`.

### Kernel modules - Are they built properly (ERROR!)?

The suggestion was to run the command `sudo dkms install openrazer-driver/x.x.x`
Then getting an error such as:

```  
Error! Could not find module source directory
Directory: /usr/src/openrazer-driver-x.x.x does not exist
```

Another step I failed as per *Polychromatic* troubleshoot tester, was the one involving the loading of the kernel modules.

### Kernel Modules - Do they load properly (ERROR!)?

In this step, I was suggested to run the command:
`sudo modprobe razerkbd`

*OUTPUT:*
`modprobe: FATAL: Module razerkbd not found in directory`

Which hinted the driver is not installed for this kernel by a quick google search.


To make this short and simplify it more than what it is in reality, I tried to focus on the daemon component.
Which apparently I was running one version behind the one I had to use.

A quick search on the internet, and scrolling a bit further down, and due to a more broader time-window I could have the sport to finally address this headache
of situation mainly due to my short time-window.
One of the key steps I was failing and I focused the most was the daemon version. Which hinted I was using an outdated one.

I spent some time with the `github.com/openrazer/openrazer/wiki/Troubleshooting`
And decided to aim the focus to the Polychromatic website a bit more.
In the `Arch Linux` install, there are two sections:
- Release
- Preview

I explored the preview, and I scrolled down to the Openrazer section, where it says.
"If your device is supported or fixed in an unreleased version, install openrazer-daemon git, openrazer-driver-dkms git, etc..."

I also clicked on the `suitable kernel headers` url link that directs you to -> `https://archlinux.org/packages/?sort=&repo=Core&repo=Extra&q=linux+-headers&maintainer=&flagged=`
And decided to install the `linux-lts-headers` since I did get errors hinting this to be an issue.

Proceeded to install the unreleased or latest versions which are included in:
- polychromatic-git
- openrazer-daemon-git
- openrazer-driver-dkms-git
- python-openrazer-git

from the AUR.

then `sudo gpasswd -a $USER plugdev`

reboot the computer, and my issues were gone!

The `-git` versions of those packages, would uninstall the "outdated" versions making you experience the errors, once you decide to install them.
You'll see it.
:)

----

# Conclusion 

I just wanted make this, since I did not find some good source to this solution straight to the point.
And I'm honestly new to Arch, so I also wanted to share this to anyone new to Arch who is experiencing this kind of issues.

