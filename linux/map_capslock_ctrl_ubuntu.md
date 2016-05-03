###How do I remap the Caps Lock and Ctrl keys?

open the following for editing:

  ```
  sudo vi /etc/default/keyboard
  ```
And edit

  ```
  XKBOPTIONS="ctrl:swapcaps"
  ```

Then, reconfigure:

  ```
  sudo dpkg-reconfigure keyboard-configuration
  ```
or

  ```
  /usr/bin/setxkbmap -option "ctrl:swapcaps"

  ```

