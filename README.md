# Ubuntu-20.04-pomodoneapp-fix
PomoDoneApp throw an error when try run on Ubuntu 20.04 or Pop!_OS 20.04, this one fix it.

### Issues:
#### [PomoDoneApp won't run on Ubuntu 20.04 & Pop!_OS 20.04](#pomodone-ubuntu-2004)

* Date: 2021-01-13
* *Error:*
  ```(pomodoneapp:38254): Pango-ERROR **: 08:34:06.746: Harfbuzz version too old (1.4.2)```

  Fixed on Ubuntu 20.04 & Pop!_OS 20.04 with:
  ```bash
  cd /tmp
  wget http://mirrors.kernel.org/ubuntu/pool/main/p/pango1.0/libpango-1.0-0_1.40.14-1_amd64.deb
  wget http://mirrors.kernel.org/ubuntu/pool/main/p/pango1.0/libpangocairo-1.0-0_1.40.14-1_amd64.deb
  wget http://mirrors.kernel.org/ubuntu/pool/main/p/pango1.0/libpangoft2-1.0-0_1.40.14-1_amd64.deb
  cd /opt/PomoDoneApp
  sudo dpkg -x /tmp/libpango-1.0-0_1.40.14-1_amd64.deb .
  sudo dpkg -x /tmp/libpangocairo-1.0-0_1.40.14-1_amd64.deb .
  sudo dpkg -x /tmp/libpangoft2-1.0-0_1.40.14-1_amd64.deb .
  LD_LIBRARY_PATH=/opt/PomoDoneApp/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH ./pomodoneapp
  ```
  *Notes:*
  If you use gnome or KDE or another standard desktop you may want to edit the application descriptor in `/usr/share/applications` to include the LD_LIBRARY_PATH as well. Also you can run via "pomodoneapp" command on gnome terminal.

* *Tags:* ubuntu, popos, 20.04, pango, pomodone, pomodoneapp, harfbuzz
