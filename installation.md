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

Then, add these lines to ```~/.xprofile```
{% highlight bash %}
export GTK_IM_MODULE=dasom
export QT_IM_MODULE=dasom
export XMODIFIERS="@im=dasom"
dasom-daemon
dasom-indicator
{% endhighlight %}

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

## Are you using GNOME Desktop?
You may need to run these commands to use dasom.
{% highlight bash %}
gsettings set org.gnome.settings-daemon.plugins.keyboard active false
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/IMModule':<'dasom'>}"
{% endhighlight %}

If needed, you can use Dasom Agent extension for GNOME.
{% highlight bash %}
# Enable Dasom Agent extension for GNOME
gnome-shell-extension-tool -e dasom-agent@gnome-shell-extensions.cogno.org
{% endhighlight %}

## Debugging Dasom
{% highlight bash %}
dasom-daemon --debug
ail -f /var/log/daemon.log

export GTK_IM_MODULE="dasom"
export QT4_IM_MODULE="dasom"
export QT_IM_MODULE="dasom"
export G_MESSAGES_DEBUG=dasom
export XMODIFIERS="@im=dasom"
gedit # or kate for Qt
{% endhighlight %}
