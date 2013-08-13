Android Coding Convention - SSS Android Team {#welcome}
=============

This is the coding convention for SSS Android Team. The IDE is ADT (based on Eclipse). [Download and setup ADT.][1]

-------------
###Table of content
[TOC]

-------------

###I. Project structure

####1. Project name and root directory
Assume the project is <b>"Drive SG"</b>, create the root folder of project which name is lower-case and connected by hyphens. After that, switch workspace to the root folder and create project in ADT. <b>We must check out or init git here.</b>

**Do**

```
drive-sg
```

**Don't**

```
Drive SG or whatever
```

####2. Project package (i.e bundle in iOS)
Follow the standard package naming. Assume the customer's URL is <b>"www.drive.sg"</b>, then package name is <b>"sg.drive.app"</b>. Never use our company URL as the package name.

**Do**

```
sg.drive.app
```

**Don't**

```
com.sss.drive.sg.app or whatever
```

####3. Directory structure
Assume <b>drive-sg</b> is the root of the project, inside <b>drive-sg</b>, there are at least 2 folders: <b>App</b> and <b>Libs</b>. <b>App</b> contains the main project (i.e src, asset, res, ...). <b>Libs</b> contains third-party libraries (both jar and project folders).


----------

###II. Naming

####1. Naming packages
Following are partial package names corresponding to the classes they contain. 
> - **app** activities, static class, static model class, shared preference manipulator, common classes (listeners).
> - **adapter** customized adapters for listview, spinner and gridview.
> - **db** database handling classes
> - **fragment** fragments and dialog fragments.
> - **model** model classes (POJOs)
> - **network** network engine and URLs
> - **view** customized views
> - **util** helper classes (DateTimeUtil, DensityUtil, FontUtil, ...)

####2. Naming classes
Using camelCase. Class name must end with it's type <b>except model classes</b>. This will increase recognition of classes.

**Examples**

```
//activity
MainActivity.java 

//adapter
HomeListViewAdapter.java

//view
MoonView.java

//handler
NetworkHandler.java

//util
DateTimeUtil.java

//listener
OnNetworkResultListener.java

//model
Car.java
```

####3. Naming methods
All methods must be camelCase and start with a lower-case character.

**Examples**

```
protected void openDatabase()
protected void onNetworkResult()
protected void callback()
```

Methods inside a <b>callback</b> listener interface must begin with <b>on</b> or a verb.

**Examples**

```
public void onResult();
public void switchToFragment(Fragment fragment);
public void showSummaryDialog();
```

Avoid including any unnecessary string in method name.

**Examples**

```
//in network handler class, instead of this
void callApiGetCars();
void callApiGetPromotions();

//using this
void getCars();
void getPromotions();
```



####4. Naming variables
All variables must be camelCase. All variables must start with a lower-case character.

**Examples**

```
//private and protected
int level;
protected boolean isChecked;
protected static int count;

//public
public Profile profile
```

Variable which represents view: if there is only one view of the class in the layout, name it as the class name. Otherwise, name it with the class of view following by the field name.                                                     

**Examples**

```
//if there's only one view of that type
ImageView imageView;

//else specify them clearly
ImageView imageViewCar;
ImageView imageViewAvatar;
```

####5. Naming constants and enums
All constants must all be upper-case connected by hyphens.

**Example**

```
public static final String API_URL = "https://beta.siliconstraits.vn/api"
```

Enum name must be camelCase. All item in an enum must be upper-case connected by hyphens.

**Example**

```
//normal enum
public enum AppNetworkResult {
	OK, NETWORK_ERROR, TRANSFORM_ERROR, NOT_EXISTS
}

//enum with String value
public enum AppFragment {
	HOME("Home"), CAR("Car"), RENT_STEP_01("Rent_01") 
}
```

####6. Naming assets and resources
Fonts and raw resources (.ttf, .otf, .db, ...) must be kept in <b>asset</b> folder. Depend on the context, some raw resources can be stored in <b>raw</b> folder for better access.

Files in <b>res</b> folder must be named by lower-case string connected by hyphens. 
> - **anim**: file name starts with **anim**. Example: ```anim_fade_out.xml```
> - **drawable**: selector starts with **selector**: ```selector_button_home.xml```; shape starts with **shape**: ```selector_button_shape.xml```.
> - **layout**: file name starts with the class inflating it: ```activity_main.xml```; ```fragment_home.xml```; ```listview_more_item.xml```. **Id of views** in layout must be named by lower-case string connected by hyphens.

--------
***SSS Android Team 2013***


[1]:http://developer.android.com/sdk/index.html