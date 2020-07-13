# Xmonad installation  

Xmonad is an awesome window tiling manager written in Haskell, which is simple to configure and use compared with dwm and i3wm , to get maximum customization out of the box.

To install xmonad use the following command :

```sudo xmonad libghc-xmonad-contrib-dev xterm dmenu```


- After installation , logout of the current session and login screen change the session to xmonad session.

- After you will login you will see a black screen , haha that's it, you got xmonad at it's very basic configuration.

Some of the key shortcuts that can come handy:  
Here ```mod``` - is generally **Alt key** for xmonad.

|KEYS SHORTCUT        | USE                           |
|:--------------------|:------------------------------|
|```mod+shift+enter```|Opens up a terminal            |
|```mod+p```          |opens dmenu -application opener|
|```mod+shift+c```    |closes current window in focus |
|```mod+q```          |restarts xmonad - use after reconfiguration|
|```mod+shift+q```    |quit xmonad|
|```mod+h```          |increase master window size|
|```mod+l```          |decrease master window size|
|```mod+shift+/```    |lists all key shortcuts|
|```mod+shift+k```    |swap the focused window with previous window|  

For more info on key shortcuts as such use following command in terminal :   
```man xmonad```  
![Xmonad keybindings](screenshots/Xmbindings.png?raw=true)
## Custom configuration of xmonad  

Head on to [Distrotube](https://www.youtube.com/watch?v=3noK4GTmyMw&t=1014s) for hands on implementation of following features.

1. A single file needs to be created :   
    - ```nano ~/.xmonad/.xmonad.hs```   
2. Check out the darcs template for [xmonad.hs](https://wiki.haskell.org/Xmonad/Config_archive/Template_xmonad.hs_(0.9))
3. Don't worry if you don't understand at first anything, copy the complete config and save it under ~/.xmonad/xmonad.hs.
4. To see if the custom config is working , type the following command in terminal.  
```xmonad --recompile```
5. If it gives no errors , you are good to go else you can see error message and search for the solution under xmonad wiki or haskell documentation.
6. Restart xmonad with ```mod+q``` here mod is ```Alt``` key.
7. Once done , you won't see much change, to make changes to window tiling manager , we can start changing xmonad.hs file.

## Setting wallpaper and transparency effect in Xmonad

This is one of the most basic customization that we can do to the tiling window manager.

In order to do so , we need two dependencies.
1. nitrogen
2. compton   
(Note: compton is also known as pycomp on Arch   distros , you will need to search accordingly.)

```sudo apt install nitrogen compton```

1. After successful installation, hit ```mod+p``` to start dmenu and enter ```nitrogen``` and hit enter.

2. Select a directory for wallpaper images from preferences and select apply, hit ```mod+shift+c``` to close window.

3. You will be able to see the change in wallpaper, in order to adjust screen resolution you can use ```xrandr```.

    ```xrandr -s 1360x768```  
    This command sets a resolution of 1360x768.
4. once done , use your favorite text editor (nano,vim,vscode,geany etc.) and edit the startupHook.

```startUpHook = do 
            spawnOnce "nitrogen --restore &"
            spawnOnce "compton &"
```

5. Add import Xmonad.Util.spawnOnce at the top of the file to avoid any errors.

6. Run ```xmonad --recompile``` to check for any errors , if not that's great, if found any errors search for xmonad haskell wiki, you most probably will find solution for it.

7. Restart xmonad with ```mod + q``` and check the screen , you will be able to see the wallpaper you set each time you login into a xmonad session, also you can set transparency on terminal and other compton effects.

![Desktop screenshot](screenshots/screenshot-desktop.png?raw=true)

## Adding rofi as an application launcher 
1. Install ```rofi```   
```sudo apt install rofi```
2. Visit [ArchLinux Wiki for Xmobar](https://wiki.archlinux.org/index.php/Xmobar#Installation) for more knowledge on configuring xmobar.
3. Add the following line for ```mod+p``` binding in xmonad.hs file.  
( Note: icon theme can be replaced with installed icon themes present on system.)

```((modm, xK_p),spawn "rofi -combi-modi window,drun,ssh -theme purple -font 'hack 10' -show combi -icon-theme 'Flat-Remix-Blue-Dark' -show-icons")```
