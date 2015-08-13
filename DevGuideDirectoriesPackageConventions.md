# Directory/Package conventions #

GWT projects are overlaid onto Java packages such that most of the configuration can be inferred from the classpath and your [module definitions](DevGuideModules.md).
If you are starting a GWT project from scratch, you should use the standard GWT package layout, which makes it easy to differentiate [client-side code](DevGuideClientSide.md) from [server-side code](DevGuideServerSide.md).

The easiest way to create a GWT project from scratch is to use the [projectCreator script](DevGuideProjectCreator.md) and [applicationCreator](DevGuideApplicationCreator.md) scripts.  These scripts will create the directories needed for a sample project and populate the directories with a minimal sample project.  For example, suppose your new project is called "Calendar" and you want to create it inside package _com.example.cal_.  In GWT terminology, the name of your module would be _com.example.cal.Calendar_.

The standard directory layout would look like this:

|  **Directory** |  **Purpose** |
|:---------------|:-------------|
|   `src/com/example/cal/`  |  The project root package contains [module XML files](DevGuideModuleXml.md)  |
|   `src/com/example/cal/client/`  |  Client-side source files and subpackages |
|   `src/com/example/cal/server/`  |  Server-side code and subpackages |
|   `src/com/example/cal/public/`  |  Static resources that can be served publicly.  Files in the public directory are copied into the same directory as the GWT compiler output. |
|   `www/com.example.cal.Calendar/`| Directory where the GWT compiler writes output and files on the public path are copied. |
|   `test/`      | Directory for unit test class source files |
|   `tomcat/`    | Directory created for hosted mode's internal tomcat server.  This directory is created automatically when hosted mode is run sucessfully for the first time.|

The working files in the project would be arranged as follows:

|  **File** |  **Purpose** |
|:----------|:-------------|
|   `src/com/example/cal/Calendar.gwt.xml`  |  A common base [module](DevGuideModules.md) for your project that inherits `com.google.gwt.user.User` module.  Intended to be used by other GWT modules. |
|   `src/com/example/cal/CalendarApp.gwt.xml`  |  Inherits the com.example.cal.Calendar` module (above) and adds an entry point class |
|   `src/com/example/cal/client/CalendarApp.java`  |  Client-side Java source for the entry-point class |
|   `src/com/example/cal/client/spelling/SpellingService.java`  |  An RPC service interface defined in a subpackage |
|   `src/com/example/cal/server/spelling/SpellingServiceImpl.java`  |  Server-side Java source that implements the logic of the spelling service |
|   `src/com/example/cal/public/Calendar.html`  |  An HTML page that loads the calendar app |
|   `src/com/example/cal/public/Calendar.css`  |  A stylesheet that styles the calendar app |
|   `Calendar-shell` or `Calendar-shell.cmd`   | Command-line script to run the Calendar module in hosted mode (generated by [applicationCreator](DevGuideApplicationCreator.md)) |
|   `Calendar-compile` or `Calendar-compile.cmd`   | Command-line script to compile the Calendar module into JavaScript to run in web mode (generated by [applicationCreator](DevGuideApplicationCreator.md)) |
|   `src/com/example/cal/public/images/logo.gif`  |  A logo      |
|   `www/com.example.cal.Calendar/Calendar.html`| Host page for running your browser in hosted mode.  This file is created after a compile is run. |

Additionally the [junitCreator](DevGuideJunitCreator.md) and [i18nCreator](DevGuideI18nCreator.md) scripts will populate the standard project with example unit test case and internationalization classes respectively.

> _Tip: The applicationCreator script insists the name_client_be in the package before the path name, such as_com.example.cal.client.Calendar_.  In most other places when you are asked to provide the full module, the_.client_substring is omitted.
>_

### See Also ###

  * [Command Line Tools](DevGuideCommandLineTools.md)