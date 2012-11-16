# CakePHP2.x upgrade shell - improved version

The original one lacks a lot of things that could be done automatically.
Changes have been reported as ticket, but so far it has not yet made it into the official version.

This version supports now on top of the original commands/tasks:
- paginator (run only once!)
- database
- legacy
- name
- constructors
- webroot
- report
- estrict
and many more

New functionally also supported now:
- svn (linux/windows)
- group commands
- except command (all except for a few, e.g. `except paginator` to skip paginator method)

## UPDATE January 2012: Support for 2.1
Now supports
- Auth::allow(), Layout Stuff and more

## UPDATE September 2012: Support up to 2.3 (and some 3.0)
Now supports
- request->query() and Set/Hash replacement


As this is a plugin, use it with:
    cake Upgrade.Upgrade [command]


Additionally you can use the CorrectShell to correct
- request
- amp
- vis
- reference
- i18n
- forms
- conventions
- conventions2
- html5
- php53

with
    cake Upgrade.Correct [command]

Tip: Use
    cake Upgrade.Correct all
to quickly apply all relevant correction commands

Tip2: The probably most important feature for me is that my version cleanly separates
app and plugins. Without -p PluginName it leaves them alone.
If you want to upgrade plugins use
    cake Upgrade.Upgrade [command] -p PluginName

I also added support for -p * - to address all plugins at once.
This is only fully supported by the `group` command like so:
    cake Upgrade.Upgrade group [command1] [command2] ... -p *
You need to supply at least two commands (if you want to use only one, type it twice:
	  cake Upgrade.Upgrade group [command1] [command1] -p *
This is necessary because 1 argument stands for a config group

The not fully tested way of using the plugin wildcard would be
    cake Upgrade.Upgrade [command] -p *
which should just grab all files at once and process them


## Installation

a) Copy this plugin into your /app/Plugin folder

b) Put `CakePlugin::loadAll();` in your app bootstrap to make sure this plugin is loaded

c) Run any of the above commands. You should start with "Upgrade.Upgrade all" to fix the most important stuff.
