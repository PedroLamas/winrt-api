---
-api-id: T:Windows.UI.Xaml.Automation.Peers.TextBlockAutomationPeer
-api-type: winrt class
---

<!-- Class syntax.
public class TextBlockAutomationPeer : Windows.UI.Xaml.Automation.Peers.FrameworkElementAutomationPeer, Windows.UI.Xaml.Automation.Peers.ITextBlockAutomationPeer
-->

# Windows.UI.Xaml.Automation.Peers.TextBlockAutomationPeer

## -description
Exposes [TextBlock](../windows.ui.xaml.controls/textblock.md) types to Microsoft UI Automation.

## -remarks
The Windows Runtime  [TextBlock](../windows.ui.xaml.controls/textblock.md) class creates a new [TextBlockAutomationPeer](textblockautomationpeer.md) as its [OnCreateAutomationPeer](../windows.ui.xaml/uielement_oncreateautomationpeer_1478162674.md) definition. [TextBlock](../windows.ui.xaml.controls/textblock.md) is sealed, so the normal scenario of deriving from the [TextBlock](../windows.ui.xaml.controls/textblock.md) class and its existing peer isn't applicable to [TextBlockAutomationPeer](textblockautomationpeer.md).

### Default peer implementation and overrides in **TextBlockAutomationPeer**

[TextBlockAutomationPeer](textblockautomationpeer.md) has overrides of **Core** methods such that the associated [AutomationPeer](automationpeer.md) methods provide peer-specific information to a Microsoft UI Automation client.

+ [GetPattern](automationpeer_getpattern_2046576749.md) reports pattern support for [TextPattern](https://msdn.microsoft.com/library/ddcf7ecd-7ed2-4b57-82a7-c7e1608dbfa1), but see "TextPattern support" in this topic for more info.
+ [GetClassName](automationpeer_getclassname_614238974.md) returns "TextBlock".
+ [GetAutomationControlType](automationpeer_getautomationcontroltype_1156384152.md) returns [AutomationControlType.Text](automationcontroltype.md).
+ [GetName](automationpeer_getname_1386609741.md) returns a plain-text representation of the [TextBlock](../windows.ui.xaml.controls/textblock.md) text content from [TextBlock.Text](../windows.ui.xaml.controls/textblock_text.md).
+ [IsControlElement](automationpeer_iscontrolelement_1004644794.md) returns a value based on the template parent. If there is a template parent then it returns **true**, otherwise the value is **false**. The scenario here is that a templated control may have forwarded to this peer for text support, but normally a [TextBlock](../windows.ui.xaml.controls/textblock.md) by itself isn't a full-fledged control.
The peer also has other behaviors that are provided by the base [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) class. For more info, see "Base implementation in FrameworkElementAutomationPeer" section of [Custom automation peers](https://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4).

### TextPattern support

 [TextBlockAutomationPeer](textblockautomationpeer.md) supports the **TextPattern**  Microsoft UI Automation pattern. The support for this pattern is implemented as native code by the peer, so you won't see public API for the [TextBlockAutomationPeer](textblockautomationpeer.md) peer class that exposes the pattern implementation for extension. And you won't see [ITextRangeProvider](../windows.ui.xaml.automation.provider/itextrangeprovider.md) and the similar managed interfaces in the [TextBlockAutomationPeer](textblockautomationpeer.md) inheritance. But Microsoft UI Automation clients can use the **TextPattern** pattern implemented by this peer and call its native API surface.

Here are some specifics of the [TextPattern](https://msdn.microsoft.com/library/ddcf7ecd-7ed2-4b57-82a7-c7e1608dbfa1) implementation in [TextBlockAutomationPeer](textblockautomationpeer.md): 
+ [Move](https://msdn.microsoft.com/library/09cd8826-4fdf-4ea5-8159-18bb81e3b5cf), [MoveEndpointByUnit](https://msdn.microsoft.com/library/3c0b9357-0f51-4044-8a5a-1f68af7a9762) and [ExpandToEnclosingUnit](https://msdn.microsoft.com/library/6128b0ef-e78d-4f87-bc70-ab5ac0d055cf) are supported for all [TextUnit](https://msdn.microsoft.com/library/518318fc-d60f-41b7-a6da-1f2bf5c2e494) units including the **Format** value.
+ [GetAttributeValue](https://msdn.microsoft.com/library/a72e780e-30e3-4feb-8f47-46b9f1714061) returns results within ranges for these text attributes: **UIA_FontNameAttributeId**, **UIA_FontSizeAttributeId**, **UIA_FontWeightAttributeId**, **UIA_ForegroundColorAttributeId**, **UIA_CultureAttributeId**, **UIA_IsHiddenAttributeId**, **UIA_IsItalicAttributeId**, **UIA_IsReadOnlyAttributeId**, **UIA_CapStyleAttributeId**, **UIA_HorizontalTextAlignmentAttributeId**, **UIA_IndentationFirstLineAttributeId**, **UIA_IndentationLeadingAttributeId**, **UIA_IsSuperscriptAttributeId**, **UIA_IsSubscriptAttributeId**, **UIA_MarginBottomAttributeId**, **UIA_MarginLeadingAttributeId**, **UIA_MarginTopAttributeId**, **UIA_MarginTrailingAttributeId**.
+ For the [Move](https://msdn.microsoft.com/library/09cd8826-4fdf-4ea5-8159-18bb81e3b5cf), [MoveEndpointByUnit](https://msdn.microsoft.com/library/3c0b9357-0f51-4044-8a5a-1f68af7a9762) and [ExpandToEnclosingUnit](https://msdn.microsoft.com/library/6128b0ef-e78d-4f87-bc70-ab5ac0d055cf)  API when using the **Format** value, a format change is defined as a change within a range in any of the supported text attributes listed above.
+ [ScrollIntoView](https://msdn.microsoft.com/library/58044de0-124f-4efd-a14f-4865f3278421) is exposed in the pattern, but can only result in a behavior if the owner control is contained within a [ScrollViewer](../windows.ui.xaml.controls/scrollviewer.md). Otherwise a [TextBlock](../windows.ui.xaml.controls/textblock.md) doesn't have its own scrolling behavior. If the [TextBlock](../windows.ui.xaml.controls/textblock.md) does have a [ScrollViewer](../windows.ui.xaml.controls/scrollviewer.md) parent, then the [ScrollIntoView](https://msdn.microsoft.com/library/58044de0-124f-4efd-a14f-4865f3278421) call fires a system event that requests the parent [ScrollViewer](../windows.ui.xaml.controls/scrollviewer.md) to scroll. The *alignToTop* value is ignored.


## -examples

## -see-also
[FrameworkElementAutomationPeer](frameworkelementautomationpeer.md)