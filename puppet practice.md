[root@ansible-masternode kranthi]# cat /etc/puppetlabs/code/environments/production/manifests/site.pp
#node 'ansible-controlnode1.local' { # Applies only to mentioned node; if nothing mentioned, applies to all
#file { '/tmp/puppetesttdir': # Resource type file
# ensure => 'directory', # Create as a diectory
# owner => 'root', # Ownership
# group => 'root', # Group Name
# mode => '0755', # Directory permissions
#}
#}

node 'ansible-controlnode.local' { # Applies only to mentioned node; if nothing mentioned, applies to all
$packages=['git','sysstat']
#package{'sysstat':
package{$packages:
ensure => installed,
}

$test="ok"
file {'/tmp/status.txt':
content => $test,
#content => 'installed',
mode => '0644'
}

#create user
#class user{
#user{'kranthi1':
#ensure=>present,
#uid=>'1101',
#shell=>'/bin/bash',
#}
#}

#class{user:}
$username="kranthi1"
#class user_account($username){
user{$username:
ensure => present,
uid => '1011',
shell => '/bin/bash',
home => "/home/$username",
}
#}

#class{user_account:
#username=>"kranthi1"
#}
}
[root@ansible-masternode kranthi]#
