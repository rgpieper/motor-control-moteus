If deploying on RaspberryPi with Motues Pi3Hat:
apt install libraspberrypi-dev

Calibrate Motors: (must activate venv)
sudo python -m moteus.moteus_tool -t 1 --calibrate

Access Console:
sudo python -m moteus.moteus_tool -t 1 --console
<Ctrl-D> (to exit)

Change Drive ID (of additional motors):
Connect drive to JC1, if pi3hat busses are not mapped yet.
sudo python -m moteus.moteus_tool -t 1 --console
conf enumerate id
conf set id.id [ID#]
<Ctrl-D> (must exit and reconnect with updated ID)
sudo python -m moteus.moteus_tool -t [ID#] --console
conf write

Remove Position Limits on Motor
sudo python -m moteus.moteus_tool -t [ID#] --console
conf enumerate servopos
conf set servopos.position_min nan
conf set servopos.position_max nan
conf write
