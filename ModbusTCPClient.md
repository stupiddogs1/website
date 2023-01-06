# ModbusTCPClient

### Introduction

ModbusTCPClient is a TCP Client for Modbus protocol. You can read/write coils and registers to devices or simulators that implemented Modbus TCP Server.

ModbusTCPClient also has Playmaker actions integrated.

### APIs

#### ReadCoilsAction

Read colis from server.

##### Paramaters

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
coilName | coil to read
numberOfPoints | number of data count to read, default to 8

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when reading data completed

##### Code Sample

```csharp
ReadCoilsAction action = new ReadCoilsAction(serverWithPort.Value, coilName.Value, numberOfPoints.Value);
action.ReuseConnection = ReuseConnection.Value;
action.OnCompleted = OnDataReceived;
action.Execute();
```

#### WriteCoilsAction

Write coil value to server.

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
coilName | Coil to read
coilValues | Value of coils to be wrotten

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when write data completed

##### Code Sample

```csharp
WriteCoilsAction action = new WriteCoilsAction(serverWithPort.Value, coilName.Value, coilValues.Value);
action.OnCompleted = Finish;
action.ReuseConnection = ReuseConnection.Value;
action.Execute();
```

#### ReadInputsAction

Read input from server.

##### Paramaters

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
inputName | input to read
numberOfPoints | number of data count to read, default to 8

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when reading data completed

##### Code Sample

```csharp
ReadInputsAction action = new ReadInputsAction(serverWithPort.Value, inputName.Value, numberOfPoints.Value);
action.ReuseConnection = ReuseConnection.Value;
action.OnCompleted = OnDataReceived;
action.Execute();
```

#### ReadHoldingRegistersAction

Read holiding registers from server.

##### Paramaters

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
startAddress | Start address of registers to read
numberOfPoints | number of data count to read, default to 8

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when reading data completed

##### Code Sample

```csharp
ReadHoldingRegistersAction action = new ReadHoldingRegistersAction(serverWithPort.Value, startAddress.Value, numberOfPoints.Value);
action.ReuseConnection = ReuseConnection.Value;
action.OnCompleted = OnDataReceived;
action.Execute();
```

#### WriteHoldingRegistersAction

Write holding registers value to server.

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
startAddress | Start address of registers to write
registerValues | Value of registers to be wrotten

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when write data completed

##### Code Sample

```csharp
WriteHoldingRegistersAction action = new WriteHoldingRegistersAction(serverWithPort.Value, startAddress.Value, registerValues.Value);
action.ReuseConnection = ReuseConnection.Value;
action.OnCompleted = Finish;
action.Execute();
```

#### ReadInputRegistersAction

Read input registers from server.

##### Paramaters

Name | Description
-- | --
serverWithPort | Modbus TCP Server address with port, for example 192.168.1.100:502
startAddress | Start address of register to read
numberOfPoints | number of data count to read, default to 8

##### Other Memebers

Name | Description
-- | --
ReuseConnection | Whether reuse tcp connection
OnCompleted | Event called when reading data completed

##### Code Sample

```csharp
ReadInputRegistersAction action = new ReadInputRegistersAction(serverWithPort.Value, startAddress.Value, numberOfPoints.Value);
action.ReuseConnection = ReuseConnection.Value;
action.OnCompleted = OnDataReceived;
```

### Playmaker Actions

Actions are under `ModbusTCPClient` category.

Name | Description
-- | --
ReadCoils | Read multiple coils
WriteCoils | Write multiple coils
ReadInputs | Read input status
ReadHoldingRegisters | Read holding registers
WriteHoldingRegisters | Write holding registers
ReadInputRegisters | Read input registers
DisposeReuseTcps | Dispose all tcp reuse connections