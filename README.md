ansible-role-tbb
==================

This [Ansible](http://www.ansible.com) role helps to download and verify [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en) (TBB) in GNU/Linux.

The idea is the same as [Tor Browser Launcher](https://github.com/micahflee/torbrowser-launcher) (see advice below).

Requirements
------------

Ansible 1.6 or higher.

Project variables
------------------

Add or modify the following variable in playbook.yml

Optional variables (not included in defaults/main.yml):

* `tbb_older_dir`: path of an older version of TBB to import the bookmarks from. It will be used when `import_settings` variable is true (default). For instance:
    tbb_older_dir: /home/user/.tbb/tbb/tor-browser-linux32-3.6.1_en-US
* `tor_control_pw`: password for tor control port. It will be used when `use_system_tor` variale is true default)

Variables you might want to change (defined in defaults/main.yml:

    # the user for which tbb will be installed
    tbb_user: user

    ## if tor is already running, this variable will download everything through Tor
    ## TODO: detect whether tor is already running
    use_tor: true

    ## to use the system tor instead of the tbb tor
    use_system_tor: true

    ## in case of running system tor with a different socks port to the default
    tor_socks_port: 9050
    ## in case of running system tor with a different control port to the default
    tor_control_port: 9051
    ## to create the hashed tor control password and modify torrc with it.
    ## it requires sudo password.
    configure_torrc: false

    ## to import some settings (currently bookmarks) from other tbb installation 
    import_settings: true

    ## to install the package dependencies. It will require sudo password
    ## If they are not already installed and this variable is false, everythinhg will fail
    install_deps: false
                                                                                
    ## to setup noscript                                                             
    setup_noscript: true 

    # the system architecture (23 or 64 bits)
    tbb_arch: 32
    # the tbb language
    tbb_lant: en-US


Example Playbook                                                                
----------                                                                      
                                                                                
This role is intended to be run with the an ansible project ansible-prj-tbb.                                      
                                                                                
```                                                                             
- hosts: localhost                                                              
  roles:
    - { role: ansible-role-tbb,
        tbb_older_dir: pathtoanolderversionoftbb,
        tor_control_pw: controlportpw
      }                                                                                
```                            

                                                                                
License                                                                         
-------                                                                         
                                                                                
GPLv3                                                                           
                                                                                
Author Information                                                              
------------------                                                              
                                                                                
Lee Woboo

Advice
---------

Unles you're looking to experiment, use something better mantained and reviewed as Torbrowser Launcher.    
