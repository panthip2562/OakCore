## You must update your Arduino Oak package to 0.9.5 via the boards manager! 

**Due to bugs in the Arduino 1.6.6 and 1.6.7 IDEs we strongly suggest using 1.6.5r2 (for all boards not just ours)**

**If you previously used an earlier Beta please do a factory reset here: http://github.com/digistump/OakRestore**

**MAKE SURE YOU USE THE LATEST OakSoftAP - force a browser refresh before using**

**HOW TO INSTALL AND USE THIS:** http://digistump.com/wiki/oak/tutorials/arduino
**TROUBLESHOOTING:** http://digistump.com/wiki/oak/tutorials/troubleshooting

**PLEASE FILE ISSUES FOR BUGS:** with as much detail as possible!

**Issues Fixed with this release:**

- Fast OTA Updates! (these are the updates from Particle, not the initial update during config) 10x the speed!
- Pin 1 selectable for safe mode entry (hold low on boot to enter config/safe mode) (Pin 6 didn't work as it is pulled down in module)
- Various small fixes (see github issue tracker for most)
- Better logic when in config mode - always connects to Particle when possible
- Config App has improved device claiming, device will always be added to your account when it first connects after a successful update, even if you close out the config app.
- OakCLI uploader now show status messages during and after the flash process.


**Known Issues with this release:**

- Sometimes FastOTA flashing fails, if this happens just power off and back on and try again. You can hold pin 1 low to force entry into config mode as well.
- Still having issues with the initial updating - power users can now do this over serial (see http://github.com/digistump/OakRestore) - still working hard to improve this.
- Initial connection before the user application starts is still a bit slow, but not horrible.
- Not tested exhaustively! May brick your unit, please don't try to break it, yet... unless you really want to.
- If you brick your unit you'll need a 3.3v serial adapter to revive it. (See https://github.com/digistump/OakRestore)
- Serial over the cloud is not fully working yet - a serial adapter on pins 3(RX) and 4(TX) can be a big help until that gets sorted in the next release or if you are debugging anything major, for now.

**Working Particle APIs:**

- Particle.variable()
- Particle.function()
- Particle.publish()
- Particle.subscribe()
- Particle.unsubscribe()
- Particle.connect()
- Particle.disconnect()
- Particle.connected()
- Particle.process()
- Particle.syncTime() - though time is not yet connected to anything

Particle docs here: https://docs.particle.io/reference/firmware/photon/

The rest of the Particle APIs are not connected right now. But all of the ESP8266 APIs are.

Be advised that some ESP8266 libraries that are included may break it, and none of the libraries have been fully tested against this release yet.

ESP8266 docs here: http://esp8266.github.io/Arduino/versions/2.0.0/doc/libraries.html

**Other useful info:**

- Oak.rebootToConfig() will get you into WiFi Config setup mode.
  - If you can't boot into that then pull Pin 1 to GND and it power cycle and you will boot to that.
  - Next release will have an option to boot there automatically if there the WiFi can't connect.
  - It will also boot to a safe mode if there is a timeout (do to a while loop that doesn't call Particle.process()) or a exception (memory overflow, etc) - in that mode it will just wait for an update. If you power cycle it will go back to the user program.
- DO NOT mess with the flash read/write/erase functions - erase the wrong sector and it will brick the unit.
- Future system updates will come automatically when you upload a new sketch.
- Have fun! Much more to come! 
