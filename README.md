#### Troubleshoot: 

* The mouse pointer stuck at the top of the screen Ubuntu 14.04.

'''

#Check the input list
$> xinput list 
# Disable the input item (e.g. touchpad)
# You may disable the keyboard watch out what you disabled
$> xinput disable <ID>
# Enable the input item
$> xinpit enable <ID>
# Restart the computer
$> sudo shutdown -r now

'''

* Moving the windows in Ubuntu 

'''
# Make sure that you have the compizconfig-settings-manager
# Search for Grid
# Generate a combination for Put+Top or Put+Bottom

e.g., 

<Ctrl><Shift><Alt>Up for Put+Top
<Ctrl><Shift><Alt>Up for Put+Bottom

This shortcuts will help you to move the window to the upper half
of the screen and lower half of the screen.
'''
