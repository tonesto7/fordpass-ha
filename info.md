## **Changelog**
### Version 1.57
- Rewrote command function to actively poll until success or failure is returned
- Fixed bug where elveh attributes wasn't showing
- Fixed bug where command wouldn't check token expiry first
### Version 1.56
- Fix for error when missing GPS data from vehicle
- Fix for electric vehicle error
- Better formatting of door statuses
- Fix for missing diesel stats
- Fix for initial integration error on startup
- Added temperature sensors
- Added extra attributes to speed sensor e.g. pedal positions and RPM
- Removed GPS sensor (All stats are in device_tracker entity)
- Added check if window position if supported, if not entity is not added
### Version 1.55
- Skipped due to git issue
### Version 1.54
- Fixed lock/unlock status (Waits 90seconds before checking command has completed)
- Added back diesel sensors
- Added indicator/warning sensor (Shows any faults on the vehicle)
### Version 1.53
- Updated vehicle endpoint to use new Autonomics API
- Added secondary Autonomic token
- Remapped commands to use new "command" API endpoint
- Remapped existing sensors to new json variables (Some are missinge)
- Added charge status sensor (Thanks @SquidBytes)
- Added new speed sensor (Will be adding more attributes to this like pedal position and torque settings soon)

*Please report any bugs as a separate issue so I can keep track easier*

There is a LOT more coming soon as the new API exposes an excessive amount of information including speed, pedal position, crash sensors and way more. 
### Version 1.52
- Update for discontinued API endpoints (Update, lock, remote start)
### Version 1.51
- Fix for incorrect tire pressure conversion
- Handling of blank nickName when configuring car in config flow
- Fix for incorrect URL reference in vehicles API
### Version 1.50
- Complete refactor of all code to make it more compliant
- Added new config flow to allow for choosing vehicles on setup instead of using VIN 
### Version 1.49
- Added German & Italian translations (@@lollo0296)
### Version 1.48
- Add translations for service strings
- Fix error on odometer missing config
- Handle unsupported car locks
- Add Units for elVeh DTE
### Version 1.47
- Add poll_api service to allow for manual refreshing of data outside of poll interval (e.g. poll more when driving)
- Add option to disable distance conversion when units displaying wrong in certain countries
- Add device_class to "last_refresh" sensor
- Add Locking/Unlocking status to lock entity
- Enabled support for debugging via the UI
### Version 1.46
- Fix diesel filter error
### Version 1.45
- Fix window position reporting as open always
### Version 1.44
- Fix incorrect window position status
- Add reload integration service 
### Version 1.43
- Add DPF status on supported vehicles
- Incorrect vehicle refresh time (@ronytomen)
- Refresh integration automatticly on options changes
### Version 1.42
- Fix incorrect tire pressure units (Thanks @costr for debugging)
### Version 1.41
- Fix options error in HA 2023
### Version 1.40
- Fix empty value bug for lighting attributes
- Fix casting bug for elvehdte and batterly level
- Fix empty but not null string for tire pressure 
- Add BAR units to options
### Version 1.39
- added statistics support to odometer sensor
- Fixed device_tracker not working correctly in automations
### Version 1.38
- Changed the default update interval from 5 minutes to 15 minutes (Reduce Ford API Requests)
- Add ability to change this interval in integration options (WARNING! setting this too low will result in your Fordpass account being locked!!!!)
### Version 1.37
- Update messages icon to new format
### Version 1.36
- Remove vehicle list endpoint on setup
- Add dutch translation (Thanks @Bert-R)
### Version 1.35
- Remove deprecated dotted module
- Add coordinator context for HA 2022.7
### Version 1.34
- Change oauth flow for latest Fordpass changes
### Version 1.33
- Fix occasional hacs error due to git tag issue
### Version 1.32
- Fix auth flow to comply with new endpoints
**Warning - If you encounter auth errors please delete the token file located in the install directory or use the "delete_token" service**
### Version 1.31
- Fix for multiple accounts
### Version 1.30
- Fix for elvDTE error
### Version 1.29
- Disabled guard mode
- Fixed elvDTE units
- set Vin check on install to warning only (Lincoln cars don't show in ford database)
### Version 1.28
- Added vin check on setup (Will check if given VIN is linked to the credentials)
### Version 1.27
- Fix fuel level error
- Add code for Vin debugging
### Version 1.25
- Updated user agent
- Added messages sensor to show current messages in fordpass

### Version 1.24
- Change device_state_attributes to extra_state_attributes (HA 2020.12.1)
- Changed session timeout to cope with timeouts in fordpass API (Helps prevent 403 error's)

### Version 1.23
**Breaking Change**

When installing this new version please go to "integrations" and click configure on Fordpass and choose your preferred units. Not doing this will result in an error!!

- Fixed tyre pressure status when sensor missing or broke
- Add DistanceToEmpty Imperial Conversion (Thanks @JacobWasFramed )
- Seperated pressure and distance measurement unit selection (Thanks @JacobWasFramed)
### Version 1.22
- Fix for custom config locations on certain HA installs

### Version 1.21
- Error handling for null fuel and elVehDTE attributes. Thanks @wietseschmitt

### Version 1.20
- Fixed incorrect reporting of guardmode switch status

### Version 1.19
- Added null guard status handling (effects some vehicles)

### Version 1.18
- Fix Guard mode error (Missing data array)

### Version 1.17
- Added VIN option to UI
- Added Guard mode switch (Need people to test as don't have access to a guard mode enabled vehicle)
- Added extra sensors (Credit @tonesto7)
    - Zonelighting (Supported models only)
    - Deep sleep status
    - Remote start status
    - Firmware update status
- Added partial opening status for windows (Credit @tonesto7)
- Added logic to only add supported sensors (Still in Beta)


### Version 1.16
- Fixed json error when adding multiple cars
- Added "vin" option to "refresh" service to allow for refreshing of individual cars
- Fixed service bug calling the wrong variable
- Updated manifest for latest HA requirements

### Version 1.15
- Added Version attribute to manifest.json

### Version 1.14
- Converted "lastrefresh" to home assistant local time

### Version 1.13
- Fixed window status for Undefined
- Tire pressure now reports based on region
- Fixed 401 error for certain token refreshes
- Token file has been moved to same folder as install (Can be changed by changing the token_location variable)

### Version 1.12
- Fixed window status reporting as Open

### Version 1.11
- Added check for "Undefined_window_position" window value
- Fixed bug when TMPS value was 0 (Some cars return 0 on individual tyre pressures)

### Version 1.10
- Fixed door open bug 2.0 (New position value)
- Added a check to see if a vehicle supports GPS before adding the entity

### Version 1.09
- Added individual TMPS Support
- Fixed door open bug

### Version 1.08
- Added Icons for each entity
- Added "clear_tokens" service call
- Added Electric Vehicle features
- Fixed "Invalid" lock status

### Version 1.07
- Support for multiple regions (Fixes unavaliable bug)
- Token renamed to fordpass_token

**In order to support regions you will need to reinstall the integration to change region** (Existing installs will default to North America)

### Version 1.06 
- Minor bug fix
### Version 1.05
- Added device_tracker type (fordpass_tracker)
- Added imperial or metric selection
- Change fuel reading to %
- Renamed lock entity from "lock.lock" to "lock.fordpass_doorlock"


### Version 1.04
- Added window position status
- Added service "fresh_status" to allow for polling the car at a set interval or event
- Added Last Refreshed sensor, so you can see when the car was last polled for data
- Added some more debug logging

### Version 1.03
- Added door status
- Added token saving
- Added car poll refresh


Fordpass can be configured via Integrations UI

## Integration page

1. From Home Assistant UI go to Configuration > Integrations
2. Click the orange + icon at the bottom right to bring up new integration window
3. Find and click on fordpass
4. Enter required information and click Submit

