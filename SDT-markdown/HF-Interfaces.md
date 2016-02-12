

# Domain "ule.hanfun.interfaces"

## ModuleClasses


### 0x100 - Alert Server Interface  
The <em>Alert Server</em>  interface can be used by any device that requires sending an  alert. The alert type will be specified by the unit type where the interface is  implemented, for example for a smoke detector the alert will indicate the presence of  smoke, but for a motion detector the same alert will indicate that movement exists on  the area covered by it.   This interface can support multiple alerts, from 1 up to 32.


#### Actions
|Return Type |Name |Arguments |Optional |Documentation |
|:-----------|:----|:---------|:--------|:-------------|
|None|Status|Unit Type:&nbsp;integer <br /><br />State Attribute:&nbsp;Array: boolean <br />&nbsp;&nbsp;&nbsp;&nbsp; {Constraint: maxStates(integer)="32"; The maximum number of independent states is fixed at 32.}<br /><br /> |No|This command, sent to a client implementation of the Alert interface, indicates  the current state of all alerts.|

#### Data
|Name |Type |Optional |Writable |Readable |Eventable |Documentation |
|:----|:----|:--------|:--------|:--------|:---------|:-------------|
|State|Array: boolean <br />&nbsp;&nbsp;&nbsp;&nbsp; {Constraint: maxStates(integer)="32"; The maximum number of independent states is fixed at 32.}|Yes|Yes|Yes|Yes|<em>State</em>  indicates the state of an alert. A bit set to "true"  indicates an active alert, a bit set to "false" indicates idle.|
|Enable|Array: boolean <br />&nbsp;&nbsp;&nbsp;&nbsp; {Constraint: maxEnables(integer)="32"; The maximum number of independent enables is fixed at 32.}|Yes|Yes|Yes|Yes|<em>Enable</em>  indicates if an alert is enabled or disabled. A disabled alert  will never trigger. A bit set to "true" indicates alert is enabled, a bit set to  "false" indicates alert is disabled.|


### 0x100 - Alert Client Interface  
The <em>Alert Client</em>  interface can be used by any device that requires receiving an  alert.



### 0x200 - On/Off Server Interface  
The <em>On/Off Server</em>  interface enables a device to have some feature  (light, relay, LED, etc) locally turned on/off.


#### Data
|Name |Type |Optional |Writable |Readable |Eventable |Documentation |
|:----|:----|:--------|:--------|:--------|:---------|:-------------|
|State|boolean |Yes|Yes|Yes|Yes|<em>State</em>  indicates the current On (when true)/Off (when false) state.|


### 0x200 - On/Off Client Interface  
The <em>On/Off Client</em>  interface enables a device to remotely turn on/off have  some feature. It allows, for example, turning on or off a siren, an LED or a relay.


#### Actions
|Return Type |Name |Arguments |Optional |Documentation |
|:-----------|:----|:---------|:--------|:-------------|
|None|On|None |No|This command, sent to a server implementation of the On-Off interface,  turns some device feature on.|
|None|Off|None |No|This command, sent to a server implementation of the On-Off interface,  turns some device feature off.|
|None|Toggle|None |No|This command, sent to a server implementation of the On-Off interface, toggles  the state of some device feature. If the feature was set to On, it will be  turned Off and vice-versa.|


### 0x300 - Simple Power Metering Server Interface  
The <em>Simple Power Metering Server</em>  interface enables a device to realize  measurements of electric quantities that are made available for other devices to read.  All attributes are optional so is up to the device definition to define which ones are  implemneted.


#### Actions
|Return Type |Name |Arguments |Optional |Documentation |
|:-----------|:----|:---------|:--------|:-------------|
|None|Report|Number of Attributes:&nbsp;integer <br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFF"}<br /><br />Pair ID-Value:&nbsp;Struct<br />- integer *Attribute ID*<br />&nbsp;&nbsp;Identifier of an attribute whose value is sent.<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFF"}<br />- integer *Attribute Value*<br />&nbsp;&nbsp;Value currently store in the specified attribute.<br /><br /> |Yes|This optional command, sent to a client implementation of the Simple Power  Metering interface, will send the value of all implemented attributes with the  periodicity defined by <em>Report Interval</em>  attribute.|

#### Data
|Name |Type |Optional |Writable |Readable |Eventable |Documentation |
|:----|:----|:--------|:--------|:--------|:---------|:-------------|
|Energy|Struct {UnitOfMeasure: "Watts/Hour"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Energy Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Energy</em>  attribute stores energy consumption from device power up  or from a measurement reset|
|Energy at Last Reset|Struct {UnitOfMeasure: "Watts/Hour"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Energy Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Energy at Last Reset</em>  stores the <em>Energy</em>  value at the  instant a measurement reset occurred (see <em>Measurement Reset</em>   action). It is mandatory if the referred action is implemented.|
|Time at Last Reset|Struct {UnitOfMeasure: "Seconds"}<br />- boolean *Time Reference*<br />&nbsp;&nbsp;<em>Time Reference</em>  indicates the original source from  which time is measured/referenced.<br />- integer *Energy Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Time at Last Reset</em>  stores the time value (from device uptime  or UTC) at the instant a measurement reset occurred (see   <em>Measurement Reset</em>  action). It is mandatory if the referred  action is implemented.|
|Instantaneous Power|Struct {UnitOfMeasure: "Watts"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Power Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Instantaneous Power</em>  stores the presently instantaneous power  value.|
|Average Power|Struct {UnitOfMeasure: "Watts"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Power Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Average Power</em>  stores the power measured over a period of time  specified by <em>Average Power Interval</em>  .|
|Average Power Interval|integer  {UnitOfMeasure: "Seconds"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x0000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFF"}|Yes|Yes|Yes|Yes|<em>Average Power Interval</em>  specifies the time period over which  power should be averaged and stored into <em>Average Power</em>  .|
|Voltage|Struct {UnitOfMeasure: "Volts"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Voltage Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Voltage</em>  stores the presently instantaneous voltage value.|
|Current|Struct {UnitOfMeasure: "Amperes"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Current Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Current</em>  stores the presently instantaneous current value.|
|Frequency|Struct {UnitOfMeasure: "Hertz"}<br />- integer *Precision Code*<br />&nbsp;&nbsp;<em>Precision Code</em>  indicates a metric prefix that affects  the basic unit of measurement.<br />&nbsp;&nbsp; {Constraint: Possible Values; <em>Precision Code</em>  can only take a value from the  following: 0x00, 0x10, 0x11, 0x12, 0x13, 0x20, 0x21, 0x22  and 0x23.}<br />- integer *Frequency Value*<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00000000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFFFFFF"}|Yes|Yes|Yes|Yes|<em>Frequency</em>  stores the presently instantaneous frequency value.|
|Power Factor|integer <br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x00"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFF"}|Yes|Yes|Yes|Yes|<em>Power Factor</em>  stores the ratio between real and apparent power.|
|Report Interval|integer  {UnitOfMeasure: "Seconds"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x0000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFF"}|Yes|Yes|Yes|Yes|<em>Report Interval</em>  stores the periodic time interval, in seconds,  at which the <em>Report</em>  action should be sent. If set to 0 (zero)  the action will never be. It is mandatory if the referred action is  implemented.|


### 0x300 - Simple Power Metering Client Interface  
The <em>Simple Power Metering Client</em>  interface enables a device to receive  measurements of electric quantities.


#### Actions
|Return Type |Name |Arguments |Optional |Documentation |
|:-----------|:----|:---------|:--------|:-------------|
|None|Measurement Reset|None |Yes|This optional command sent to a server implementation of the Simple Power  Metering interface, performs the following operations:  * Copy Energy attribute present value into Energy at Last Reset attribute;  * Set Energy attribute to 0 (zero);  * Store device time into Time at Last Reset attribute.   Due to the nature of these operations, if this action is implemented then   <em>Energy at Last Reset</em>  and <em>Time at Last Reset</em>  must also be.|


### 0x301 - Simple Temperature Server Interface  
The <em>Simple Temperature Server</em>  interface enables a device to be able to  provide temperature readings.


#### Data
|Name |Type |Optional |Writable |Readable |Eventable |Documentation |
|:----|:----|:--------|:--------|:--------|:---------|:-------------|
|Measured Temperature|integer  {UnitOfMeasure: "One hundredth Celsius"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="-32768"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="+32767"}|Yes|Yes|Yes|Yes|<em>Measured Temperature</em>  holds the current measured temperature,  in one hundredth (1/100) of Celsius degrees.|
|Minimum Measureable Temperature|integer  {UnitOfMeasure: "One hundredth Celsius"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="-32768"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="+32767"}|Yes|Yes|Yes|Yes|<em>Minimum Measureable Temperature</em>  holds the minimum temperature,  in one hundredth (1/100) of Celsius degrees, that can be measured by the  device.|
|Maximum Measureable Temperature|integer  {UnitOfMeasure: "One hundredth Celsius"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="-32768"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="+32767"}|Yes|Yes|Yes|Yes|<em>Maximum Measureable Temperature</em>  holds the maximum temperature,  in one hundredth (1/100) of Celsius degrees, that can be measured by the  device.|
|Tolerance|integer  {UnitOfMeasure: "One hundredth Celsius"}<br />&nbsp;&nbsp; {Constraint: minValue(integer)="0x0000"}<br />&nbsp;&nbsp; {Constraint: maxValue(integer)="0xFFFF"}|Yes|Yes|Yes|Yes|<em>Tolerance</em>  holds the magnitude, in one hundredth (1/100) of  Celsius degrees of the error associated with <em>Measured Temperature</em>  ,  which means the actual value is between  ( <em>Measured Temperature</em>  - <em>Tolerance</em>  ) and  ( <em>Measured Temperature</em>  + <em>Tolerance</em>  ).|


### 0x301 - Simple Temperature Client Interface  
The <em>Simple Temperature Client</em>  interface enables a device to be able to  receive temperature readings.
