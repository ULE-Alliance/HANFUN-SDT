

# Domain "ule.hanfun.devices"
- **Includes**
	- Parse: xml, Href: ./HF-Interfaces.xml

## Devices


### AC_Outlet  
An <em>AC Outlet</em>  .


#### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: AC_Outlet.unit.0|
|Vendor|string| |Yes|Original value: ULE Alliance|

#### SubDevices

##### SubDevice "unit.1"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: AC_Outlet.unit.1|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|


### Smart_Plug  
A <em>Smart Plug</em>  that besides On/Off functionality is able to provide energy  consumption readings.


#### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Smart_Plug.unjit.0|
|Vendor|string| |Yes|Original value: ULE Alliance|

#### SubDevices

##### SubDevice "unit.1"  
The <em>AC Outlet with Simple Power Metering</em>  specifies a unit type that  receives a command to turn on/off some physical bi-stable AC actuator attached to  the device. It is also capable of doing and providing Energy consumption  measurements and accepts the <em>Measurement Reset</em>  command.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Smart_Plug.unit.1|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|


**Energy Consumption Measurements**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x300 - Simple Power Metering Server Interface|

**Data**

|Name |Type |Optional |Writable |Readable |Eventable |Documentation |
|:----|:----|:--------|:--------|:--------|:---------|:-------------|
|Energy|integer |Yes|Yes|Yes|Yes|<em>Energy</em>  stores energy consumption since device power up  or since a measurement reset. The stored value has the basic  unit of Watts/Hour that may be affected by a precision code.|
|Energy at Last Reset|integer |Yes|Yes|Yes|Yes|<em>Energy at Last Reset</em>  stores the <em>Energy</em>  value  at the instant a measurement reset occurs. The stored value has  the basic unit of Watts/Hour that may be affected by a precision  code.|
|Time at Last Reset|integer |Yes|Yes|Yes|Yes|<em>Time at Last Reset</em>  stores the time value (from device  uptime or UTC) at the instant a measurement reset occurs. The  stored value has the basic unit of Seconds.|


### Temperature_Sensor  
A <em>Temperature Sensor</em>  .


#### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Temperature_Sensor.unit.0|
|Vendor|string| |Yes|Original value: ULE Alliance|

#### SubDevices

##### SubDevice "unit.1"  
The <em>Simple Temperature Sensor</em>  specifies a unit type that is able to  provide temperature readings.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Temperature_Sensor.unit.1|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Simple Temperature Sensor**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x301 - Simple Temperature Server Interface|


### Window_Sensor  
A <em>Window Sensor</em>  .


#### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Window_Sensor.unit.0|
|Vendor|string| |Yes|Original value: ULE Alliance|

#### SubDevices

##### SubDevice "unit.1"  
The <em>Window Open/Close Detector</em>  specifies a unit type that sends an alert  when it detects that a window opened or closed. The alert message is sent as soon  as the window state changes.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Window_Sensor.unit.1|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Window Open/Close Detector**
  
<em>Window State</em>  bit is set to "true" if the window is open  or set to "false" if the window is closed.


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x100 - Alert Server Interface|


### Power_Plug_Bar  
A <em>Power Plug Bar</em>  with 5 (five) independent outlets.


#### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar|
|Vendor|string| |Yes|Original value: ULE Alliance|

#### SubDevices

##### SubDevice "unit.1"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar.unit.1|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|

##### SubDevice "unit.2"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar.unit.2|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|

##### SubDevice "unit.3"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar.unit.3|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|

##### SubDevice "unit.4"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar.unit.4|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|

##### SubDevice "unit.5"  
The <em>AC Outlet</em>  specifies a unit type that receives a command to turn  on/off some physical bi-stable AC actuator attached to the device.


###### Properties
|Name |Type |Value |Optional |Documentation |
|:----|:----|:-----|:--------|:-------------|
|Name|string| |Yes|Original value: Power_Plug_Bar.unit.5|
|Vendor|string| |Yes|Original value: ULE Alliance|


###### Modules


**Power Switch**


**Extends**

|Domain |Class |
|:------|:-----|
|ule.hanfun.interfaces|0x200 - On/Off Server Interface|