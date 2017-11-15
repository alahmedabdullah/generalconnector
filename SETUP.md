TINA Connector
================

Setup
-----
1. Install Chiminey (https://github.com/chiminey/docker-chiminey)
2. Go to docker-chiminey directory
```
	$ cd docker-chiminey
```
3. Enter into the Chiminey container
```
	$ ./chimineyterm
```
4. Go to chiminey directory
```
	$ cd /opt/chiminey/current/chiminey
```
5. Modify the SMART_CONNECTORES dictionary in settings_change.py file to have following:
```
         'general':  {'init': 'chiminey.generalconnector.initialise.GeneralInitial',
                      'name': 'general',
                      'description': 'The General Interface to Chiminey Connectors',
                      'sweep': True,
                      'hide_external_sweep': True
                    },
```
6. Modify the INPUT_FIELDS dictionary in settings_change.py file to have following:
```
	'general':  SCHEMA_PREFIX + "/input/general",
```
7. Clone the git repository https://github.com/alahmedabdullah/generalconnector.git in /opt/chiminey/current/chiminey
```
	$ git clone https://github.com/alahmedabdullah/generalconnector.git
```
8. Change ownership of the newly created uppalconnector directory
```
	$ chown -R chiminey.nginx generalconnector
```
9. Exit from the chiminey container
```
	$ exit
```
10. Restart the chiminey container
```
	$ docker-compose restart chiminey
```
11. Check that general connector is listed in available smart connectors list
```
	$ ./listscs
```
12. Activate the general connector and follow the prompts
```
	$ ./activatesc general
```
