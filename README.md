
ssh-auth-id
===========

You're logged onto an EC2 instance, working on a problem with your fellow devs, and you want to invite them to log in and take a look at these crazy log messages. What do?

Oh. You have to ask them to cat their public SSH key, paste it into IRC (wait, no, it's id\_rsa.pub, not id\_rsa silly!) then you copy it and cat it to the end of authorized\_hosts.

That's where ssh-auth-id comes in. With ssh-auth-id, you can add the public SSH keys from a known, trusted online identity to grant SSH access.

Currently supported identities include Launchpad (https://launchpad.net) and of course, Github!


Usage
-----

ssh-auth-id uses short prefix to indicate the location of the online identity. For now, these are:

	'gh:' for Github
	'lp:' for Launchpad

 usage: ssh-auth-id [-h] [-o FILE] USERID [USERID ...]

 Authorize SSH public keys from trusted online identities.

 positional arguments:
   USERID                User IDs to import

 optional arguments:
   -h, --help            show this help message and exit
   -o FILE, --output FILE
                         Write output to file (default ~/.ssh/authorized_keys)

Example
-------

 $ ssh-auth-id gh:cmars

Would grant me access to log into your machine. Rather, it would grant access to the public keys I have registered with Github. So, you probably don't want to do that, since you're not paying me to look at those logs... but you get the idea.

Used with care, it is a great collaboration tool!


Credits
-------

This project is a port of https://launchpad.net/ssh-import-id, written by Dustin Kirkland.

