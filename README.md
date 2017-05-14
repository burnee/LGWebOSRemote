# LGWebOSRemote
Command line webOS remote for LGTVs

## Supported models

### Tested with

UF830V

Tested with python 2.7 on mac/linux and works fine, your mileage may vary with windows, patches welcome.

### Likely suports

All devices with firmware major version 4, product name "webOSTV 2.0"

## Available Commands
    scan
    auth                  Hostname/IP     Authenticate and exit, creates initial config ~/.lgtv.json
    audioStatus           
    audioVolume           
    closeApp              appid
    getTVChannel          
    input3DOff            
    input3DOn             
    inputChannelDown      
    inputChannelUp        
    inputMediaFastForward  
    inputMediaPause       
    inputMediaPlay        
    inputMediaRewind      
    inputMediaStop        
    listApps              
    listChannels          
    listInputs            
    listServices          
    mute                  muted
    notification          message
    off                   
    on                    
    openAppWithPayload    payload
    openBrowserAt         url
    openYoutubeId         videoid
    openYoutubeURL        url
    setInput              input_id
    setTVChannel          channel
    setVolume             level
    startApp              appid
    swInfo                
    volumeDown            
    volumeUp

## Install

Requires wakeonlan, websocket for python from here git+https://github.com/klattimer/WebSocket-for-Python.git#egg=ws4py

There's a requirements.txt included

    virtualenv venv
    source venv/bin/activate
    pip install -r requirements.txt

The TV doesn't respond when an Origin header (any origin header) is included, so I upstreamed
a patch to handle it but waiting on the pull request https://github.com/Lawouach/WebSocket-for-Python/pull/217.

## Example usage

    $ python lgtv.py on
    $ python lgtv.py off

    # If you have the youtube plugin
    $ python lgtv.py openYoutubeURL https://www.youtube.com/watch?v=dQw4w9WgXcQ

    # Otherwise, this works reasonably well
    $ python lgtv.py openBrowserAt https://www.youtube.com/tv#/watch?v=dQw4w9WgXcQ

## Caveats

You need to auth with the TV before being able to use the on command as it requires the mac address.

## Bugs

I couldn't test youtube because it seems the app isn't installed and not available to download right now
maybe they're updating it?