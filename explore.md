## Deeper ##

Once the ES File Explorer File Manager has been launched on an android device it opens TCP port 59777 and leaves it open. By curling to the port and ip you can execute commands through the data property of a POST request:

	curl --header "Content-Type: application/json" --request POST --data '{"command":"[my_awesome_cmd]"}' http://192.168.0.8:59777
	
This gives us access to a SSH server(android device) which allows us to connect to Port 5555 on the same server. We can bridge to that port from our own machine. We can now use adb connect. Note that the device needs to be in debug mode in order for this to work. SU Root allows user root access to the device but adb root allows access to the adbd daemon running on the phone with root rights. It does this because adb creates a shell instance on a device a sends output to the client. The new sell instance created by the DAEMON inherits the rights of the DAEMON. This can be easily achieved if ro.debuggable=1 in the default.prop file is set. This tells adbd that it can as root. More often than not, shell access and the lower priviledge of the user though.

ssh kristi@<ip address> -L 5555:localhost:5555 -p 2222


## Resources ##
[[https://www.apriorit.com/dev-blog/255-android-rooting]]
[[https://harrisonsand.com/posts/patching-adb-root/]]

