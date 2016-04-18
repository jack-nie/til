###Error: Agent admitted failure to sign

In rare circumstances, connecting to GitHub via SSH on Linux produces the error "Agent admitted failure to sign using the key". Follow these steps to resolve the problem.

####Overview

When trying to SSH into GitHub on a Linux computer, you may see the following message in your terminal:

  ssh -vT git@github.com
  ...
  Agent admitted failure to sign using the key.
  debug1: No more authentication methods to try.
  Permission denied (publickey).
  For more details, see this issue report.

####Resolution

You should be able to fix this error by loading your keys into your SSH agent with ssh-add:

  # start the ssh-agent in the background
  eval "$(ssh-agent -s)"
  Agent pid 59566
  ssh-add
  Enter passphrase for /home/you/.ssh/id_rsa: [tippy tap]
  Identity added: /home/you/.ssh/id_rsa (/home/you/.ssh/id_rsa)

If your key does not have the default filename (/.ssh/id_rsa), you'll have to pass that path to ssh-add:

  # start the ssh-agent in the background
  eval "$(ssh-agent -s)"
  Agent pid 59566
  ssh-add ~/.ssh/my_other_key
  Enter passphrase for /home/you/.ssh/my_other_key: [tappity tap tap]
  Identity added: /home/you/.ssh/my_other_key (/home/you/.ssh/my_other_key)
