---
-api-id: P:Windows.ApplicationModel.Activation.ContactCallActivatedEventArgs.ServiceUserId
-api-type: winrt property
---

<!-- Property syntax
public string ServiceUserId { get; }
-->

# Windows.ApplicationModel.Activation.ContactCallActivatedEventArgs.ServiceUserId

## -description
Gets the user identifier of the service used for the call.

## -property-value
The user identifier of the service used for the call.

## -remarks
For PSTN calls, the [ServiceUserId](contactcallactivatedeventargs_serviceuserid.md) property is set to the PSTN number for the contact. For web-based services, the [ServiceUserId](contactcallactivatedeventargs_serviceuserid.md) property is set to the contact’s user id for that particular service.

For info about how to handle app activation through contact actions, see [Quickstart: Handling contact actions ](https://msdn.microsoft.com/library/397d8b2a-6255-4f37-8556-449a3be2ef3f) and [Quickstart: Handling contact actions ](https://msdn.microsoft.com/library/61bacc8a-24c9-4b3d-b77b-e0822467700c).

## -examples

## -see-also
[Handling Contact Actions sample](https://go.microsoft.com/fwlink/p/?LinkID=320151)
