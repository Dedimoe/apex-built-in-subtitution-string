# apex-built-in-subtitution-string
apex built in subtitution string

<a id="0"></a>
### Using Built-in Substitution Strings
App Builder supports many built-in substitution strings. You can reference these substitution strings to achieve specific types of functionality.

Tip: Note that bind variable :USER has special meaning within the database. Also, the term Direct PL/SQL refers to PL/SQL that can be used in stored database objects such as procedures and functions.


1. [APEX$ROW_NUM](#1)
2. [APEX$ROW_SELECTOR](#2)
3. [APEX$ROW_STATUS](#3)
4. [APP_ID](#4)
5. [APP_ALIAS](#5)
6. [APP_AJAX_X01, ... APP_AJAX_X10](#6)
7. [APP_BUILDER_SESSION](#7)
8. [APP_DATE_TIME_FORMAT](#8)
9. [APP_IMAGES](#9)
10. [APP_NLS_DATE_FORMAT](#10)
11. [APP_NLS_TIMESTAMP_FORMAT](#11)
12. [APP_NLS_TIMESTAMP_TZ_FORMAT](#12)
13. [APP_PAGE_ALIAS](#13)
14. [APP_PAGE_ID](#14)
15. [APP_REGION_ID](#15)
16. [APP_REGION_STATIC_ID](#16)
17. [APP_REQUEST_DATA_HASH](#17)
18. [APP_SESSION](#18)
19. [APP_SESSION_VISIBLE](#19)
20. [APP_TITLE](#20)
21. [APP_UNIQUE_PAGE_ID](#21)
22. [APP_USER](#22)
23. [AUTHENTICATED_URL_PREFIX](#23)
24. [BROWSER_LANGUAGE](#24)
25. [CURRENT_PARENT_TAB_TEXT](#25)
26. [DEBUG](#26)
27. [HOME_LINK](#27)
28. [IMAGE_PREFIX](#28)
29. [JET_BASE_DIRECTORY](#29)
30. [JET_CSS_DIRECTORY](#30)
31. [JET_JS_DIRECTORY](#31)
32. [LOGIN_URL](#32)
33. [LOGOUT_URL](#33)
34. [APP_TEXT$Message_Name, APP_TEXT$Message_Name$Lang](#34)
35. [PRINTER_FRIENDLY](#35)
36. [PROXY_SERVER](#36)
37. [PUBLIC_URL_PREFIX](#37)
38. [REQUEST](#38)
39. [Using REQUEST](#39)
40. [SCHEMA OWNER](#40)
41. [SQLERRM](#41)
42. [SYSDATE_YYYYMMDD](#42)
43. [THEME_DB_IMAGES](#43)
44. [THEME_IMAGES](#44)
45. [WORKSPACE_IMAGES](#45)
46. [WORKSPACE_ID](#46)

<a id="1"></a>
### 1 APEX$ROW_NUM
APEX$ROW_NUM refers the currently processed row number of a submitted tabular form data. You can use this placeholder in validations, processes, and conditions associated with a tabular form to refer to the row number of the currently processed tabular form row.

Table 3-3 APEX$ROW_NUM Syntax

Reference Type | Syntax
:--- | :--
Bind variable | ```:APEX$ROW_NUM```
PL/SQL | ```V('APEX$ROW_NUM')```
Substitution string | ```&APEX$ROW_NUM.```

[^top](#0)
<a id="2"></a>
### 2 APEX$ROW_SELECTOR
Use APEX$ROW_SELECTOR in validations, processes, and conditions associated with a tabular form to refer to the row selector check box in a tabular form. This placeholder returns X if the tabular form row selector check box of the currently processed tabular form row is checked and NULL if it unchecked.

Table 3-4 APEX$ROW_SELECTOR Syntax

Reference Type	Syntax
Bind variable

:APEX$ROW_SELECTOR

PL/SQL

V('APEX$ROW_SELECTOR')

Substitution string

&APEX$ROW_SELECTOR.

Parent topic: Using Built-in Substitution Strings

<a id="3"></a>
### 3 APEX$ROW_STATUS
Use APEX$STATUS in validations, processes, and conditions associated with a tabular form to refer to the row status in a tabular form. This placeholder returns the status of C if created, U if updated, or D if deleted for the currently processed tabular form row.

Table 3-5 APEX$ROW_STATUS Syntax

Reference Type	Syntax
Bind variable

:APEX$ROW_STATUS

PL/SQL

V('APEX$ROW_STATUS')

Substitution string

&APEX$ROW_STATUS.

Parent topic: Using Built-in Substitution Strings

<a id="4"></a>
### 4 APP_ID
APP_ID identifies the application ID of the currently executing application.

Table 3-6 APP_ID Syntax

Reference Type	Syntax
Bind variable

:APP_ID

Direct PL/SQL

APEX_APPLICATION.G_FLOW_ID (A NUMBER)

PL/SQL

NV('APP_ID')

Substitution string

&APP_ID.

SYS_CONTEXT variable

SYS_CONTEXT('APEX$SESSION', 'APP_ID')

Substitution String Reference Example

The following is an example of a substitution string reference:

Copyf?p=&APP_ID.:40:&APP_SESSION.
SYS_CONTEXT Variable Example

The following is a SYS_CONTEXT variable example:

CopySELECT ... WHERE application_id = SYS_CONTEXT('APEX$SESSION', 'APP_ID')
Oracle Application Express sets up the APEX$SESSION context when it starts to process an incoming request. For example, you can use the value of 'APP_ID' to access the current application ID in queries and Virtual Private Database (VPD) security policies that protect your table data.

Parent topic: Using Built-in Substitution Strings

<a id="1"></a>
### 5 APP_ALIAS
APP_ALIAS is an alphanumeric name for the current application. APP_ALIAS is different from the APP_ID in that the APP_ID must be unique over all workspaces and all applications hosted in one database. In contrast, APP_ALIAS must be unique within a workspace. For example, by using the same APP_ALIAS you can create the application, ABC, in two different workspaces. You can use APP_ALIAS almost anywhere APP_ID can be used. For example, f?p syntax can use an APP_ALIAS or an application ID as demonstrated in this example:

Copyf?p=ABC:1:&APP_SESSION.
This example runs application ABC, page 1 using the current session.

Table 3-7 APP_ALIAS Syntax

Reference Type	Syntax
Bind variable

:APP_ALIAS

PL/SQL

V('APP_ALIAS')

Substitution string

&APP_ALIAS.

The following is an HTML example:

CopyClick me to go to page 1 <a href="f?p=&APP_ALIAS.:1:&APP_SESSION."> of the current application</a>
Parent topic: Using Built-in Substitution Strings

<a id="6"></a>
### 6 AP_AJAX_X01, ... APP_AJAX_X10
APP_AJAX_Xnn specifies the values of the APP_AJAX_X01, ... APP_AJAX_X10 URL parameters most recently passed to or set within the show or accept modules. You typically use these variables in On Demand AJAX processes.

Table 3-8 APP_AJAX_Xnn Syntax

Reference Type	Syntax
Bind variable

... :APP_AJAX_X01, ... :APP_AJAX_X10
PL/SQL

... v('APP_AJAX_X01'), ... v('APP_AJAX_X10')
Substitution string

... &APP_AJAX_X01., ... &APP_AJAX_X10.
See Also:

G_X01, ... G_X10 variables in the APEX_APPLICATION in Oracle Application Express API Reference

Parent topic: Using Built-in Substitution Strings

<a id="7"></a>
### 7 APP_BUILDER_SESSION
If the user is also logged in to the workspace as a developer, APP_BUILDER_SESSION contains the current session ID of the development environment. Otherwise, APP_BUILDER_SESSION is null.

Table 3-9 APP_BUILDER_SESSION Syntax

Reference Type	Syntax
Bind variable

:APP_BUILDER_SESSION

PL/SQL

V('APP_BUILDER_SESSION')

Substitution string

&APP_BUILDER_SESSION.

Parent topic: Using Built-in Substitution Strings

<a id="8"></a>
### 8 APP_DATE_TIME_FORMAT
APP_DATE_TIME_FORMAT is the application date time format of the application. This value reflects the format specified in the Application Date Time Format attribute of the Globalization settings of an application. If the Application Date Time Format is not set in an application, then a reference to APP_DATE_TIME_FORMAT returns the database session NLS date format and the NLS time format.

Table 3-10 APP_DATE_TIME_FORMAT Syntax

Reference Type	Syntax
Bind variable

:APP_DATE_TIME_FORMAT

PL/SQL

V('APP_DATE_TIME_FORMAT')

Substitution string

&APP_DATE_TIME_FORMAT.

Parent topic: Using Built-in Substitution Strings

<a id="9"></a>
### 9 APP_IMAGES
Use this substitution string to reference uploaded images, JavaScript, and cascading style sheets that are specific to a given application and are not shared over many applications. If you upload a file and make it specific to an application, then you must use this substitution string, or bind variable.

Table 3-11 APP_IMAGES Syntax

Reference Type	Syntax
Bind variable

:APP_IMAGES

Direct PL/SQL

Not available.

PL/SQL

V('APP_IMAGES')

Substitution string

&APP_IMAGES.

Template substitution

#APP_IMAGES#

See Also:

"IMAGE_PREFIX," "WORKSPACE_IMAGES," and "About Managing Images"

Parent topic: Using Built-in Substitution Strings

<a id="10"></a>
### 10 APP_NLS_DATE_FORMAT
APP_NLS_DATE_FORMAT is the application date format of the database session. This value reflects the format specified in the Application Date Format attribute of the Globalization settings of the application. However, if the Application Date Format is not set, then APP_NLS_DATE_FORMAT returns the NLS_DATE_FORMAT value of the database session at the start of the request to the Application Express engine.

Table 3-12 APP_NLS_DATE_FORMAT Syntax

Reference Type	Syntax
Bind variable

:APP_NLS_DATE_FORMAT

PL/SQL

V('APP_NLS_DATE_FORMAT')

Substitution string

&APP_NLS_DATE_FORMAT.

Parent topic: Using Built-in Substitution Strings

<a id="11"></a>
### 11 APP_NLS_TIMESTAMP_FORMAT
APP_NLS_TIMESTAMP_FORMAT is the application timestamp format of the database session. This value reflects the format specified in the Application Timestamp Format attribute of the Globalization settings of the application. However, if the Application Timestamp Format is not set, then APP_NLS_TIMESTAMP_FORMAT return the NLS_TIMESTAMP_FORMAT value of the database session at the start of the request to the Application Express engine.

Table 3-13 APP_NLS_TIMESTAMP_FORMAT Syntax

Reference Type	Syntax
Bind variable

:APP_NLS_TIMESTAMP_FORMAT

PL/SQL

V('APP_NLS_TIMESTAMP_FORMAT')

Substitution string

&APP_NLS_TIMESTAMP_FORMAT.

Parent topic: Using Built-in Substitution Strings

<a id="12"></a>
### 12 APP_NLS_TIMESTAMP_TZ_FORMAT
APP_NLS_TIMESTAMP_TZ_FORMAT is the application timestamp time zone format of the database session. This value reflects the format specified in the Application Timestamp Time Zone Format attribute of the Globalization settings of an application. However, if the Application Timestamp Time Zone Format is not set, then APP_NLS_TIMESTAMP_TZ_FORMAT returns the NLS_TIMESTAMP_TZ_FORMAT value of the database session at the start of the request to the Application Express engine.

Table 3-14 APP_NLS_TIMESTAMP_TZ_FORMAT Syntax

Reference Type	Syntax
Bind variable

:APP_NLS_TIMESTAMP_TZ_FORMAT

PL/SQL

V('APP_NLS_TIMESTAMP_TZ_FORMAT')

Substitution string

&APP_NLS_TIMESTAMP_TZ_FORMAT.

Parent topic: Using Built-in Substitution Strings

<a id="13"></a>
### 13 APP_PAGE_ALIAS
APP_PAGE_ALIAS is an alphanumeric name for the current application page. A page alias is not case-sensitive and it is an optional page attribute. APP_PAGE_ALIAS is unique within an application. You can use APP_PAGE_ALIAS almost anywhere APP_PAGE_ID can be used.

Table 3-15 APP_PAGE_ALIAS Syntax

Reference Type	Syntax
Bind variable

:APP_PAGE_ALIAS

PL/SQL

v('APP_PAGE_ALIAS')

Substitution string

&APP_PAGE_ALIAS.

The following is an HTML example:

The alias of the current page is: &APP_PAGE_ALIAS.

Parent topic: Using Built-in Substitution Strings

<a id="14"></a>
### 14 APP_PAGE_ID
APP_PAGE_ID is the current application page ID. For example, if your application was on page 3, then the result would be 3. Using this syntax is useful when writing application components that must work generically in multiple applications.

Table 3-16 APP_PAGE_ID Syntax

Reference Type	Syntax
Bind variable

:APP_PAGE_ID

PL/SQL

:APP_PAGE_ID

PL/SQL and Direct PL

NV('APP_PAGE_ID')

Substitution string

&APP_PAGE_ID.

The following is an example of a substitution string reference:

Copyf?p=&APP_ID.:&APP_PAGE_ID.:&APP_SESSION.
Parent topic: Using Built-in Substitution Strings

<a id="15"></a>
### 15 APP_REGION_ID
APP_REGION_ID identifies the ID of the current executing region.

Table 3-17 APP_REGION_ID Syntax

Reference Type	Syntax
Bind variable

:APP_REGION_ID

PL/SQL

v('APP_REGION_ID')

Substitution string

&APP_REGION_ID.

Parent topic: Using Built-in Substitution Strings

<a id="16"></a>
### 16 APP_REGION_STATIC_ID
APP_REGION_STATIC_ID identifies the static ID of the current executing region. If no static ID has been entered by a developer, NULL is returned.

Table 3-18 APP_REGION_STATIC_ID Syntax

Reference Type	Syntax
Bind variable

:APP_REGION_STATIC_ID

PL/SQL

v('APP_REGION_STATIC_ID')

Substitution string

&APP_REGION_STATIC_ID.

Parent topic: Using Built-in Substitution Strings

<a id="17"></a>
### 17 APP_REQUEST_DATA_HASH
APP_REQUEST_DATA_HASH is a hash value of the request, item name, and item value parts in the URL. It is primarily useful to detect whether two browser requests passed different parameters to Oracle Application Express.

Table 3-19 APP_REQUEST_DATA_HASH Syntax

Reference Type	Syntax
Bind variable

:APP_REQUEST_DATA_HASH

PL/SQL

V('APP_REQUEST_DATA_HASH')

Substitution string

&APP_REQUEST_DATA_HASH.

Parent topic: Using Built-in Substitution Strings

<a id="18"></a>
### 18 APP_SESSION
APP_SESSION is the most commonly used built-in substitution strings. You can use this substitution string to create hypertext links between application pages that maintain a session state by passing the session number. Note that you can also use the substitution string SESSION in place of APP_SESSION.

Table 3-20 APP_SESSION Syntax

Reference Type	Syntax
Bind variable

:APP_SESSION

PL/SQL

V('APP_SESSION')

Short PL/SQL

V('SESSION')

Substitution string

&APP_SESSION.

SYS_CONTEXT variable

SYS_CONTEXT('APEX$SESSION', 'APP_SESSION')

Consider the following examples:

From within an HTML region:

Copy<a href="f?p=100:5:&APP_SESSION.">click me</a> 
Using PL/SQL:

Copyhtf.anchor('f?p=100:5:'||V('APP_SESSION'),'click me');
Using a SQL query:

CopySELECT htf.anchor('f?p=100:5:'||:APP_SESSION,'click me') FROM DUAL;
Using the SYS_CONTEXT variable:

CopySELECT ... WHERE apex_session_id = SYS_CONTEXT('APEX$SESSION', 'APP_SESSION')
Oracle Application Express sets up the APEX$SESSION context when it starts to process an incoming request. For example, you can use the value of 'APP_SESSION' to access the current application session in queries and VPD (Virtual Private Database) security policies that protect your table data.

Parent topic: Using Built-in Substitution Strings

<a id="19"></a>
### 19 APP_SESSION_VISIBLE
APP_SESSION_VISIBLE is similar to the built-in substitution APP_SESSION. Use this substitution string to create hypertext links between application pages that maintain a session state by passing the session number. APP_SESSION_VISIBLE always returns '0' when users are not authenticated to an application and they are using the Zero Session ID feature of Oracle Application Express.

Table 3-21 APP_SESSION_VISIBLE Syntax

Reference Type	Syntax
Bind variable

:APP_SESSION_VISIBLE

PL/SQL

V('APP_SESSION_VISIBLE')

Substitution string

&APP_SESSION_VISIBLE.

Consider the following examples:

From within an HTML region:

Copy<a href="f?p=100:5:&APP_SESSION_VISIBLE.">click me</a>
Using PL/SQL:

Copysys.htf.anchor('f?p=100:5:'||V('APP_SESSION_VISIBLE'),'click me');
Using a SQL query:

CopySELECT sys.htf.anchor('f?p=100:5:'||:APP_SESSION_VISIBLE,'clickme') FROM DUAL;
Parent topic: Using Built-in Substitution Strings

<a id="20"></a>
### 20 APP_TITLE
APP_TITLE is an alphanumeric title for the current application. The title is derived from an application substitution string called APP_TITLE. If not defined the Logo attribute will be used if it is of type text. The last fallback is the application name.

Table 3-22 APP_TITLE Syntax

Reference Type	Syntax
Bind variable

:APP_TITLE

PL/SQL

v('APP_TITLE')

Substitution string

&APP_TITLE.

The following is an HTML example:

CopyThe title of the current application is: &APP_TITLE!HTML.
Parent topic: Using Built-in Substitution Strings

<a id="21"></a>
### 21 APP_UNIQUE_PAGE_ID
APP_UNIQUE_PAGE_ID is an integer generated from an Oracle sequence which is unique for each page view. This number is used by applications to prevent duplicate page submissions and can be used for other purposes. For example, to make a unique URL and avoid browser caching issues, you can embed this number in the request or debug column in calls to the f procedure.

Table 3-23 APP_UNIQUE_PAGE_ID Syntax

Reference Type	Syntax
Bind variable

:APP_UNIQUE_PAGE_ID

PL/SQL

V('APP_UNIQUE_PAGE_ID')

Substitution string

&APP_UNIQUE_PAGE_ID.

The following is an HTML example:

CopySELECT 'f?p=100:1:'||:APP_SESSION||':'||:APP_UNIQUE_PAGE_ID||
    ':::P1_EMPNO:'||employee_id,
   first_name,
    job_id
FROM employees
Note the use of the APP_UNIQUE_PAGE_ID in the request column. This makes this URL unique and may avoid excessive browser caching problems.

Parent topic: Using Built-in Substitution Strings

<a id="22"></a>
### 22 APP_USER
APP_USER is the current user running the application. Depending upon your authentication model, the value of the user is set differently. If the application is running using database authentication, then the value of the user is the same as the database pseudo column USER. If the application uses an authentication scheme that requires the user to authenticate, the value of APP_USER is set by the authentication scheme, usually to the user name used during authentication.

Table 3-24 APP_USER Syntax

Reference Type	Syntax
Bind variable

:APP_USER

PL/SQL

V('APP_USER')

Substitution string

&APP_USER.

SYS_CONTEXT variable

SYS_CONTEXT('APEX$SESSION', 'APP_USER')

Consider the following examples:

From within an HTML region:

CopyHello you are logged in as &APP_USER.
Using PL/SQL:

Copyhtp.p('Hello you are logged in as'||V('APP_USER')); 
As a bind variable:

CopySELECT * FROM some_table WHERE user_id = :APP_USER
Using the SYS_CONTEXT variable:

CopySELECT ... WHERE username = SYS_CONTEXT('APEX$SESSION', 'APP_USER')
Oracle Application Express sets up the APEX$SESSION context when it starts to process an incoming request. For example, you can use the value of 'APP_USER' to access the current application user in queries and VPD (Virtual Private Database) security policies that protect your table data.

See Also:

"Authentication" for information about the Public User attribute

Parent topic: Using Built-in Substitution Strings

<a id="23"></a>
### 23 AUTHENTICATED_URL_PREFIX
This application-level attribute identifies a valid authenticated prefix (that is, a logged in URL prefix). You can use a relative path or a full path beginning with http. This item is useful if your application can be run in both authenticated (logged in) and public (not logged in) modes. You can use AUTHENTICATED_URL_PREFIX to construct a link to an authenticated page. This item is most useful when using basic database authentication because changes to the URL can require authentication.

Table 3-25 AUTHENTICATED_URL_PREFIX Syntax

Reference Type	Syntax
Bind variable

:AUTHENTICATED_URL_PREFIX

PL/SQL

V('AUTHENTICATED_URL_PREFIX')

Substitution string

&AUTHENTICATED_URL_PREFIX.

Parent topic: Using Built-in Substitution Strings

<a id="24"></a>
### 24 BROWSER_LANGUAGE
BROWSER_LANGUAGE refers to the web browser's current language preference.

Table 3-26 BROWSER_LANGUAGE Syntax

Reference Type	Syntax
Bind variable

:BROWSER_LANGUAGE

Direct PL/SQL

APEX_APPLICATION.G_BROWSER_LANGUAGE

PL/SQL

V('BROWSER_LANGUAGE')

Substitution string

&BROWSER_LANGUAGE.

Parent topic: Using Built-in Substitution Strings

<a id="25"></a>
### 25 CURRENT_PARENT_TAB_TEXT
CURRENT_PARENT_TAB_TEXT is most useful in page templates, but is only relevant for applications that use two-level tabs (that is, parent and standard tabs). Use this string to reference the parent tab label. This substitution string enables you to repeat the currently selected parent tab within the page template.

Table 3-27 CURRENT_PARENT_TAB_TEXT Syntax

Reference Type	Syntax
Bind variable

Not Available.

Substitution string

&CURRENT_PARENT_TAB_TEXT.

Parent topic: Using Built-in Substitution Strings

<a id="26"></a>
### 26 DEBUG
Valid values for the DEBUG flag are Yes or No. Turning debug on shows details about application processing. If you write your own custom code, you may want to generate debug information only if the debug mode is set to Yes.

Table 3-28 DEBUG Syntax

Reference Type	Syntax
Bind variable

:DEBUG

Direct PL/SQL

APEX_APPLICATION.G_DEBUG

PL/SQL

V('DEBUG')

Substitution string

&DEBUG.

The following is an example of a substitution string reference that preserves the current value of DEBUG:

Copyf?p=100:1:&APP_SESSION.::&DEBUG
Parent topic: Using Built-in Substitution Strings

<a id="27"></a>
### 27 HOME_LINK
HOME_LINK is the home page of an application. The Application Express engine redirects to this location if no page is given and if no alternative page is dictated by the authentication scheme's logic. You define the Home URL on the User Interface page, under Attributes.

Table 3-29 HOME_LINK Syntax

Reference Type	Syntax
Direct PL/SQL

APEX_APPLICATION.G_HOME_LINK

PL/SQL

V('HOME_LINK')

Template Reference

#HOME_LINK#

Substitution String

&HOME_LINK.

See Also:

"Editing User Interface Attributes" and "Attributes"

Parent topic: Using Built-in Substitution Strings

<a id="28"></a>
### 28 IMAGE_PREFIX
The value of IMAGE_PREFIX determines the virtual path the web server uses to point to the images directory distributed with Oracle Application Express. To reference uploaded images, use WORKSPACE_IMAGES and APP_IMAGES.

Table 3-30 IMAGE_PREFIX Syntax

Reference Type	Syntax
Bind variable

:IMAGE_PREFIX

Direct PL/SQL

APEX_APPLICATION.G_IMAGE_PREFIX

PL/SQL

V('IMAGE_PREFIX')

Substitution string

&IMAGE_PREFIX.

Template Substitution

#IMAGE_PREFIX#

See Also:

"APP_IMAGES"

"WORKSPACE_IMAGES"

"Editing the Application Definition"

Parent topic: Using Built-in Substitution Strings

<a id="29"></a>
### 29 JET_BASE_DIRECTORY
Use the JET_BASE_DIRECTORY substitution string to reference the base directory of the Oracle JavaScript Extension Toolkit (JET) which ships with Oracle Application Express. Supported syntax for referencing JET_BASE_DIRECTORY :

Copy#JET_BASE_DIRECTORY#
Parent topic: Using Built-in Substitution Strings

<a id="30"></a>
### 30 JET_CSS_DIRECTORY
Use the JET_CSS_DIRECTORY substitution string to reference the base directory of the Oracle JavaScript Extension Toolkit (JET) which ships with Oracle Application Express. Supported syntax for referencing JET_CSS_DIRECTORY:

Copy#JET_CSS_DIRECTORY#
Parent topic: Using Built-in Substitution Strings

<a id="31"></a>
### 31 JET_JS_DIRECTORY
Use the JET_JS_DIRECTORY substitution string to reference the JavaScript directory of the Oracle JavaScript Extension Toolkit (JET) components which ships with Oracle Application Express. Supported syntax for referencing JET_JS_DIRECTORY:

Copy#JET_JS_DIRECTORY#
Parent topic: Using Built-in Substitution Strings

<a id="32"></a>
### 32 LOGIN_URL
Use LOGIN_URL to display a link to a login page for users that are not currently logged in.

See Also:

"Authentication" and "Security Page"

Table 3-31 LOGIN_URL Syntax

Reference Type	Syntax
Bind variable

:LOGIN_URL

Direct PL/SQL

APEX_APPLICATION.G_LOGIN_URL

PL/SQL

V('LOGIN_URL')

Substitution string

&LOGIN_URL.

Template Substitution

#LOGIN_URL#

Parent topic: Using Built-in Substitution Strings

<a id="33"></a>
### 33 LOGOUT_URL
LOGOUT_URL is an application-level attribute used to identify the logout URL. This is a URL that navigates the user to a logout page or optionally directly logs out a user. To create a logout navigation bar entry, add a trailing period to &LOGOUT_URL (&LOGOUT_URL.). If you are coding a page template, use #LOGOUT_URL#.

Table 3-32 LOGOUT_URL Syntax

Reference Type	Syntax
Bind variable

:LOGOUT_URL

PL/SQL

V('LOGOUT_URL')

Substitution string

&LOGOUT_URL.

Template substitution

#LOGOUT_URL#

Parent topic: Using Built-in Substitution Strings

<a id="34"></a>
### 34 APP_TEXT$Message_Name, APP_TEXT$Message_Name$Lang
With APP_TEXT$Message_Name, APP_TEXT$Message_Name$Lang built-in substitution, you can access application defined or system defined text messages, like APEX_LANG.MESSAGE. Message_Name is the name of the text message, Message_Name has to be a valid identifier (A-Z, 0-9, $, #, _). The optional $Lang parameter can be used to access a specific translation, $Lang defaults to the current language for the page request.

Table 3-33 APP_TEXT$Message_Name, APP_TEXT$Message_Name$Lang Syntax

Reference Type	Syntax
Bind variable

:APP_TEXT$Message_Name , :APP_TEXT$Message_Name$Lang

PL/SQL

V('APP_TEXT$Message_Name') , V('APP_TEXT$Message_Name$Lang')

Substitution string

&APP_TEXT$Message_Name. , &APP_TEXT$Message_Name$Lang.

The following is an example for the default and the French text message MY_MESSAGE, using HTML escaping:

CopyDefault text: &APP_TEXT$MY_MESSAGE!HTML.
Pardon my French: &APP_TEXT$MY_MESSAGE$FR!HTML.
Parent topic: Using Built-in Substitution Strings

<a id="35"></a>
### 35 PRINTER_FRIENDLY
The value of PRINTER_FRIENDLY determines if the Application Express engine is running in print view mode. This setting can be referenced in conditions to eliminate elements not desired in a printed document from a page.

Table 3-34 PRINTER_FRIENDLY Syntax

Reference Type	Syntax
Direct PL/SQL

APEX_APPLICATION.G_PRINTER_FRIENDLY (VARCHAR2 DATATYPE)

PL/SQL

V('PRINTER_FRIENDLY')

Substitution string

&PRINTER_FRIENDLY.

Parent topic: Using Built-in Substitution Strings

<a id="36"></a>
### 36 PROXY_SERVER
PROXY_SERVER is an application attribute. The attribute may be used by regions whose source comes from a URL. The following is the correct syntax for a direct PL/SQL reference used when you are writing PL/SQL to access remote web servers from within the database (for example, when using the utl_http package shipped with the database).

CopyAPEX_APPLICATION.G_PROXY_SERVER
Parent topic: Using Built-in Substitution Strings

<a id="37"></a>
### 37 PUBLIC_URL_PREFIX
PUBLIC_URL_PREFIX is an application-level attribute that identifies a URL to toggle out of a logged in mode to a public view.

Table 3-35 PUBLIC_URL_PREFIX Syntax

Reference Type	Syntax
Bind variable

:PUBLIC_URL_PREFIX

PL/SQL

V('PUBLIC_URL_PREFIX')

Substitution string

&PUBLIC_URL_PREFIX.

Template substitution

#PUBLIC_URL_PREFIX#

Parent topic: Using Built-in Substitution Strings

<a id="38"></a>
### 38 REQUEST
Each application button sets the value of REQUEST to the name of the button or to the request value attribute associated with the button, enabling accept processing to reference the name of the button when a user clicks it. In the f?p syntax, REQUEST may be set using the fourth argument.

REQUEST is typically referenced during Accept processing (that is, the processing that occurs when you post a page).

Table 3-36 REQUEST Syntax

Reference Type	Syntax
Bind variable

:REQUEST

Direct PL/SQL

APEX_APPLICATION.G_REQUEST

PL/SQL

V('REQUEST')

Substitution string

&REQUEST.

See Also:

"Using REQUEST"

Parent topic: Using Built-in Substitution Strings

<a id="39"></a>
### 39 Using REQUEST
REQUEST is typically referenced during Accept processing (that is, the processing that occurs when you post a page). This section describes additional information about how to use the REQUEST substitution string.

About Scope and Value of REQUEST for Posted Pages
About the When Button Pressed Attribute
About Referencing REQUEST Using Declarative Conditions
About Using REQUEST for Show Processing
About Using BRANCH_TO_PAGE_ACCEPT
See Also:

"REQUEST"

Parent topic: Using Built-in Substitution Strings

#### 39.1 About Scope and Value of REQUEST for Posted Pages
When you post a page, you initiate Accept processing. Accept processing consists of computations, validations, processes, and branches. The value of REQUEST is available during each phase of the Accept processing. Once an application branches to a different page then REQUEST is set to NULL.

The value of REQUEST is the name of the button the user clicks, or the name of the tab the user selects. For example, suppose you have a button with a name of CHANGE, and a label Apply Change. When a user clicks the button, the value of REQUEST is CHANGE.

Parent topic: Using REQUEST

#### 39.2 About the When Button Pressed Attribute
Validations, processes, and branches have a When Button Pressed attribute. This attribute displays as a select list and contains the names of buttons that exist on the current page. If you make a selection from When Button Pressed, you associate the button's REQUEST value with the validation, process, or branch.

When you use a button to submit a page, the REQUEST value is passed to the page. The Accept processing logic evaluates each validation, process, and branch that uses a When Button Pressed attribute to determine whether the component should run (or fire). When one of these components runs, do not assume that a user actually clicked the associated button and caused the page to be submitted. Keep in mind, that another button using the same request value may have submitted the page. Similarly, JavaScript on the page can also submit the page and pass in a request value.

Parent topic: Using REQUEST

#### 39.3 About Referencing REQUEST Using Declarative Conditions
Many developers reference REQUEST using conditions. For example, you may want to reset pagination when a user clicks Go on a report page. You can reset pagination by creating an on-submit page process. The page process can be made conditional using the condition Request = Expression 1.

To conditionalize an on-submit page process:

Under Condition, select the condition type Request = Expression 1.

In Expression 1, enter GO.

Parent topic: Using REQUEST

#### 39.4 About Using REQUEST for Show Processing
You can also use REQUEST for Show processing when navigating to a page using f?p syntax. For example:

Copyf?p=100:1:&APP_SESSION.:GO
Remember that the fourth argument in the f?p syntax is REQUEST. This example goes to application 100, page 1 for the current session, and sets the value of REQUEST to GO. Any process or region can reference the value of REQUEST using Show processing.

The following is a similar example using PL/SQL:

CopyIF V ('REQUEST') = 'GO' THEN
   htp.p('hello');
END IF;
Note that htp.p('hello') is a call to a PL/SQL Web Toolkit package to print the specified text string.

See Also:

Oracle Database Development Guide

Parent topic: Using REQUEST

#### 39.5 About Using BRANCH_TO_PAGE_ACCEPT
You can use a special request BRANCH_TO_PAGE_ACCEPT for Show processing to automatically submit the page. For example:

Copyf?p=100:1:&APP_SESSION.:BRANCH_TO_PAGE_ACCEPT|SAVE:::P1_DATA:value
Using BRANCH_TO_PAGE_ACCEPT is the same as navigating to page 1, entering a value into the item P1_DATA, and clicking a button that submits the page with a SAVE request.

Parent topic: Using REQUEST

<a id="40"></a>
### 40 SCHEMA OWNER
If you are generating calls to applications from within your PL/SQL code, you must reference the owner of the Oracle Application Express schema. The following describes the correct syntax for a direct PL/SQL reference:

CopyAPEX_APPLICATION.G_FLOW_SCHEMA_OWNER
You may also use #FLOW_OWNER# to reference this value in SQL queries and PL/SQL (for example, in a region or a process).

Parent topic: Using Built-in Substitution Strings

<a id="41"></a>
### 41 SQLERRM
SQLERRM is a template substitution only available in the Applications Region Error Message. Supported syntax for a region template substitution reference:

Copy#SQLERRM#
Parent topic: Using Built-in Substitution Strings

<a id="42"></a>
### 42 SYSDATE_YYYYMMDD
SYSDATE_YYYYMMDD represents the current date on the database server, with the YYYYMMDD format mask applied. You may use this value instead of repeated calls to the SYSDATE() function. The following list describes the supported syntax for referencing SYSDATE_YYYYMMDD.

Bind variable

Copy:SYSDATE_YYYYMMDD
PL/SQL

CopyV('SYSDATE_YYYYMMDD')
Direct PL/SQL

CopyAPEX_APPLICATION.G_SYSDATE (DATE DATATYPE)
Table 3-37 SYSDATE_YYYYMMDD Syntax

Reference Type	Syntax
Bind variable

:SYSDATE_YYYYMMDD

Direct PL/SQL

APEX_APPLICATION.G_SYSDATE (DATE DATATYPE)

PL/SQL

V('SYSDATE_YYYYMMDD')

Parent topic: Using Built-in Substitution Strings

<a id="43"></a>
### 43 THEME_DB_IMAGES
Use the THEME_DB_IMAGES substitution string to always reference files which are stored with your theme definition in the database, regardless of the File Prefix" setting of your theme. Supported syntax for a template substitution:

Copy#THEME_DB_IMAGES#
Parent topic: Using Built-in Substitution Strings

<a id="44"></a>
### 44 THEME_IMAGES
Use the THEME_IMAGES substitution string to reference files which are stored with your theme definition. Supported syntax for a template substitution:

Copy#THEME_IMAGES#
Parent topic: Using Built-in Substitution Strings

<a id="45"></a>
### 45 WORKSPACE_IMAGES
Use this substitution string to reference uploaded images, JavaScript, and cascading style sheets that are shared over many applications within a workspace.

Table 3-38 WORKSPACE_IMAGES Syntax

Reference Type	Syntax
Bind variable

:WORKSPACE_IMAGES

Direct PL/SQL

Not available

PL/SQL

V('WORKSPACE_IMAGES')

Substitution string

&WORKSPACE_IMAGES.

Template substitution

#WORKSPACE_IMAGES#

See Also:

"APP_IMAGES" and "IMAGE_PREFIX"

Parent topic: Using Built-in Substitution Strings

<a id="46"></a>
### 46 WORKSPACE_ID
Use this substitution string to reference the workspace ID.

Table 3-39 WORKSPACE_ID Syntax

Reference Type	Syntax
Bind variable

:WORKSPACE_ID

PL/SQL

V('WORKSPACE_ID')

Substitution string

&WORKSPACE_ID.

SYS_CONTEXT variable

SELECT ... WHERE workspace_id = SYS_CONTEXT('APEX$SESSION', ''WORKSPACE_ID')

Consider the following examples:

From within an HTML region:

CopyHello your workspace id is &WORKSPACE_ID.
Using PL/SQL:

Copyhtp.p('Hello your workspace id is '||V('WORKSPACE_ID'));
Using a bind variable:

CopySELECT * FROM some_table WHERE workspace_id = :WORKSPACE_ID
Using the SYS_CONTEXT variable:

CopySELECT ... WHERE workspace_id = SYS_CONTEXT('APEX$SESSION', 'WORKSPACE_ID')
Oracle Application Express sets up the APEX$SESSION context when it starts to process an incoming request. For example, you can use the value of 'WORKSPACE_ID' to access the current workspace ID value in queries and VPD (Virtual Private Database) security policies that protect your table data.

source: [oracle-doc](https://docs.oracle.com/en/database/oracle/application-express/20.1/htmdb/understanding-substitution-strings.html#GUID-34118202-1B85-4D38-8C27-F819679504DB).
