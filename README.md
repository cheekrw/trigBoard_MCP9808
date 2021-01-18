# trigBoard_MCP9808

This is a hack of Kevin Darrah's teaching.  https://trigboard-docs.readthedocs.io/en/latest/temperatureSensor.html

This changes from sending data to Corlysis via the house wifi to sending data to an esp32 in the house with a TFT LCD display.

I expect to add internet connectivity back in later.  For now it's just a nice bright display of the outdoor temperature.  No online reporting or storage, though I intend to add that at some point.

Also this does not not automatically send data over wifi every time the trigboard wakes up.  It stores the temperature value in EEPROM, so when it wakes up and gets new data it compares the new data to what is in EEPROM.  If the values match (converted to int) then it just goes back to sleep.  If the values differ then it does the wifi stuff and updates the value in EEPROM.  This is done to increase battery lifetime.

This also differs from Kevin's project in that I use UDB instead of TCP.  I wasn't able to get the TCP part to work, but I didn't spend a lot of time on it.  This also is on the list of things to fix.  Actually, I should explore using ESP-NOW.
