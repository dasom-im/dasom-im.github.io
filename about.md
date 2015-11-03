---
layout: page
title: About
permalink: /about/
---

Dasom is a multilingual input method framework, which provides

  * Input Method Server
    * dasom-daemon including XIM

  * Client Modules
    * GTK+2, GTK+3, Qt4, Qt5

  * Indicators
    * GNOME shell: dasom agent extension
    * KDE, Unity, GNOME panel: dasom-indicator (using libappindicator3)

Dasom is licensed under the LGPL.

## Architecture
~~~~~

      +- im modules --+    +---- each process -----+  +- a process --+
      | gtk im module |    | gnome-shell-extension |  |   X server   |
      | qt  im module |    | dasom-indicator       |  +--------------+
      +---------------+    +-----------------------+         ^ |
              | calls                  | calls               | |
    +------------------+    +---------------------+          | |
    | dasom IM library |    | dasom agent library |          | | communicates
    +------------------+    +---------------------+          | |
             ^ |                      ^ |                    | |
             | |   communicates       | |                    | |
             | |   via Unix Socket    | |                    | |
             | v                      | v                    | v
          +---------------------- a process ----------------------+
          |                     dasom-daemon (including XIM)      |
          +-------------------------------------------------------+
                          | calls                  | create instance
                          | singleton instance     | (not module yet)
                +---------------+            +------------------+
                | engine module |   calls    | candidate module |
                |   interface   | ---------> |    interface     |
                +---------------+            +------------------+
                  |                            |
                  +- dasom-english             +- dasom-candidate (gtk3)


~~~~~
