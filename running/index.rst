How to start MPF and run your game
==================================

.. note:: This page is a reference for how to start MPF and all the
   various command-line options. If you're brand-new to MPF and running
   it for the first time, we recommend that you follow our :doc:`step-by-step
   getting started tutorial </tutorial/index>`. The first few steps will walk you through
   downloading and installing MPF and getting our sample *Demo Man*
   machine up and running.)

MPF is a console-based application which you
run from the command line. There are actually two separate processes
that you need to run for MPF: The *MPF game engine* and the
separate *media controller*. The game engine talks to the pinball
hardware and runs the game logic, and the media controller drives the
display and audio. The game engine and media controller talk to each
other via an open protocol called *BCP* (for "Backbox Control
Protocol") via a TCP socket.

At this point you might be wondering why
the game engine and media controller are two separate processes? Two
reasons:

+ Having two processes means that each one can run on a separate core
  in a multi-core host computer. This makes efficient use of hardware
  since the trend is to have multiple cores. If the game engine and
  media controller were combined, then your quad-core Raspberry Pi 3
  would have all the MPF stuff running on one core while the other three
  cores were wasted doing nothing.
+ Having two processes means you can replace the built-in Python-based
  media controller with something else if you want different features.
  For example, there is a group of people building an open source Unity
  3D-based media controller which can be used for very advanced 3D
  display graphics.

To run an MPF game, you have to start both the media controller and
the MPF game engine. You can do both of these via the command line.
However, by default, each component "takes over" the terminal window
while it's running, so you actually need to open two terminal windows
and run the MPF core engine in one and the media controller in the
other.

Starting the MPF media controller
---------------------------------

To run MPF, first start the media controller.

Since this is done from the command line, you'll need to open a command line
window. On Windows, you can right-click on the Start Button (or whatever it's
called these days) and click the "Command Prompt". On Mac OS X you can run the
Terminal app. On Linux, well, if you're using Linux, you know what a command
line is. :)

From the command line, change to the directory which is the root of your machine
folder. This is the folder that contains your machine's ``config``, ``modes``,
``shows``, etc. folders.

.. note:: Prior to MPF 0.30, we recommended that you put your machine's folder
   in the ``/machine_files`` folder inside the MPF package. That is changed now,
   and you can put your machine folder(s) wherever you want.


Then run:

::

    mpf mc <enter>


You should see a popup window and a bunch of stuff scroll by in the console.

Starting the MPF game engine
----------------------------

Since the MPF game engine is a separate process from the media controller, you need
to start it separately.

Open a second console window, change to your machine folder, and run:

::

    mpf <enter>


Understanding what's happening
------------------------------

Starting in MPF 0.30, when you install MPF, the command ``mpf`` is registered with your system. You can
open a command prompt and run "mpf", by itself, from anywhere.

There are several sub-commands you can specify when you run MPF. You specify a
sub-command by running `mpf <command>`. (Some mpf commands take additional
options).

Here's a list of valid MPF commands. Click on any one of them for full details and command-line options.

* `mpf <mpf>`_ (Starts the MPF game engine and other commands)
* `mpf game <commands/game>`_ (Starts the MPF game engine)
* `mpf mc <commands/mc>`_ (Starts the MPF Media Controller)
* `mpf both <commands/both>`_ (Starts both the MPF game engine and media controller at the same time)
* `mpf migrate <commands/migrate>`_ (Migrates older config and show files to the current version)

.. toctree::
   :hidden:

   MPF command launcher <mpf>
   MPF commands <commands/index>



