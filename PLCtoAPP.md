# PLCtoAPP

### Introduction

PLCtoAPP allows communication between your apps with Mitsubishi PLC devices or Virtual PLC Simulators base on GXWorks. Useful for Digital Twins.

PLCtoAPP also provides Playmaker Actions.

Any questions, please contact 1372610017@qq.com

### Supports 

- Mitsubishi PLC devices: FX1N、FX2N、FX3U、FX5U etc.
- GXWorks2 and GXWorks3 Simulators.

### Code Samples

Below is a simple sample of reading/writing data from/to devices or simulators 

```csharp
var logicalStationNumber = 0;
var password = "your_passwords";
// Open connections
ActUtlType.Instance.Open(logicalStationNumber, password);

// Read data samples, you can change real address of your side.
var deviceNames = new string[] { "X0", "X1" };
var data = ActUtlType.Instance.ReadDeviceData(deviceNames);
Debug.Log(string.Format("Read data: {0}, {1}", data[0], data[1]));

// Write Data samples
int[] dataToWrite = new int[] { 32, 31 };
ActUtlType.Instance.WriteDeviceData(deviceNames, dataToWrite);

// Close connections
ActUtlType.Instance.Close();
```

### APIs

`ActUtlType` is a singleton wrapper class for communication between apps with devices or simulators

| Method Name| Description |
-- | -- |
Open | Open connection
ReadDeviceData | Read data from devices, return int or array of int
WriteDeviceData | Write data to devices
Close | Close connection
Dispose | Dispose all resources
