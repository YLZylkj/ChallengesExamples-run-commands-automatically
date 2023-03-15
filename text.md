When the background script is running, sometimes it's required that the user is blocked until the script finishes.

In this case, using files as notifications can be useful.

For example, the following is a background script that is running:

#!/bin/bash

echo "This is a background script with a long running process"

sleep 10

echo "done" >> /opt/.backgroundfinished

The foreground script waits for the file to be created. After the file exists, the while loop finishes and the user is allowed to access the terminal.

echo "Waiting to complete"; while [ ! -f /opt/.backgroundfinished ] ; do sleep 2; done; echo "Done"
This can be improved by displaying a Progress Spinner to the user as described in an additional scenario.