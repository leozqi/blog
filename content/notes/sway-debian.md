+++
title="Sway window manager"
date=2023-02-25
+++

Stuff on setting up Sway for Debian.

<!-- more -->

Configuration: <https://github.com/swaywm/sway/wiki#configuration>

## App launchers

Fuzzel is a great launcher.

```sh
bindsym Control+space     exec $launcher
bindsym Mod1+F1           exec $launcher
```

## Activate volume keys

Add this to your Sway configuration file:

```sh
bindsym XF86AudioMute exec pactl set-sink-mute @DEFAULT_SINK@ toggle
bindsym XF86AudioRaiseVolume exec pactl set-sink-volume @DEFAULT_SINK@ +5%
bindsym XF86AudioLowerVolume exec pactl set-sink-volume @DEFAULT_SINK@ -5%
```

[Source](https://old.reddit.com/r/swaywm/comments/qei3oh/how_can_i_set_up_keybindgs_with_sway_for_volume/)
