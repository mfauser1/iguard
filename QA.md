##IGuard

Frequently Asked Questions (FAQ)

#(0) How do I use IGuard?

Enable the IGuard firewall using the switch in IGuard's action bar Allow (greenish*) or deny (reddish*) Wi-Fi or mobile internet access using the icons next to an application name in IGuard's applications list You can use Settings > Defaults to change from block/blacklist mode (disable Block Wi-Fi and Block mobile, and then block unwanted applications in IGuard's applications list) to allow/whitelist mode (enable Block Wi-Fi and Block mobile, and then allow desired applications in IGuard's applications list).

Depending on the theme you use, the icons may be:
Allowed (internet access permitted): greenish (teal) / blue / purple / gray Blocked (internet access denied): reddish (salmon) / orange / yellow / amber

(1) Can IGuard completely protect my privacy?

No - nothing can completely protect your privacy. IGuard will do its best, but it is limited by the fact it must use the Android VPN service. This is the trade-off required to make a firewall which does not require root access. The firewall can only start when Android "allows" it to start, so it will not offer protection during early boot-up (although you can disable your network before rebooting). Also, the Android VPN service needs to be restarted to apply new rules when connectivity has changed or when the screen is being turned on or off. It will, however, be much better than nothing.

In the advanced options you can enable Seamless VPN handover on reload to prevent traffic from leaking when the Android VPN service is being restarted. However, this does not work properly on all Android versions/variants causing IGuard to hang and block all connections.

Android N and later allows IGuard to be an Always-On VPN. On Android O do not enable 'Block connections without VPN', see question 51) for more information on this.

To protect yourself more, remember to disable Wi-Fi and mobile data before rebooting, and only enable them on reboot, after the firewall service has started (and the key icon is visible in the status bar).

#(2) Can I use another VPN application while using IGuard

If the VPN application is using the VPN service, then no, because IGuard needs to use this service. Android allows only one application at a time to use this service.

IGuard is a firewall application, so there is no intention to add VPN support. However, IGuard supports a SOCKS5 proxy to chain VPN applications.

#(3) Can I use IGuard on any Android version?

No, the minimum required Android version is 5.1 (Lollipop)

#(4) Will IGuard use extra battery power?

By default IGuard will hardly use any battery power. All settings resulting in extra battery usage, like IP filtering and logging, have a warning. If IGuard uses a lot of battery power, please double check your settings.

The battery usage when IP filtering is enabled depends on the quality of your Android VPN service implementation and the efficiency of the processor of your device. Generally the battery usage on older devices might be unacceptable, yet hardly noticeable on modern devices with an efficient processor.

The network speed graph notification will use extra battery power. This is why the notification is shown only when the screen is on. You can decrease the update frequency using the settings to reduce the battery usage.

Note that Android often incorrectly contribute battery usage of other apps to IGuard, because the network traffic of other apps is flowing through IGuard. This means that it might look like IGuard is using a lot of battery power, but that in fact the total battery usage of all apps is still the same.

#(6) Will IGuard send my internet traffic to an external (VPN) server?

No, depending on the mode of operation basically one of two things will happen with your internet traffic:

When IP filtering is disabled, blocked internet traffic will be routed into the local VPN service, which will operate as a sinkhole (in effect dropping all blocked traffic) When IP filtering is enabled, both blocked and allowed internet traffic will be routed into the local VPN service and only allowed traffic will be forwarded to the intended destination (and not to a VPN server) The Android VPN service is being used to locally route all internet traffic to IGuard so no root is required to build this firewall application. IGuard, unlike all other no-root firewalls applications, is 100% open source, so when you are in doubt you can check the source code yourself.

#(7) Why are applications without internet permission shown?

Internet permission can be granted with each application update without user consent. By showing all applications, IGuard allows you to control internet access even before such an update occurs.

#(8) What do I need to enable for the Google Play™ store app to work?

You need 3 packages (applications) enabled (use search in IGuard to find them quickly):

com.google.android.gms (Play services) com.android.providers.downloads (Download manager) Since the Google Play™ store app has a tendency to check for updates or even download them all by itself (even if no account is associated), one can keep it in check by enabling "Allow when device in use" for all 3 of these packages. Click on the down arrow on the left side of an application name and check that option, but leave the network icons set to red (hence blocked). The little human icon will appear for those packages.

Note that IGuard does not require any Google service to be installed.

#(9) Why is the VPN service being restarted?

The VPN service will be restarted when you turn the screen on or off and when connectivity changes (Wi-Fi, mobile) to apply the rules with the conditions 'Allow when screen is on' and 'Block when roaming'.

See here for more details.

#(10) Will you provide a Tasker plug-in?

No, because if Tasker is allowed to disable IGuard, any application can disable IGuard. Allowing a security application to be disabled by other applications is not a good idea.

#(13) How can I remove the ongoing IGuard entry in the notification screen?

Long click the IGuard notification Tap the 'i' icon Depending on your device and/or ROM manufacturer's software customizations, you can be directed to either: the App Info screen and you can uncheck 'Show notifications' and agree to the next dialog the App Notifications screen and you can toggle the 'Block' slider to on Note that, whether or not you get a dialog warning to agree upon, this operation will also disable any information or warning notifications from IGuard, such as the new application installed notification.

To read about the need for the notification in the first place, see question 24.

Some Android versions display an additional notification, which might include a key icon. This notification, unfortunately, cannot be removed.

#(14) Why can't I select OK to approve the VPN connection request?

There might be another (invisible) application on top of the VPN connection request dialog. Some known (screen dimming) applications which can cause this are Lux Brightness, Night Mode, and Twilight. To avoid this problem, at least temporarily, close all applications and/or services which may be running in the background.

#(16) Why are some applications shown dimmed?

Disabled applications and applications without internet permission are shown dimmed.

#(17) Why is IGuard using so much memory?

It isn't. IGuard doesn't allocate any memory, except a little for displaying the user interface elements and for buffering traffic. It appears, on some Android variants, that the Google Play™ store app connection uses almost 150 MB. It is needed for in-app donations, and is incorrectly attributed to IGuard instead to the Google Play™ store app.

#(18) Why can't I find IGuard in the Google Play™ store app?

IGuard requires at least Android 5.1, so it is not available in the Google Play™ store app on devices running prior Android versions.

#(19) Why does application XYZ still have internet access?

If you block internet access for an application, there is no way around it. However, applications could access the internet through other (system) applications/components. For example, Google Play services receives incoming push messages and ads for most applications, including WhatsApp and Facebook messenger. You can prevent this by blocking internet access for the other application/component as well. You can block system applications and components, like Google Play services, by enabling the advanced IGuard option Manage system apps. This can best be diagnosed by checking the global access log (three dot menu, Show log).

Note that some applications keep trying to access the internet, which is done by sending a connection request packet. This packet goes into the VPN sinkhole when internet access for the application is blocked. This packet consists of less than 100 bytes and is counted by Android as outgoing traffic and will be visible in the speed graph notification as well.

#(20) Can I Greenify/hibernate IGuard?

No. Greenifying or otherwise hibernating IGuard will result in rules not being applied when connectivity changes from Wi-Fi/mobile, screen on/off, and roaming/not roaming.

#(21) Does doze mode affect IGuard?

I am not sure, because the doze mode documentation is not clear if the Android VPN service will be affected.

To be sure, you can disable battery optimizations for IGuard manually like this:

Android settings > Battery > three dot menu > Battery optimizations > Dropdown > All apps > IGuard > Don't optimize > Done The procedure to accomplish this can vary between devices.

Disabling doze mode for IGuard cannot be done from within IGuard because, according to Google, IGuard is not an application type allowed to do this.

#(22) Can I tether (use the Android hotspot) / use Wi-Fi calling while using IGuard?

Yes, but you'll need to enable subnet routing and tethering in the IGuard network settings. Whether or not it works depends on your Android version because some Android versions have a bug preventing tethering and the VPN service working together.

Some devices hibernate Wi-Fi, preventing tethering from working when the screen is off. This behavior can be disabled in the Android enhanced/advanced Wi-Fi settings.

#(24) Can you remove the notification from the status bar?

Android can kill background services at any time. This can only be prevented by turning a background service into a foreground service. Android requires an ongoing notification for all foreground services to make you aware of potential battery usage (see question 4). So, the notification cannot be removed without causing instability. However, the notification is being marked as low priority, which should result in moving it to the bottom of the list.

The key icon and/or the VPN running notification, which is shown by Android and not by IGuard, unfortunately, cannot be removed. The Google documentation states: "A system-managed notification is shown during the lifetime of a VPN connection".

Android 8 Oreo and later display a notification "... running in the background" listing all apps running in the background. You can't disable this notification, but you can remove the icon from the status bar like this:

Open Settings > Apps & notifications > App info Open settings (three dots); Select "Show system" Select "Android System" Select "App notifications" Select "Apps running in background" Select "Importance" and select "Low" #(25) Can you add a 'Select All' function?

There is no need for a 'Select All' function because you can switch from block (blacklist) to allow (whitelist) mode using IGuard's settings. See also question 0.

#(27) How do I read the blocked traffic log?

The columns have the following meanings:

Time (tap on a log entry to see the date) Application icon (tap on a log entry to see the application name) Application UID Wi-Fi / mobile connection, green=allowed, red=blocked Interactive state (screen on or off) Protocol (see below) and packet flags (see below) Source and destination port (tap on a log entry to lookup a destination port) Source and destination IPv4 or IPv6 address (tap on a log entry to lookup a destination IP address) Organization name owning the IP address (needs to be enabled via the menu) Protocols:

HOPO (IPv6 Hop-by-Hop Option) ICMP IGMP ESP (IPSec) TCP UDP Number = one of the protocols in this list 4 = IPv4 6 = IPv6 Packet flags:

S = SYN A = ACK P = PSH F = FIN R = RST For a detailed explanation see here.

Only TCP, UDP, and ICMP ping traffic can be routed through the Android VPN service. All other traffic will be dropped and will be shown as blocked in the global traffic log. This is almost never a problem on an Android device.

#(28) Why is Google connectivity services allowed internet access by default?

The Google connectivity services system application checks if the current network is really connected to the internet. This is probably accomplished by briefly connecting to some Google server.

If this is not the case, there will be an '!' in the Wi-Fi or mobile icon in the system status bar.

Recent Android versions seem not to switch connectivity from mobile to Wi-Fi when the Wi-Fi network is not really connected, even though there is a connection to the Wi-Fi network (or the other way around). On Android 6.0 and later you might get a notification asking you if you want to keep this connection on or not. To prevent a bad user experience, IGuard includes a predefined rule to default allow the Google connectivity services.

You can find all predefined rules here.

You can override predefined rules.

#(29) Why do I get 'The item you requested is not available for purchase'?

You can only purchase pro features when you have installed IGuard from the Google Play store.

#(30) Can I also run AFWall+ on the same device?

Unless you are just testing IGuard, there is no current reason to use them both, since they cover the same function (firewall), although with different base needs (AFWall+ needs a rooted device) and ways of doing their thing (AFWall+ uses iptables whereas IGuard uses a VPN).

Also you need to keep per application access rules always in sync between AFWall+ and IGuard, else the application will not be able to access the network, hence bringing another level of complexity when setting and assuring everything work as expected.

Some pointers on how to set up AFWall+ to be used simultaneously with IGuard:

if not using filtering in IGuard, applications need direct internet access (Wi-Fi and/or mobile) in AFWall+ if using filtering, IGuard will need internet access (Wi-Fi and/or mobile) in AFWall+ if using filtering, when you un/reinstall IGuard, remember to re-allow IGuard in AFWall+ if using filtering, applications need VPN internet access (check the box to show that option in AFWall+ settings) This question was community contributed. There is no support on using IGuard and AFWall+ together.

#(31) Why can some applications be configured as a group only?

For many purposes, including network access, Android groups applications on UID and not on package/application name. Especially system applications often have the same UID, despite having a different package and application name; these are set up like this by the ROM manufacturer at build time. These applications can only be allowed/blocked access to the internet as a group.

#(32) Why is the battery/network usage of IGuard so high?

This is because Android counts battery and network usage which is normally counted for other applications against IGuard in IP filtering mode. The total battery usage is slightly higher when IP filtering mode is enabled. IP filtering mode is always enabled on Android versions prior to 5.0, and optionally enabled on later Android versions.

#(33) Can you add profiles?

Profiles are inconvenient because they need to be operated manually. Conditions like 'When screen is on' are, on the other hand, convenient because they work automatically. Therefore profiles will not be added, but you are welcome to propose new conditions; however, they need to be generally usable to be included.

As a workaround you can use the export/import function to apply specific settings in specific circumstances. Alternatively, you can use lockdown mode as a profile.

#(34) Can you add a condition 'when on foreground' or 'when active'?

Recent Android versions do not allow an application to query if other applications are in the foreground/background or active/inactive without holding an additional privacy violating permission and at the expense of extra battery usage (because periodic polling is required). As a result, this cannot be added without significant disadvantages, like this one. You can use the condition 'when screen is on' instead.

#(35) Why does the VPN not start?

IGuard "asks" Android to start the local VPN service, but some Android versions contain a bug which prevents the VPN from starting (automatically). Sometimes this is caused by updating IGuard. Unfortunately this cannot be fixed by IGuard. You can try to restart your device and/or revoke the VPN permissions from IGuard using the Android settings. Sometimes it helps to uninstall and install IGuard again (be sure to export your settings first!).

#(36) Can you add PIN or password protection?

Since turning off the VPN service using the Android settings cannot be prevented, there is little use in adding PIN or password protection.

#(38) Why did IGuard stop running?

On most devices, IGuard will keep running in the background with its foreground service. On some devices (in particular some Samsung models), where there are lots of applications competing for memory, Android may still stop IGuard as a last resort. Some Android versions, in particular of Huawei (see here for a fix) or Xiaomi (see here for a fix) stop apps and services too aggressively. Unfortunately this cannot be fixed by IGuard, and can be considered a shortcoming of the device and/or as a bug in Android. As a matter of fact lots of apps suffer from this, see the website Don't kill my app! for more information and solutions. You can workaround this problem by enabling the watchdog in the IGuard advanced options to check every 10-15 minutes.

#(39) How does a VPN based firewall differ from a iptables based firewall?

See this Stack Exchange question.

#(40) Can you add schedules?

Besides not being trivial to add, schedules - in my opinion - are not a good idea, since time is not a good rule condition. A rule condition like When screen is on is a better and more straightforward condition. Therefore schedules will not be added, but you are welcome to propose other new conditions.

#(41) Can you add wildcards / address/port ranges?

Wildcards to allow/block addresses and address/port ranges would have a significant performance and usability impact and therefore will not be added. Wildcards rules and address/port ranges would need to be checked for each and every connection attempt. Since IGuard blocks, unlike any other no-root firewall, domain names instead of IP addresses there is hardly a need for wildcards.

#(42) Why is permission ... needed?

INTERNET ('Full network access'): to forward allowed (filtered) traffic to the internet ACCESS_NETWORK_STATE ('View network connections'): to check if the device is connected to the internet through Wi-Fi READ_PHONE_STATE ('Device ID & call information'): to detect mobile network changes, see here for more details ACCESS_WIFI_STATE ('Wi-Fi connection information'): to detect Wi-Fi network changes RECEIVE_BOOT_COMPLETED ('Run at startup'): to start the firewall when booting the device WAKE_LOCK ('Prevent device from sleeping'): to reliably reload rules in the background on connectivity changes VIBRATE: to provide vibration feedback on widget tap FOREGROUND_SERVICE ('foreground service'): to run a foreground service on Android 9 Pie and later #(43) I get 'This app is causing your device to run slowly'

This message is displayed by the Smart Manager, but actually it is the 'Smart' Manager application itself which is causing delays and lags. Some links:

Smart Manager complaining about LastPass Disable Smart Manager? #(44) I don't get notifications on access

To prevent a high number of status bar notifications, notify on access is done only once per domain name per application. Access to domain names shown in the application access log (drill down in the IGuard application settings) will not be notified again, even if you just enabled notify on access. To get notified for all domain names again, you can clear the application access log using the trashcan icon. If you want to clear all applications logs, you can export and import your settings.

Another reason why you don't get notifications could be an applied "Power Saving Mode" for example on Samsung devices. Even if you do not restrict CPU frequency in this mode.

#(45) Does IGuard handle incoming connections?

The Android VPN service handles outgoing connections only (from applications to the internet), so incoming connections are normally left alone.

If you want to run a server application on Android, then be aware that using port numbers below 1024 require root permissions and that some Android versions contain routing bugs, causing inbound traffic incorrectly being routed into the VPN.

#(46) Can I get a refund?

If a purchased pro feature doesn't work as described and this isn't caused by a problem in the free features and I cannot fix the problem in a timely manner, you can get a refund. In all other cases there is no refund possible. In no circumstances there is a refund possible for any problem related to the free features, since there wasn't paid anything for them and because they can be evaluated without any limitation. I take my responsibility as seller to deliver what has been promised and I expect that you take responsibility for informing yourself of what you are buying.

#(48) Why are some domain names blocked while they are set to be allowed?

IGuard blocks traffic based on the IP addresses an application is trying to connect to. If more than one domain name is on the same IP, they cannot be distinguished. If you set different rules for 2 domains which resolve to the same IP, both will be blocked.

Another potential problem is that Android doesn't honor the DNS TTL value and applies its own caching rules. This could result in IGuard too early or too late purging a DNS record from its own cache, resulting in not recognizing an IP address or recognizing a wrong IP address. You can try to workaround this by changing the DNS TTL value setting of IGuard. This value is used as a minimum DNS TTL value in an attempt to mimick the behavior of Android.

IGuard will also block traffic while restarting the Android VPN service to apply new rules, for example when connectivity changes or when the screen is turned on or off.

#(49) Does IGuard encrypt my internet traffic / hide my IP address?

IGuard is a firewall application that filters internet traffic on your device (see also this question), so it is not meant to - and does not - encrypt your internet traffic or hide your IP address.

#(50) Will IGuard automatically start on boot?

Yes, IGuard will automatically be started on boot if you powered off your device with IGuard enabled and IGuard is not installed on external storage.

Some devices, for example OnePlus and Mi devices, can prevent certain apps from auto-starting after reboot. This can be disabled in the Android settings.

#(51) Why does IGuard block all internet traffic?!

Make sure you have put IGuard on the doze exception list (Android 6 Marshmallow or later) and that Android allows IGuard to use the internet in the background (see also this question).

Make sure you are not running IGuard in allow (whitelist) mode (check the IGuard default settings).

Make sure you didn't enable the Always-On VPN setting 'Block connections without VPN' (Android 8 Oreo or later). This will block resolving domain names too (is it a bug or feature?).

Some Android versions, including LineageOS for some devices, contain a bug resulting in all internet traffic being blocked. Mostly, you can workaround this bug by enabling filtering in IGuard's Advanced options. If this doesn't solve the issue, the problem can unfortunately not be fixed or worked around by IGuard.

#(52) What is lockdown mode?

In lockdown mode, all traffic for all applictions will be blocked, except for applications with the condition 'Allow in lockdown mode' enabled. You can use this mode to limit battery usage or network usage, for example, when your battery is almost empty or when your data allotment is almost exhausted. Note that system applications will only be blocked in this mode when managing system applications is enabled in the advanced settings.

You can enable/disable lockdown mode in the main menu, using a widget, or using a settings tile (Android 7 Nougat or later).

#(53) The translation in my language is missing / incorrect / incomplete

You can contribute translations here (registration is free). If your language is missing, please contact me to have it added.

#(54) How to tunnel all TCP connections through the Tor network?

Tor with IGuard is only supported in the XDA IGuard forum. There is no personal support on Tor with IGuard, because I don't use Tor myself.

First, install Orbot, the Android client for Tor, run it, press Start, while it connects open its Settings and make sure it's setup to auto-start on device start.

In IGuard's Network options enable Subnet routing and in Advanced options toggle on Use SOCKS5 proxy with address 127.0.0.1 and port as 9050 (this is the default port, if you changed this in Orbot make the adjustment here also).

This should be enough, if testing fails (eg. no connection at all) you can open the app details for Orbot, uncheck Apply rules and conditions and retry.

How to test: open Firefox (or another non-proxy enabled browser) to the address https://ipleak.net/ and you should see a different IP address from your regular one, and below in the Tor Exit Node field something else besides Unknown.

Be aware that all the other Tor caveats (https://www.torproject.org/docs/faq.html.en) still apply, like having the Tor network unreacheable, your activity actively monitored/targeted in your country, online services (eg. Gmail, Google Play store) failing to login or being forced to solve endless capchas when accessing sites that use Cloudflare's CDN services.

#(55) Why does IGuard connect to Amazon / ipinfo.io / 216.239.34.21?

IGuard connects to Amazon / ipinfo.io to show the names and organizations for IP addresses. If you don't want this, just disable showing names and organizations using the three dot menu in the global log view.

#(56) Why does IGuard allow all internet traffic?!

IGuard can block each and every application, even system applications and components.

IGuard, by default, allows all traffic to prevent hard to find problems. You need to selectively block traffic yourself by tapping on the mobile or Wi-Fi icons.

Be aware that IGuard will allow traffic to an application when the screen is on and the condition 'when screen on' is enabled.

#(57) Why does IGuard use so much data?

Basically, IGuard doesn't use data itself. However, many Android versions incorrectly account data of other applications flowing through IGuard to IGuard instead of to the applications. The data usage of other applications will be zero with IGuard enabled in this case.

The total data usage of your device will be the same with and without IGuard.

(58) Why does loading the application list take a long time?

The application list is provided by Android, so the loading speed depends mostly on the power of your device and on the efficiency of your Android version. For example shortage of memory could lead to increased loading times, because memory needs to be freed, for example by pausing other applications.

In some circumstances, restricting system apps and system components is known to cause the application list to load slowly or not at all. The exact circumstances are unknown.

(59) Can you help me restore my purchase?

Google manages all purchases, so as developer I have no control over purchases. So, the only thing I can do, is give some advice:

Make sure you have an active internet connection Make sure you didn't block Google Play store / Play services Make sure you are logged in with the right Google account and that there is nothing wrong with your Google account Open the Play store application and wait at least a minute to give it time to synchronize with the Google servers Open IGuard and navigate to the pro features screen; IGuard will check the purchases again You can also try to clear the cache of the Play store app via the Android apps settings.

Note that:

Purchases are stored in the Google cloud and cannot get lost There is no time limit on purchases, so they cannot expire Google does not expose details (name, e-mail, etc) about buyers to developers An application like IGuard cannot select which Google account to use If you cannot solve the problem with the purchase, you will have to contact Google about it.

#(60) Why does IP (Wi-Fi) calling/SMS/MMS not work?

Please see the compatibility section about this (you might need to request the desktop version to see this section if you are using a mobile device).

#(61) Help, IGuard crashed!

IGuard rarely crashes ("unexpectedly stopped"), but if it crashed (which is something different than being stopped by Android, see this FAQ), then it is mostly caused by bugs in your Android version (either in the Android VPN service implementation or in the Android Linux kernel). I am happy to check what the cause of a crash is and I will fix it whenever possible, but I need a logcat captured from your PC with the crash log for this. Since logcats are mostly quite large, I will need the exact time of the crash as well. If you don't know how to capture a logcat from your PC, please use your favorite search engine to find one of the numerous guides.

#(62) How can I solve 'There was a problem parsing the package' ?

Likely causes are that the downloaded APK file is damaged (which could be caused by a virus scanner) or that you are trying to install IGuard on a not supported Android version.

#(63) Why is all DNS traffic allowed?

IGuard blocks unlike any other Android firewall on real domain names. For this a list of domain names and IP address needs to be built. For this purpose, IGuard allows all DNS traffic, even if the domain name is listed in the hosts file. However, this doesn't mean traffic to the resolved IP address is allowed.

If you don't trust the system (Google's) or your provider's DNS servers, you can set alternative DNS servers in the advanced settings. Be sure to enter and confirm the addresses and to set two DNS server addresses. If you enter just one DNS server address, it will be used in addition to the default DNS server addresses.

#(64) Can you add DNS over TLS?

If you mean to intercept DNS over TLS requests to resolve domain names, this is not possible because DNS over TLS traffic is encrypted, which is the whole point of DNS over TLS.

If you mean to translate plain DNS to DNS over TLS, Android 9 Pie and later already support DNS over TLS out of the box, so it isn't worth the significant effort to add this.

#(65) Why can IGuard not block itself?

First of all, if IGuard could block itself, you should trust that IGuard really blocks itself, which is basically the same as trusting that IGuard doesn't connect to the internet when not needed.

Note that IGuard needs to connect to the internet to forward traffic of other apps to the internet and to lookup information on IP addresses, see also this FAQ.

IGuard could block itself in older versions, but this required calling VpnService.protect for each and every connection. Since there are lots of connections of lots of apps in a typical Android environment, this resulted in wasting battery power and in crashes on some Android versions with bugs in this function.

So, because blocking IGuard with itself didn't added anything useful and to save on battery power and to prevent crashes blocking IGuard with itself was removed.

#(66) Why is a blocked app still accessing the internet?

Blocked apps cannot access the internet. There are no exceptions to this.

However:

Apps can show locally cached content Incoming (push) messages are received by the system component Google Play services and not apps, especially when the app is in the background or when the screen is turned off Similarly, advertisements are mostly received by the system component Google Play services Downloads are often performed by the download manager and not apps If you like to block Google Play services or the download manager, you'll need to enable managing system apps in the advanced settings.

To be clear: in most cases you cannot block ads by blocking apps. However, you can block ads for all apps with IGuard, please see here about how to.
