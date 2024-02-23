# Highlight of SCADA HMI 2.0 New Features

## View Structure and Navigation

-   ![A screenshot of a computer Description automatically
    generated](media/image1.png){width="1.8125in"
    height="5.746527777777778in"}**The number of views that need to be
    developed by the SI has been significantly reduced.** Originally, a
    "Mobile", "Tablet", "Desktop", and "Overview Widget" view had to be
    developed for every location. Now, only a "P&ID" view needs to be
    developed and only for process locations. See image on the right for
    an example view structure. Note also that any type of view can be
    easily overridden with a custom view by placing that view in the
    appropriate location folder. For example, if a SI would like to
    create a custom mobile view for a certain location, they just create
    a view call "Mobile" in that location folder and that view will be
    used at runtime. Not only does this feature speed up development
    time, it also helps ensure consistency within a project and across
    multiple projects. It also makes maintenance easier since there will
    be significantly fewer views to maintain.

-   **Navigation is now URL based.** This means multiple tabs/windows
    will behave independently. The browser back and forward buttons will
    work as expected. Finally, any location/view can be bookmarked by
    the user.

-   **Navigation performance has been significantly improved.**
    Originally, before a view can be rendered, the location details had
    to be retrieved from the database. Not only did this slow
    responsiveness but the entire SCADA HMI would be unusable if the
    connection to the database was lost. Now the location details can be
    retrieved from a session property in constant time (the fastest
    complexity time possible) with no scripting overhead. This also
    allows more computationally complex details like tag path and
    children locations to be cached at build-time.

## Faceplates and Docks

-   **The faceplate skeleton has been completely refactored to improve
    performance and customizability.** Originally, there was a lot of
    scripting to figure out which tab view to render based on the UDT
    type. This decreased performance and a SI would have to update the
    scripting in multiple places to add a new faceplate or faceplate tab
    view. Now, which view to render comes from a custom property within
    the UDT (see image below). This means SIs can now easily add, edit
    and remove tab views for specific user defined UDTs. ![A screenshot
    of a computer program Description automatically
    generated](media/image2.png){width="4.645833333333333in"
    height="2.8996751968503935in"}

-   ![A screenshot of a computer program Description automatically
    generated](media/image3.png){width="2.5694444444444446in"
    height="4.277777777777778in"}**Form templates have been added to
    speed up development, improve maintainability, and ensure
    consistency when developing faceplates and docks.** Most forms
    consist of a list of rows where each row consists of a label, a form
    of input/output, and possibly units. SIs no longer have to do the
    tedious work of lining up rows, enforcing security, read/writing tag
    values, and adding the correct style class. This is taken care of in
    the form templates. Also, maintenance is much easier since only a
    view places need to be updated to update every faceplate/dock that
    uses form templates. See image on right of a custom dock made using
    form templates.

## UDTs and Tags

-   ![A screenshot of a computer program Description automatically
    generated](media/image4.png){width="2.4375in"
    height="5.715277777777778in"}**UDT inheritance can now be used**.
    UDT inheritance allows SIs to make modifications to the core UDTs
    without breaking their respective symbol/faceplate views. This also
    allows the SI to setup multiple UDTs of a similar type but from
    different AOIs. For example, an SI can setup a VFD UDT and a
    Soft-Start UDT that inherent from the same Motor UDT and use the
    same symbol and faceplate. This will also make maintenance easier
    since there will be less core UDTs, symbols, and faceplates to
    maintain. See image on the right for an example UDT structure using
    inheritance.

-   **UDT parameters and custom properties are used to speed up
    development and to make UI modifications.** Parameters are used
    internally by the UDT to form opc tag paths and alarm descriptions.
    Custom properties are used by the HMI framework to automate
    overviews, mobile views, trending, etc ... Both are used to speed up
    development and reduce bugs.

Performance Enhancements

-   **Tag groups are used to reduce CPU overhead for tag scanning.**

-   **Updated method for alarm scanning.**

-   **Unnecessary scripting has been removed from core component
    symbols.**

## New Tools

-   **New Ad Hoc Reporting tool.**

-   **Updated Ad Hoc Alarm Notification tool to quickly create and
    customize alarm pipelines/rosters.**

-   **Updated Ad Hoc Trending tool with an easier to use interface.**

-   **UI update for all tools to improve consistency.**

**\
**

## Improved SI Resources

-   **A fully simulated project that can be ran in parallel to
    development.**

-   **Series of videos from basic to advanced covering all phases of
    development.**

-   **Cleaner separation of template resources from user defined
    resources.**
