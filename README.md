# plane-notify
Nearing final first version. Notify If a Selected Plane has taken off or landed using Python with OpenSky API, outputs location of takeoff location of landing and takeoff by revese lookup of cordinates.

## How It works
- Takes data about every 15 seconds from OpenSky Network compares it to previous data with whats I've defined as a landing or takeoff event. 
- A takeoff event event is the plane is not on ground, below 10k feet and ((previously no data and now getting data) or was previously on ground). 
- A landing event is previosly below 10k feet and (previously getting data, no longer getting data and previously not on ground) or (now on ground and previously not on ground).
- Given the coordinates of the aircraft the coordinates are reverse looked up for a location name. (Geopy Nomination Geolocater)
- At time of takeoff a takeoff time is set which is refrenced in landing event to calculate an approximate total flight time.
- Static map image is created based off location name. (Google Static Maps API)
- If the landing event and takeoff events are true creates the output to Twitter and Pushbullet, uses the  location name, map image and takeoff time if landing. (Tweepy and Pushbullet )
a
## Required PIP packages
- OpenSky API https://github.com/openskynetwork/opensky-api
- geopy https://github.com/geopy/geopy
- colorama https://github.com/tartley/colorama

### Install OpenSky API
```bash
apt install git 
git clone https://github.com/openskynetwork/opensky-api.git
pip install -e ~/opensky-api/python
```
### Install Colorama and geopy
```bash
pip install colorama
pip install geopy
```
### Install Pushbullet and Tweepy optional output methods already implemented in code
```bash
pip install tweepy
pip install pushbullet.py
```
### Install Screen to run in background
```
apt install screen
```

### Make sure Python is installed
```
apt install python3
```
### Download / Clone 
```
git clone https://github.com/Jxck-S/plane-notify.git
cd plane-notify
```

### Configure defOpenSky, defTweet and defMap with API keys 
- defOpenSky doesn't require an OpenSky API key but bennefits from one.
- defTweet can be disabled if removed from NotifyBot.py or give Twitter API keys to it.
- Pushbullet is setup in main NotifyBot.py
- defMap needs Google Static Map API keys.
- edit them with nano or vi 


### Enter and create new Screen Session 
``` 
screen -R <name screen whatever you want>
```

### Start Program 
```
python3 NotifyBot.py
```
### TODO
implement YAML file for config options
implement airport name, done by closest airport
#### Refrences
- https://opensky-network.org/apidoc/
- https://geopy.readthedocs.io/en/stable/
- https://www.geeksforgeeks.org/python-get-google-map-image-specified-location-using-google-static-maps-api/
- https://realpython.com/twitter-bot-python-tweepy/
- https://github.com/rbrcsk/pushbullet.py


