---
title: "Logitech mouse"
---

I have a logitech M720 mouse and a logitech K850 keyboard. There are no offical drivers for linux, so I am using [PixlOne/logiops](https://github.com/PixlOne/logiops). This is my config for the mouse:

``` cfg title="/etc/logic.cfg"
devices: (
{
    name: "M720 Triathlon Multi-Device Mouse";
    smartshift:
    {
        on: true;
        threshold: 20;
    };
    hiresscroll:
    {
        hires: true;
        invert: false;
        target: false;
    };
    dpi: 1000;
    buttons: (
	{
            cid: 0xd0;
            action =
            {
                type: "Gestures";
                gestures: (
                    {
                        direction: "Up";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_LEFTALT", "KEY_TAB"];
                        };
                    },
                    {
                        direction: "Down";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_LEFTMETA", "KEY_D"];
                        };
                    },
                    {
                        direction: "Left";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_LEFTCTRL", "KEY_LEFTALT", "KEY_LEFT"];
                        };
                    },
                    {
                        direction: "Right";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_LEFTCTRL", "KEY_LEFTALT", "KEY_RIGHT"];
                        };

                    },
                    {
                        direction: "None";
                        mode: "OnRelease";
			action = 
                        {
                            type: "Keypress";
                            keys: ["KEY_LEFTMETA"];
                        };
                    }
                );
            };
        }
    );
}
);

```
