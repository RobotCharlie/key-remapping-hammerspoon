# key-remapping-hammerspoon


## Step 1
Download Hammerspoon from [official github site](https://github.com/Hammerspoon/hammerspoon/releases/tag/0.9.90)

Unzip it and turn on permissions including `Accessibility` (this is important otherwise your eventtab will be failed to load)

## Step 2
Create a Hammerspoon init file by doing this in your terminal

```bash
vi ~/.hammerspoon/init.lua
```
in which you can put your key remap configs.
Since I wanted to remap my arrow keys so I added the following
```local function pressFn(mods, key)
	if key == nil then
		key = mods
		mods = {}
	end

	return function() hs.eventtap.keyStroke(mods, key, 1000) end
end

local function remap(mods, key, pressFn)
	hs.hotkey.bind(mods, key, pressFn, nil, pressFn)	
end


remap({"ctrl"}, "j", pressFn("left"))
remap({"ctrl"}, "k", pressFn("down"))
remap({"ctrl"}, "i", pressFn("up"))
remap({"ctrl"}, "l", pressFn("right"))

remap({"ctrl", "shift"}, "j", pressFn({"shift"}, "left"))
remap({"ctrl", "shift"}, "k", pressFn({"shift"}, "down"))
remap({"ctrl", "shift"}, "i", pressFn({"shift"}, "up"))
remap({"ctrl", "shift"}, "l", pressFn({"shift"}, "right"))

remap({"ctrl", "cmd"}, "j", pressFn({"cmd"}, "left"))
remap({"ctrl", "cmd"}, "k", pressFn({"cmd"}, "down"))
remap({"ctrl", "cmd"}, "i", pressFn({"cmd"}, "up"))
remap({"ctrl", "cmd"}, "l", pressFn({"cmd"}, "right"))

remap({"ctrl", "alt"}, "j", pressFn({"alt"}, "left"))
remap({"ctrl", "alt"}, "k", pressFn({"alt"}, "down"))
remap({"ctrl", "alt"}, "i", pressFn({"alt"}, "up"))
remap({"ctrl", "alt"}, "l", pressFn({"alt"}, "right"))

remap({"ctrl", "shift", "cmd"}, "j", pressFn({"shift", "cmd"}, "left"))
remap({"ctrl", "shift", "cmd"}, "k", pressFn({"shift", "cmd"}, "down"))
remap({"ctrl", "shift", "cmd"}, "i", pressFn({"shift", "cmd"}, "up"))
remap({"ctrl", "shift", "cmd"}, "l", pressFn({"shift", "cmd"}, "right"))

remap({"ctrl", "shift", "alt"}, "j", pressFn({"shift", "alt"}, "left"))
remap({"ctrl", "shift", "alt"}, "k", pressFn({"shift", "alt"}, "down"))
remap({"ctrl", "shift", "alt"}, "i", pressFn({"shift", "alt"}, "up"))
remap({"ctrl", "shift", "alt"}, "l", pressFn({"shift", "alt"}, "right"))

remap({"ctrl", "cmd", "alt"}, "j", pressFn({"cmd", "alt"}, "left"))
remap({"ctrl", "cmd", "alt"}, "k", pressFn({"cmd", "alt"}, "down"))
remap({"ctrl", "cmd", "alt"}, "i", pressFn({"cmd", "alt"}, "up"))
remap({"ctrl", "cmd", "alt"}, "l", pressFn({"cmd", "alt"}, "right"))

remap({"ctrl", "cmd", "alt", "shift"}, "j", pressFn({"cmd", "alt", "shift"}, "left"))
remap({"ctrl", "cmd", "alt", "shift"}, "k", pressFn({"cmd", "alt", "shift"}, "down"))
remap({"ctrl", "cmd", "alt", "shift"}, "i", pressFn({"cmd", "alt", "shift"}, "up"))
remap({"ctrl", "cmd", "alt", "shift"}, "l", pressFn({"cmd", "alt", "shift"}, "right"))

```

This will map 
CTRL+i => up
CTRL+k => down
CTRL+j => left
CTRL+l => right
and also the more complex ones (I am sure you understand the rest of the code)

## Step 3
You can reload the config by clock the `Reload config` in the Hammerspoon Console, this will make whatever you just configed in the `init.lua`.

## Step 4
Verification. Hope it works!

