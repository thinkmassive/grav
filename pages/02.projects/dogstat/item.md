---
title: DogStat
taxonomy:
  category: project
  tag: [ project, hardware, raspberrypi, pets ]
---

A simple system to track dog activities, including walks, meals, and medicine.

===

[Github repo](https://github.com/thinkmassive/dogstat)

# Product Requirements

## Objective
Track when the dog is fed and walked, so multiple masters can synchronize their activities. Events to track include: walk, meal, medicine. Output should include the number of each activity so far today, and the last time for each activity.

A primary hardware interface should allow activity input and reporting. This can be AC-powered, and batteries should only be considered as the primary power source if the device can operate for at least a week per charge. Activity should reside in a persistent data store that maintains state across power cycles. A networked device would be ideal, so a web interface can eventually be exposed.

## Core Components

### Software
- Application: [hoover.py](https://github.com/thinkmassive/dogstat/blob/master/hoover.py)
- Data store: [pickledb](https://patx.github.io/pickledb/)
- System service: [dogstat.service](https://github.com/thinkmassive/dogstat/blob/master/dogstat.service)

### Hardware
- Computer: Raspberry Pi 2 B
- Power supply: 5V USB
- Display: SenseHAT LED matrix
- Input: SenseHAT joystick button
  - up: increment walks
  - down: view activity report
  - left: increment meals
  - right: increment meds
  - button: unused

## User Flow

## Analytics

## Future Features

## Links
- [SenseHAT API Reference](https://pythonhosted.org/sense-hat/api)
- [python: how to process SIGTERM](https://stackoverflow.com/questions/18499497/how-to-process-sigterm-signal-gracefully)
- [Python MotW: threading](https://pymotw.com/2/threading/)
- [MicroPython Forum: multithreading](https://forum.micropython.org/viewtopic.php?t=1864)
- [Python cheatsheet for couchdb module](https://gist.github.com/marians/8e41fc817f04de7c4a70)
- [CouchDB Docs](http://docs.couchdb.org/en/stable/)
