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
