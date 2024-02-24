# SCADA 2.x

This is a new major version of the American Water Ignition HMI SCADA framework.
In line with the semantic versioning principles, this release has breaking changes
and is not backwards compatible with version 1.x. While this version is intended for
new projects, some features can be incorporated into version 1.x on a case-by-case basis.

## Highlights

### Views and Navigation

#### View development significantly reduced

For the previous version, a
`Mobile`, `Tablet`, `Desktop`, and `Overview Widget` view had to be
developed for every location. With this version, only a `P&ID` view needs to be
developed and only for process locations. See image below for
an example view structure. Note also that any type of view can
easily be overridden with a custom view by placing that view in the
appropriate location folder. For example, if a developer would like to
create a custom mobile view for a certain location, they just create
a view call `Mobile` in that location's folder and that view will be
used at runtime. Not only does this feature speed up development
time, it also helps ensure consistency within a project and across
multiple projects. It also makes maintenance easier since there will
be significantly fewer views to maintain.

<img src="../img/view_structure.png" alt="View Structure" style="margin-bottom:15px;">

#### Navigation is now URL based

URL navigation allows multiple tabs and windows on the same device
to behave independently. The browser back and forward buttons will
work as expected. Also, any location view can be bookmarked by
the user.

#### Navigation performance significantly improved

For the previous version, before a view can be rendered, the location details had
to be retrieved from the database. Not only did this slow
responsiveness but the entire SCADA HMI would be unusable if the
connection to the database was lost. Now the location details can be
retrieved from a session property in constant time (the fastest
complexity time possible) with no scripting overhead. This also
allows more computationally complex details like tag path and
children locations to be cached at build-time.


### UDTs and Tags

#### UDT inheritance

UDT inheritance allows developers to make modifications to the core UDTs
without breaking their respective symbol/faceplate views. This also
allows the developer to setup multiple UDTs of a similar type but for
different AOIs. For example, a developer can setup a VFD UDT and a
Soft-Start UDT that inherent from the same Motor UDT and use the
same symbol and faceplate. This also makes maintenance easier
since there will be less core UDTs, symbols and faceplates to
maintain. See image below for an example UDT structure using
inheritance.

<img src="../img/udt_structure.png" alt="View Structure" style="margin-bottom:15px;">

#### UDT parameters

Effective use of UDT parameters speeds up development and reduces bugs. For example, 
a parameter called `opcPrefix` can be used to map a PLC AOI's atomic tags to a UDT's atomic tags with 
a binding like `{opcPrefix}.Running` for a motor running status. Similar for alarms, parameters called 
`locationName` and `componentName` can be used to create consistant alarm descriptions with the 
binding `{locationName} {componentName} {alarm}`. 

#### UDT custom properties

UDT custom properties are used by the HMI framework to automate overview displays, mobile views, 
trending pens, etc ... Any UDT that inherits from the core UDT `Components/Component` will get
these custom properties and will be considered a "component" by the HMI framework. These custom 
properties allow the developer to tweak the behavior of the HMI framework without modifying any of 
the scripting. See image below for the custom properties of a motor UDT.

<img src="../img/motor_custom_props.png" alt="View Structure" style="margin-bottom:15px;">



### Faceplates and Docks

#### Faceplate skeleton refactored

Faceplate skeleton refactored to improve performance and customizability. 
Originally, there was a lot of
scripting to figure out which tab view to render based on the UDT
type. This decreased performance and a SI would have to update the
scripting in multiple places to add a new faceplate or faceplate tab
view. Now, which view to render comes from a custom property within
the UDT (see image below). This means SIs can now easily add, edit
and remove tab views for specific user defined UDTs.

#### Form templates

Form templates have been added to speed up development, improve maintainability, and ensure
consistency when developing faceplates and docks.** Most forms
consist of a list of rows where each row consists of a label, a form
of input/output, and possibly units. SIs no longer have to do the
tedious work of lining up rows, enforcing security, read/writing tag
values, and adding the correct style class. This is taken care of in
the form templates. Also, maintenance is much easier since only a
view places need to be updated to update every faceplate/dock that
uses form templates. See image on right of a custom dock made using
form templates.




### Performance Enhancements

#### Tag groups 

Tag groups are used to reduce CPU overhead for tag scanning.

#### Alarm scanning

Updated method for alarm scanning

#### Symbol script transforms

Unnecessary scripting has been removed from core component symbols.


### New Tools

#### Ad Hoc Reporting Tool

#### Updated Alarm Notification Tool

Updated Ad Hoc Alarm Notification tool to quickly create and
customize alarm pipelines/rosters.

#### Updated Ad Hoc Trending Tool 

with an easier to use interface

#### UI Update 

for all tools to improve consistency.**



### Improved Resources

#### Simulated Project

A fully simulated project that can be ran in parallel to development.

#### Cleaner separation of shared resources vs user-defined resources

#### Videos

Under development

#### Improved Documentation

Under development

#### Git Integration?
