# Code-one
from tinydb import TinyDB, Query

# Initialize TinyDB and create a database file
db = TinyDB('home_automation_db.json')

# Define a table for devices
devices_table = db.table('devices')

# Define a table for sensors
sensors_table = db.table('sensors')

# Define a table for actions
actions_table = db.table('actions')

# Example: Inserting devices into the devices table
devices_table.insert({'name': 'Light Bulb', 'type': 'light', 'status': 'off'})
devices_table.insert({'name': 'Fan', 'type': 'fan', 'status': 'off'})

# Example: Inserting a temperature sensor into the sensors table
sensors_table.insert({'name': 'Temperature Sensor', 'type': 'temperature', 'value': 0.0})

# Example: Inserting actions into the actions table
actions_table.insert({'device': 'Light Bulb', 'action': 'turn_on', 'timestamp': '2023-11-13 12:00:00'})
actions_table.insert({'device': 'Fan', 'action': 'turn_off', 'timestamp': '2023-11-13 13:30:00'})

# Example: Querying the devices table
Device = Query()
fan_status = devices_table.get(Device.name == 'Fan')['status']
print(f"The status of the Fan is {fan_status}")

# Example: Querying the sensors table
TemperatureSensor = Query()
temperature_value = sensors_table.get(TemperatureSensor.name == 'Temperature Sensor')['value']
print(f"The current temperature is {temperature_value} degrees Celsius")

# Example: Querying the actions table
all_actions = actions_table.all()
print("All recorded actions:")
for action in all_actions:
    print(f"Device: {action['device']}, Action: {action['action']}, Timestamp: {action['timestamp']}")
