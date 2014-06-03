ACSpy
=====

A Python package for working with ACS motion controllers.

Installation
------------
  - `git clone https://github.com/petebachant/ACSpy.git`
  - `python setup.py install`

Usage
-----
### Using the `acsc` module
The `acsc` module is designed to mimic the syntax of the ACS C library that it wraps. 

```python
>>> from acspy import acsc
>>> hcomm = acsc.openCommDirect()
>>> acsc.enable(hcomm, 0)
>>> acsc.getMotorState(hcomm, 0)
{'moving': False, 'enabled': True, 'in position': True, 'accelerating': False}
>>> acsc.closeComm(hcomm)
```

### Using the `Controller` and `Axis` objects
The `control` module contains an object to handle communication with the controller, and
and object to represent an axis.
An example of its use:

```python
>>> from acspy.control import Controller, Axis
>>> controller = Controller("simulator")
>>> controller.connect()
>>> axis = Axis(controller, 0)
>>> axis.enable()
>>> axis.enabled
True
>>> controller.disconnect()
```

License
-------

ACSpy Copyright (c) 2013-2014 Peter Bachant

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
