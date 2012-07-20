C2FO-SAP-Plugin
===============

Source code and documentation to connect your SAP ERP system to the C²FO working capital platform.

# 1.  INSTALLING C2FO PLUGIN FOR SAP

## 1.1.  Copy the C2FO Plugin for SAP Transport Files

The files and folders required to install C2FO Plugin for SAP on your SAP system are located in the `\C2FO_BaseCode_V2.0\Transports` distribution directory. These files should be copied to a working directory on your SAP server. Please note the following when performing the copy:

* For UNIX servers, you must log on as the root user ID to copy the files.  The directory to which the files are copied must have read, write and execute permissions.
* For Windows servers, you must log on as `<SID>ADM`.  The directory to which you copy the files must be writeable.
* If you copy the files to your SAP server using FTP, be sure to transfer them in binary mode.

## 1.2.  Load the Transport files into SAP

Copy the command files and data files as below:

* Copy the command files to `<DIR_TRANS>/cofiles`. If you are accessing the application server directly, copy the files to `/usr/sap/trans/cofiles`. Make sure the copied files are in upper case.
* Copy the data files to `<DIR_TRANS>/data`. If you are accessing the application server directly, copy the files to `/usr/sap/trans/data`. Make sure the copied files are in upper case.

`<DIR_TRANS>` can be determined by running the program `RSWATCH0` from SAP transaction `SE38`.

## 1.3.  Import the Transport files into SAP

Use the SAP R/3 transaction STMS to import the appropriate transport. Add the specified files to the import queue and import them in the same sequence as below:

* Add `EP4K900413` to the import queue and import it. `EP4K900413` is the prerequisite for importing the other three transport requests.
* Add `EP4K900417` to the import queue and import it. `EP4K900417` carries authorization objects. 
* Add `EP4K900881` to the import queue and import it. `EP4K900881` carries the complete source code of C2FO Plugin programs.
* Add `EP4K900845` to the import queue and import it. `EP4K900845` carries the authorization roles and profiles to be assigned for users accessing C2FO Plugin programs.
* Add `EP4K901860` to the import queue and import it. `EP4K901860` carries the updates made to the base code for both outbound and inbound C2FO Plugins.

Review the transport log for the transport files that were imported. Review this log before continuing, to make sure no errors occurred. A Return Code of 0 indicates success, 4 warning while a Return Code of 8 or higher indicates an error.

## 1.4 Further Reading (in MS Word format)

* [Installation guide](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Help/C2FO_SAPPlugin_InstallationGuide_V2.0.docx)
* [Configuration guide](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Help/C2FO_SAPPlugin_ConfigurationGuide_V2.0.docx)
* [Functional specification, Inbound](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Specifications/FuncSpec_Interface_Inbound_V02.docx) 
* [Functional specification, Outbound](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Specifications/FuncSpec_Interface_Outbound_V02.docx) 
* [Technical specification, Inbound](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Specifications/TechSpec_Interface_Inbound_V02.docx) 
* [Technical specification, Outbound](https://github.com/Pollenware/C2FO-SAP-Plugin/blob/master/Specifications/TechSpec_Interface_Outbound_V02.docx)
* [SAP vendor extraction demonstration on YouTube](http://www.youtube.com/watch?v=fEM7_nYKcEg)
