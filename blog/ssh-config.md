# Separate SSH keys for separate hosts

*May 13, 2021*

It is possible to use a single SSH key for multilpe remote hosts, but as soon as you start to think about this approach you'll find a lot of issues.

That's why you need `config` file in your `~/.ssh` folder - and it works for MacOs, Linux and Windows 10. `config` file format is not that complicated:

```
Host hostname_a
    SSH_Option options_value
    SSH_Option options_value

Host hostname_b
    SSH_Option options_value

Host hostname_c
    SSH_Option options_value
```

Let's say I have a machine with IP `11.22.33.44` in some cloud and private key `machine_a_in_cloud_1_key.pem` for it (by the way, put this file into `~/.ssh` folder). I need to add this lines to `~/.ssh/config` file

```
Host machine_a
    HostName 11.22.33.44
    IdentityFile ~/.ssh/machine_a_in_cloud_1_key.pem
    User your_user_name
```

And now you can do `> ssh machine_a` to connect to the remote machine!

If it's needed to override some value defined in `config`, it can be done with CLI arguments, for example `> ssh -o "User=another_user" machine_a`.

`config` file could define both all required parameters for a connection and only some subset:

```
Host machine_a
    HostName 11.22.33.44
    IdentityFile ~/.ssh/machine_a_in_cloud_1_key.pem
    User your_user_name

Host machine_b
    HostName my_machine_b.insomecloud.dev
    IdentityFile ~/.ssh/machine_b_key.pem
    User your_user_name_on_machine_b

Host machine_b_root
    HostName my_machine_b.insomecloud.dev
    IdentityFile ~/.ssh/machine_b_root_key.pem
    User root

Host subservice_a_*
    User user_for_subservice_a
    Port 1234

Host subservice_b_*
    User user_for_subservice_b
    Port 2345
```

Above you see an example where `machine_a` can be connected as it is, but two other hosts serve as templates and require additional parameters to be passed from terminal. Also it shows an example of how to create two connections to the same host but with two different users with separate keys.


