Role Name
=========

igami.zigbee2mqtt

Ansible role to install  zigbee2mqtt on Raspberry Pi running stock Raspbian lite or full. Should also work on other Debian distributions.

https://www.zigbee2mqtt.io/

Requirements
------------

Raspberry Pi with SSH enabled and CC2531 USB sniffer.  
If installing on a fresh 'headless' Raspberry Pi server, add an empty file named 'ssh' to the boot directory of the SD card to enable remote SSH access.

Role Variables
--------------

- `zigbee_user`: zigbee
- `zigbee_user_groups`: tty,dialout
- `zigbee_user_append`: false
- `zigbee_dir`: /opt/zigbee2mqtt
- `zigbee_repository`: https://github.com/Koenkk/zigbee2mqtt.git
- `zigbee_homeassistant`: false
- `zigbee_permit_join`: true
- `zigbee_mqtt_base_topic`: zigbee2mqtt
- `zigbee_mqtt_server`: mqtt://localhost
- `zigbee_serial_port`: /dev/ttyACM0
- `zigbee_mqtt_user`: 
- `zigbee_mqtt_password`: 
- `zigbee_network_key`: "'!network_key network_key'"  
  Zigbee2mqtt uses a known default encryption key. Therefore it is recommended to use a different one.  
  By default this role will create an random key at firstrun.
- `zigbee_generate_new_network_key`: no
- `zigbee_frontend`: no

Dependencies
------------

- npm >=5.8
- nodejs >=10

Example Playbook
----------------

To install zigbee2mqtt with default serial port:

```yaml

    - name: zigbee2mqtt octoprint on raspbian
      hosts: ip_address_of_rpi
      become: yes

      roles:
      - igami.zigbee2mqtt
```

To install zigbee2mqtt with custom serial port:

```yaml

    - name: zigbee2mqtt octoprint on raspbian
      hosts: ip_address_of_rpi
      become: yes

      roles:
      - role: igami.zigbee2mqtt
        vars: 
          zigbee_serial_port: /dev/serial/by-id/usb-Texas_Instruments_TI_CC2531_USB_CDC___0X00124B0018ED3DDF-if00
```

To install zigbee2mqtt with default serial port and MQTT authentication:

```yaml

    - name: zigbee2mqtt octoprint on raspbian
      hosts: ip_address_of_rpi
      become: yes

      roles:
      - role: igami.zigbee2mqtt
        vars: 
          zigbee_mqtt_user: mqtt_user
          zigbee_mqtt_password: mqtt_password
```

License
-------

BSD

Author Information
------------------

igami@noreply.user.github.com
