# rfidsntacher
Arduino RFID Cloner and Texter 


## Project Description

This Arduino based RFID snatcher was built for an experiment/PoC for DefCon 26 (August 9 - 12 2018).

The project consists of several core components:

1. An Arduino microcontroller

2. Support for GSM (send SMS)

3. A battery 

4. Attenna 

5. An RFID shield.


The RFID shield allows you to scn passive devices such as key cards. It will then attempt to crack the card, and will text the cracked key to a cell phone.


## Source Code

The source code is relatively simple and uses some of the default code/concepts provided by many of the Arduino libraries and keys documentation that are available, including:

1. MFRC522 library example: https://github.com/miguelbalboa/rfid

2. Check default keys: https://code.google.com/p/mfcuk/wiki/MifareClassicDefaultKeys


Currently the phone number you wish to SMS to needs to be hard coded into the `rfid_gsm_default_keys.ino` file on line `157`

Example:

```
 char remoteNum[] = "0000000";  // telephone number to send sms
```


Line 203 contains the check for the MIFAR known keys. 

If you wish to just attempt to crack a single known key, this can be hard coced, or the array reduce to a single value:


```

  for (byte i = 0; i < MFRC522::MF_KEY_SIZE; i++) {
      key.keyByte[i] = knownKeys[k][i];
  }

```

or

```

 key.keyByte[i] = 0xFF;

```



