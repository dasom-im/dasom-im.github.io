---
layout: page
title: Installation
permalink: /installation/
---

## Arch Linux
Build and Install ```dasom-git``` package from AUR
{% highlight bash %}
yaourt -S dasom-git
{% endhighlight %}

Build and Install ```dasom-gtk-git``` and ```dasom-qt-git``` (IM Modules for dasom) from AUR
{% highlight bash %}
yaourt -S dasom-gtk-git dasom-qt-git
{% endhighlight %}

for Korean Input, Build and Install ```dasom-jeongeum-git``` package from AUR Additionally.
{% highlight bash %}
yaourt -S dasom-jeongeum-git
{% endhighlight %}

Then, add these lines to ```~/.xprofile```
{% highlight bash %}
export GTK_IM_MODULE=dasom
export QT_IM_MODULE=dasom
export XMODIFIERS="@im=dasom"
dasom-daemon
dasom-indicator
{% endhighlight %}

## Ubuntu & Debian
Get Latest Dasom Package from [Here](https://github.com/dasom-im/dasom/releases).<br>
Get Latest GTK IM Modules Package from [Here](https://github.com/dasom-im/dasom-gtk/releases) and Latest QT IM Modules package from [Here](https://github.com/dasom-im/dasom-qt/releases).<br>
For Korean Input, Get Latest Dasom Jeongeum Package from [Here](https://github.com/dasom-im/dasom-jeongeum/releases). <br>
Then, use dpkg for installation.
{% highlight bash %}
sudo dpkg -i <Path To Package> # Example : sudo dpkg -i dasom_1.1-ubuntu-15.10_amd64.deb
{% endhighlight %}

Run ```im-config``` to set ```dasom``` as a default Input Method
{% highlight bash %}
im-config
{% endhighlight %}
then, select ```dasom``` from the list

## Build and Install from source
{% highlight bash %}
git clone https://github.com/dasom-im/dasom.git
cd dasom
./autogen.sh
make
sudo make install
sudo ldconfig
sudo make update-gtk-im-cache
sudo make update-gtk-icon-cache
{% endhighlight %}

## Are you using GNOME Desktop on Arch Linux?
You may need to run the following commands to use dasom.
{% highlight bash %}
gsettings set org.gnome.settings-daemon.plugins.keyboard active false
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/IMModule':<'dasom'>}"
{% endhighlight %}

If needed, you can use dasom-agent extension for GNOME shell.
{% highlight bash %}
# Enable dasom-agent extension for GNOME shell
gnome-shell-extension-tool -e dasom-agent@gnome-shell-extensions.cogno.org
{% endhighlight %}

## Debugging
{% highlight bash %}
dasom-daemon --debug
tail -f /var/log/daemon.log

export GTK_IM_MODULE="dasom"
export QT4_IM_MODULE="dasom"
export QT_IM_MODULE="dasom"
export G_MESSAGES_DEBUG=dasom
export XMODIFIERS="@im=dasom"
gedit # or kate for Qt
{% endhighlight %}
