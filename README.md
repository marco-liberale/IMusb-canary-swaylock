
# usb-canary

A Linux or macOS shell script to monitor USB devices while your computer is locked. Get notified or execute custom commands when someone plugs in or removes a USB device.

## Features
- Monitors USB device connections and disconnections.
- Works on macOS and Linux (supports ```swaylock``` for lock detection on Linux).
- Allows execution of custom commands when a USB event is detected.
- Supports "paranoid mode" to always alert, even if the system is not locked.

## Usage

### Basic Monitoring
Run the script to monitor USB devices:
```bash
./usb-canary -c "echo 'USB DEVICE DETECTED'"
```

### Paranoid Mode
Enable paranoid mode to always alert on USB events, regardless of whether the system is locked:
```bash
./usb-canary -p
```

### Execute a Custom Command
Run a custom command when a USB event is detected:
```bash
./usb-canary -c "<your_command>"
```

For example, send a notification using ```ntfy.sh```:
```bash
sh ./usb-canary -c 'curl -d "WARN: USB DEVICE CONNECTED/REMOVED" -H "Priority: 5" https://ntfy.sh/canaryusb' -p
```

### Combine Paranoid Mode and Custom Command
You can combine paranoid mode with a custom command:
```bash
./usb-canary -p -c "echo 'USB event detected at $(date)' >> usb-events.log"
```

### Examples
- **Log USB events to a file**:
  ```bash
  ./usb-canary -p -c "echo 'USB event detected at $(date)' >> usb-events.log"
  ```

- **Send a desktop notification**:
  ```bash
  ./usb-canary -c "notify-send 'USB Event' 'A USB device was plugged in or removed'"
  ```

## Authors

fijimunkii (original)
marco-liberale (fork)

## Changes
(See full changelist in commits)
- Added full support for Swaylock
- Removed Twilio messages and replaced them with custom commands


## License

This project is licensed under the GNU GPLv3 License - see the [LICENSE](LICENSE.txt) file for details.
