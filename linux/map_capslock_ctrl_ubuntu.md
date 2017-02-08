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
  
  ```
  setxkbmap -option caps:none
  ```

You can also use other options instead of “caps:none”:

```

caps:numlock – Caps Lock becomes an additional Num Lock.

caps:swapescape – Caps Lock becomes Escape, and Escape becomes Caps Lock

caps:escape – Caps Lock becomes an additional Escape.

caps:backspace – Caps Lock becomes an additional Backspace.

caps:super – Caps Lock becomes an additional Super. (Super is also known as the Windows key.)
```
