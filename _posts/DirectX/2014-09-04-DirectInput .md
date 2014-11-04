---
layout: post
title: DirectInput 
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

FORMAT:

    less important.

    **important.**

    <span style="color:#e53333;">important.</span>

    **<span style="color:#e53333;">very important.</span>**

    <span style="color:#cc33e5;"><span style="color:#000000;"><span
style="color:#ee33ee;">a little don't </span><span
style="color:#ee33ee;">understand</span></span><span
style="color:#ee33ee;">.</span></span>

    <span style="color:#00d5ff;">can't understand.</span>

    **<span style="background-color:#e53333;">Functions and
Structures</span>**

------------------------------------------------------------------------

 Reference:

<http://msdn.microsoft.com/en-us/library/windows/desktop/ee418998(v=vs.85).aspx>

Introduction to DirectInput {#TopicTitle style="padding-bottom:35px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:36px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#707070;word-spacing:0px;padding-top:30px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
===========================

<span style="font-size:14px;">DirectInput is an API for input devices
including the mouse, keyboard, joystick, and other game controllers, as
well as for force-feedback (input/output) devices.</span>

<span style="font-size:14px;">This topic provides a brief overview of
the capabilities of DirectInput and how to set it up in an application.
For a more comprehensive view of how DirectInput works, see</span><span
class="Apple-converted-space" style="font-size:14px;"> </span>[<span
style="font-size:14px;">Understanding
DirectInput</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee418998(v=vs.85).aspx)<span
style="font-size:14px;">. For a step-by-step guide to using the
DirectInput API, see</span><span class="Apple-converted-space"
style="font-size:14px;"> </span>[<span style="font-size:14px;">Using
DirectInput</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee416845(v=vs.85).aspx)<span
style="font-size:14px;">.</span>

<span id="the_power_of_directinput"></span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span>

<span style="font-size:24px;">The Power of DirectInput</span> {.heading style="padding-bottom:5px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:18px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#db7100;word-spacing:0px;padding-top:5px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
=============================================================

<div id="the_power_of_directinput1" class="hxnx1"
style="widows:2;text-transform:none;text-indent:0px;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<span style="font-size:14px;">DirectInput enables an application to
retrieve data from input devices even when the application is in the
background. It also provides full support for any type of input device,
as well as for force feedback.</span>

<span style="font-size:14px;">Through</span>**<span
style="font-size:14px;"> action mapping</span>**<span
style="font-size:14px;">, </span><span
style="font-size:14px;">applications can retrieve input data without
needing to know what kind of device is being used to generate it.</span>

**<span style="font-size:14px;">The extended services and improved
performance of DirectInput make it a valuable tool for games,
simulations, and other real-time interactive applications running under
Windows.</span>**

<span style="font-size:14px;">DirectInput does not provide any
advantages for applications that use the keyboard for text entry or the
mouse for navigation. For more information, see</span><span
class="Apple-converted-space" style="font-size:14px;"> </span>[<span
style="font-size:14px;">Interaction with
Windows</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee418998(v=vs.85).aspx#Interaction_with_Windows)<span
style="font-size:14px;">.</span>

</div>

<span id="getting_started_with_directinput"></span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span>

<span style="font-size:24px;">Getting Started with DirectInput</span> {.heading style="padding-bottom:5px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:18px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#db7100;word-spacing:0px;padding-top:5px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
=====================================================================

<div id="getting_started_with_directinput1" class="hxnx1"
style="widows:2;text-transform:none;text-indent:0px;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<span style="font-size:14px;">This topic is an overview of what is
involved in setting up and using DirectInput in a simple
application.</span>

<span style="font-size:14px;">For details and examples of these steps,
see</span><span class="Apple-converted-space"
style="font-size:14px;"> </span>[<span style="font-size:14px;">Using
DirectInput</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee416845(v=vs.85).aspx)<span
style="font-size:14px;">.</span>

<div class="alert">

![Ee418273.note(en-us,VS.85).gif](http://i.msdn.microsoft.com/Hash/030c41d9079671d09a62d8e2c1db6973.gif "Ee418273.note(en-us,VS.85).gif")Note
<span style="font-size:14px;">To understand DirectInput, it is essential
to understand the following terms:</span>

 ***<span style="font-size:14px;">DirectInput object</span>*** 
:   <span style="font-size:14px;">The root DirectInput interface.</span>

 ***<span style="font-size:14px;">Device</span>*** 
:   <span style="font-size:14px;">A keyboard, mouse, joystick, or other
    input device.</span>

 ***<span style="font-size:14px;">DirectInputDevice object</span>*** 
:   <span style="font-size:14px;">Code representing a keyboard, mouse,
    joystick, or other input device.</span>

 ***<span style="font-size:14px;">Device object</span>*** 
:   <span style="font-size:14px;">Code representing a key, button,
    trigger, and so on found on a DirectInput device object. Also called
    device object instance.</span>

</div>

<span style="font-size:14px;">The following steps represent a simple
implementation of DirectInput in which the application takes
responsibility for ascertaining what device object (button, axis, and so
on) generated each item of data.</span>

1.  <span style="color:#e53333;font-size:14px;">**Create the DirectInput
    object.**</span>

    <span style="font-size:14px;">You use methods of this object to
    enumerate devices and create DirectInput device objects.</span>

2.  <span style="color:#e53333;font-size:14px;">**Enumerate
    devices.**</span>

    <span style="font-size:14px;">This is not an essential step if you
    intend to use only the system mouse or keyboard. To ascertain what
    other input devices are available on the user's system, have
    DirectInput enumerate them. Each time DirectInput finds a device
    that matches the criteria you set, it gives you the opportunity to
    examine the device's capabilities. It also retrieves a unique
    identifier that you can use to create a DirectInput device object
    representing the device.</span>

3.  <span style="color:#e53333;font-size:14px;">**Create a
    DirectInputDevice object for each device you want to use.**</span>

    <span style="font-size:14px;">To do this, you need the unique
    identifier retrieved during enumeration. For the system mouse or
    keyboard, you can use a standard </span>**<span
    style="font-size:14px;">globally unique identifier (GUID).</span>**

4.  <span style="color:#e53333;font-size:14px;">**Set up the
    device.**</span>

    <span style="font-size:14px;">For each device, first set the
    cooperative level, which determines the way the device is shared
    with other applications or the system. You must also set the data
    format used for identifying device objects, such as buttons and
    axes, within data packets. If you intend to retrieve buffered
    data-that is, events rather than states-you also need to set a
    buffer size. Optionally, at this stage you can retrieve information
    about the device and tailor the application's behavior accordingly.
    You can also set properties such as the range of values returned by
    joystick axes.</span>

5.  <span style="color:#e53333;font-size:14px;">**Acquire the
    device.**</span>

    <span style="font-size:14px;">At this stage you tell DirectInput
    that you are ready to receive data from the device.</span>

6.  <span style="color:#e53333;font-size:14px;">**Retrieve
    data.**</span>

    <span style="font-size:14px;">At regular intervals, typically on
    each pass through the message loop or rendering loop, get either the
    current state of each device or a record of events that have taken
    place since the last retrieval. If you prefer, you can have
    DirectInput notify you whenever an event occurs.</span>

7.  <span style="color:#e53333;font-size:14px;">**Act on the
    data.**</span>

    <span style="font-size:14px;">The application can respond either to
    the state of buttons and axes or to events such as a key being
    pressed or released.</span>

8.  <span style="color:#e53333;font-size:14px;">**Close
    DirectInput.**</span>

    <span style="font-size:14px;">Before exiting, your application
    should unacquire all devices and release them, then release the
    DirectInput object.</span>

<span style="font-size:14px;">This is not the only approach to
implementing DirectInput. To take advantage of the great variety of
input devices available now and later, and to simplify configuration for
the user, you can use action mapping.</span>

<span style="color:#ee33ee;font-size:14px;">By setting an action map for
a device, you let DirectInput decide which device object to use for each
application action. For example, instead of specifying that the throttle
in your racing game must always be controlled by the y-axis, you can
create an action called AXIS\_THROTTLE and have DirectInput assign that
action to the most appropriate axis available on the device. When you
retrieve events, you identify them by their associated actions rather
than by the device objects that generated them.</span>

------------------------------------------------------------------------

</div>

 

Understanding DirectInput {#TopicTitle style="padding-bottom:35px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:36px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#707070;word-spacing:0px;padding-top:30px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
=========================

<span style="font-size:14px;">This topic covers the underlying structure
of Microsoft DirectInput and its relationship to the Microsoft Windows
message system.</span>

<span style="font-size:14px;">For practical information about how to
implement the elements of DirectInput introduced here, see</span><span
class="Apple-converted-space" style="font-size:14px;"> </span>[<span
style="font-size:14px;">Using
DirectInput</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee416845(v=vs.85).aspx)<span
style="font-size:14px;">.</span>

<span id="DirectInput_Objects"></span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span>

<span style="font-size:24px;">DirectInput Objects</span> {.heading style="padding-bottom:5px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:18px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#db7100;word-spacing:0px;padding-top:5px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
========================================================

<div id="DirectInput_Objects1" class="hxnx1"
style="widows:2;text-transform:none;text-indent:0px;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

An input-only DirectInput implementation consists of the DirectInput
object, which supports<span
class="Apple-converted-space"> </span>[IDirectInput8
Interface](http://msdn.microsoft.com/en-us/library/windows/desktop/ee417799(v=vs.85).aspx),
a <span style="color:#e53333;">Component Object Model (COM)</span>
interface, and a DirectInputDevice object for each input device that
provides data. Each DirectInputDevice object in turn has<span
class="Apple-converted-space"> </span>*device objects*, which are
individual controls or switches, such as keys, buttons, or axes. Device
objects are also called<span
class="Apple-converted-space"> </span>***device object instances*****.**

**Each DirectInputDevice object represents one input device, such as a
mouse, keyboard, or joystick**. In the DirectInput API, the <span
style="font-size:14px;">word</span><span class="Apple-converted-space"
style="font-size:14px;"> </span>*<span
style="color:#e53333;font-size:14px;">**joystick**</span>*<span
class="Apple-converted-space"
style="color:#e53333;font-size:14px;">** **</span><span
style="font-size:14px;">means any type of input device other than a
mouse or keyboard</span><span style="font-size:14px;">. A piece of
hardware that is really a combination of different types of input
devices, such as a keyboard with a touchpad, can be represented by two
or more DirectInputDevice objects. </span><span
style="font-size:14px;">A force-feedback device is represented by a
single joystick object that handles both input and output.</span>

<span style="font-size:14px;">DirectInputDevice objects instantiate
the</span><span class="Apple-converted-space"
style="font-size:14px;"> </span>[<span
style="background-color:#e53333;color:#000000;font-size:14px;">**IDirectInputDevice8
Interface**</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/ee417816(v=vs.85).aspx)<span
style="background-color:#e53333;color:#000000;font-size:14px;">**.**</span><span
style="font-size:14px;"> The application ascertains the number and type
of device objects available by using the</span><span
class="Apple-converted-space" style="font-size:14px;"> </span>[**<span
style="background-color:#e53333;font-size:14px;">IDirectInputDevice8::EnumObjects</span>**](http://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.directx_sdk.idirectinputdevice8.idirectinputdevice8.enumobjects(v=vs.85).aspx)<span
class="Apple-converted-space" style="font-size:14px;"> </span><span
style="font-size:14px;">method. Individual device objects are not
encapsulated as code objects, but are described in</span>[<span
style="background-color:#e53333;font-size:14px;">**DIDEVICEOBJECTINSTANCE**</span>](http://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.directx_sdk.reference.dideviceobjectinstance(v=vs.85).aspx)<span
class="Apple-converted-space" style="font-size:14px;"> </span><span
style="font-size:14px;">structures.</span>

<span style="font-size:14px;">All DirectInput interfaces are available
in ANSI and Unicode versions. If "UNICODE" is defined during
compilation, the Unicode versions are used.</span>

</div>

<span id="Interaction_with_Windows"></span><span
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"></span>

<span style="font-size:24px;">Interaction with Windows</span> {.heading style="padding-bottom:5px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:18px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#db7100;word-spacing:0px;padding-top:5px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
=============================================================

<div id="Interaction_with_Windows1" class="hxnx1"
style="widows:2;text-transform:none;text-indent:0px;font:12px 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<span style="font-size:14px;">Because DirectInput works directly with
the device drivers, it either suppresses</span><span
style="font-size:14px;"> or ignores Windows mouse and keyboard messages.
It also ignores mouse and keyboard settings made by the user in Control
Panel. </span><span style="font-size:14px;">It does, however, use the
calibrations set for a joystick or other game controller.</span>

<span style="font-size:14px;">DirectInput does not recognize keyboard
character repeat settings. </span><span style="font-size:14px;">When
using buffered data, </span><span style="font-size:14px;">DirectInput
interprets each press and release as a single event with no
repetition.</span><span style="font-size:14px;"> When using immediate
data, DirectInput is concerned only with the present physical state of
the keys, not with keyboard events as interpreted by Windows.</span>

<span style="font-size:14px;">DirectInput does not perform any character
conversion or translation. For example, the SHIFT key is treated like
any other key, not as a modifier of another keypress. Keys return the
same identifiers regardless of the user's system language
settings.</span>

**<span style="font-size:14px;">Because DirectInput works directly with
the mouse driver, it bypasses the subsystem of Windows that interprets
mouse data for windowed applications. </span><span
style="font-size:14px;">Applications that rely on the Windows cursor for
navigation should continue to use the standard Windows mouse messages
and Microsoft Win32 functions.</span>**

<span style="font-size:14px;">When using the system mouse in exclusive
mode, DirectInput suppresses mouse messages, and therefore Windows is
unable to show the standard cursor.</span>

<span style="font-size:14px;">DirectInput ignores Control Panel settings
such as acceleration and swapped buttons. However, DirectInput
recognizes settings in the driver itself. For example, if the user has a
three-button mouse and uses the driver-utility software to make the
middle button a double-click shortcut, DirectInput reports a click of
the middle button as two clicks of the primary button.</span>

</div>

------------------------------------------------------------------------

  {#TopicTitle style="padding-bottom:35px;widows:2;text-transform:none;text-indent:0px;margin:0px;font:36px 'Segoe UI Light', 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#707070;word-spacing:0px;padding-top:30px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}
=

\

 







