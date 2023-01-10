# RobotToAPP

## Introduction

RobotToAPP allows your application connect to Robot Studio. 

RobotToAPP Supports read robot joints and read/write signal value.
RobotToAPP Supports Playmaker actions.
RobotToAPP Supports Robot Studio 6.0.8.
RobotToAPP build on .NET 4.0, so you need set to project base on .NET 4.x.

Any questions, please contact 1372610017@qq.com

## Newtonsoft.Json issue

Unity Editor have include Newtonsoft.Json as dependency of Version control package. There will be an error in some Unity Editor version about Newtonsoft.Json conflict. We can either remove the Newtonsoft.Json.dll in RobotToAPP package or remove the Newtonsoft.Json of Unity from Package Manager to fix the issue.

## APIs

### ABBCommunicator

Singleton class to comunicate with Web Services from Robot Studios.

#### Static Property

Name | Description
-- | --
Instance | Instance of ABBCommunicator

#### Property

Name | Description
-- | --
NetWorkCredential | Credential of web services
HOST | Host address of web services, have to end with '/'

#### Methods

Name | Description
-- | --
Post | Send post request to web services
Get | Send get request to web services


### ReadJointAction

Get joint data.

#### Methods

Name | Description
-- | --
Execute | Execute the request

#### Events

Name | Description
-- | --
OnCompleted | Return data of joint

#### Code Samples

```csharp
ReadJointAction action = new ReadJointAction();
action.OnCompleted = data =>
{
    Debug.Log(string.Format("{0},{1},{2},{3},{4},{5}",
     data.Joint1, 
     data.Joint2, 
     data.Joint3, 
     data.Joint4, 
     data.Joint5, 
     data.Joint6
    ));
};
```

### ReadExternalJointAction

Get external joint data.

#### Methods

Name | Description
-- | --
Execute | Execute the request

#### Events

Name | Description
-- | --
OnCompleted | Return data of joint

#### Code Samples

```csharp
ReadExternalJointAction action = new ReadExternalJointAction();
action.OnCompleted = data =>
{
    Debug.Log(string.Format("{0},{1},{2},{3},{4},{5}",
     data.EJoint1, 
     data.EJoint2, 
     data.EJoint3, 
     data.EJoint4, 
     data.EJoint5, 
     data.EJoint6
    ));
};
```

### ReadSignalAction

Read signal

#### Methods

Name | Description
-- | --
Execute | Execute the request

#### Events

Name | Description
-- | --
OnCompleted | Return data of signal

#### Code Sampels

```csharp
ReadSignalAction rsAction = new ReadSignalAction("SIGNAL_TO_READ");
rsAction.OnCompleted = signal =>
{
    Debug.Log(string.Format("{0},{1},{2}", 
        signal.category, 
        signal.type, 
        signal.lstate, 
        signal.lvaule
    ));
};
rsAction.Execute();
```

### SetSignalValueAction

Set signal value

#### Methods

Name | Description
-- | --
Execute | Execute the request

#### Events

Name | Description
-- | --
OnCompleted | Callback after setting completed

#### Code Sampels

```csharp
SetSignalValueAction ssAction = new SetSignalValueAction("SIGNAL_TO_SET", "VALUE_OF_SIGNAL");
ssAction.OnCompleted = () => Debug.Log("Done!");
ssAction.Execute();
```


## Playmaker Actions

Name | Description
-- | --
ABBSetHost | Set the host address of web services
ABBReadJoint | Read data of 6 Joints
ABBReadExternalJoint | Read data of external Joints
ABBReadSignal | Read data of signal
ABBSetSignalValue | Set value of signal