# universal_tool_template.py
a quick Qt GUI tool development template for both Maya or Desktop application, supports automatically for both PySide and PyQt4

**Feature**
  * version 7.3: (2016.10.13)
    * 7.3.1: minor tune for better look and notation, add 'tree, txt, space' on qui (2016.10.24)
    * add Maya UI name to Qt object 2-way conversion
  * version 7.2: (2016.09.20)
    * fix layout margin clear
    * add quickPolicy
    * add quickInfo for quick notify and feedback, user customizable
    * fix btnMsg issue
  * version 7: (2016.09.15)
    * rewrite quickUI, backward compatible, and also optimized label creation for form layout, only create label when needed
    * enable you to directly nest quickUI inside quickUI with various return type,
      * eg. self.quickUI([self.quickUI(), self.quickUI()], 'main_vbox')
    * enable you to quickUI with tab, split, groupbox as layout object, same creation string syntax as element
    * a even compact pure text based UI creation and reference function on top of quickUI, called "qui()"
  * version 6.2:
    * (to do) format utf8 text output support
    * add unicode for text read, better structure for fast template update and cleanup
  * version 6.1: (2016.08.18)
    - (v6.1.3) unicode support for template text edit
    - rewrite lang functions
    - fix qmenu creation for lang function
    - fix file icon template name
  * version 6.0: (2016.08.16)
    - self location and location for load lang
    - window icon support and window initial drag position
    - quickMsgAsk for user input
    - quickTabUI (no tab name lang out yet)
    - better fixed area and user change area separation and code cleanup
  * version 5.0: (2016.07.30)
    * add language support with json file
    * support better QGridLayout with "h" or "v" insertion
  * version 4.0: (2016.07.28)
    -  built-in automatically button and menuItem action binding
    - standalone, frameless, transparent-irregular-win-shape and always-on-top option
    - drag, move, right-click-menu window interface interaction functions
    - example of invisible but functional button
    - automatically use modern style for desktop app
  * version 3.0: (2016.07.22)
    - automatically detect whether run in Maya panel mode or Desktop mode
    - automatically detect to use PySide Qt binding or PyQt4 Qt binding
    - universal coding format, seamlessly works in all 4 combination conditions
    - built-in json file operation and format text operation
    - built-in quickUI() v3.0 features
    - built-in auto button action linking
    - now quickSplitUI() supports more than 2 layouts or widgets

**Usage**
  * usage in maya: 
```python
import universal_tool_template
universal_tool_template.main()
```
  * usage in commandline: 
```python
python universal_tool_template.py
```

  * version 7 syntax 
```python
quickUI(["elementA_btn;QPushButton;Title Here"], "config_layout;QVBoxLayout")

element_list:

ui_name@ui_label;ui_type;ui_opts
-------------------------------------
elementA_btn;QPushButton;Title Here
elementA_btn@User label;QPushButton;Title Here
elementB_choice@Choose one;QComboBox;(A,B,C,4)
partB_space;QSpacerItem;(200,10,5,4)
elementC_txtEdit@Custom label;LNTextEdit
partB_layout;vbox
partB_QVBoxLayout

main_split;QSplitter;v
main_tab;QTabWidget
elementB_grp@System label;QGroupBox;vbox,My Group Title


parentObject
parent_name;parent_type;parent_opts
-------------------------------------
config_layout;QVBoxLayout
config_vbox
config_split;QSplitter;v
config_split;v
config_grp;QGroupBox;vbox,My Group Title
main_tab
main_tab;QTabWidget

parentObject's insert_opt
-------------------------------------
gridLayout: "h", "v" for grid insertion
tab: (Tab A, Tab B, Tab C) for tab name insertion

#####################################

qui('elementA_btn;Title Here | elementB_label;Label here', 'config_vbox')

element_list:

ui_name@ui_label;ui_opts
-------------------------------------
can't use ; in ui_opts

parentObject
parent_name;parent_type;parent_opts
-------------------------------------
parentObject's insert_opt
-------------------------------------
```

**File Structure**

  * universal_tool_template.py: main GUI and core function
  * (required) if you want to use LNTextEdit in your tool.


**Screenshot**

http://shining-lucy.com/wiki/page.php?id=devwiki:template:universal_tool_template