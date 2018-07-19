---
title: "0120. Custom ArcGIS scripted tools"
layout: page
collection: sections
excerpt:  "Use Python to create custom ArcGIS scripted tools."

---

>Objectives
>
>Students will be able to:
>- Use `arcpy` to create custom scripted tools in ArcGIS Pro.

To create a custom tool:
- Create a script.
- Create a custom toolbox.
- Add the tool to the toolbox.
- Modify the script and/or the tool properties as necessary.

A script that can be included in a tool, prints the names as warnings or messages.

```python
#
import arcpy

myName = arcpy.GetParameterAsText(0)
myQuest = arcpy.GetParameterAsText(1)
myFavoriteColor = arcpy.GetParameterAsText(2)

arcpy.AddMessage("Your name is " + myName)
arcpy.AddWarning("Your quest is " + myQuest)
arcpy.AddError("Your favorite color is " + myFavoriteColor)

```

Another script that can be included in a tool to print the names of feature classes:

```python

#Describe a feature class

#import arcpy, set up environments
import arcpy
arcpy.env.workspace = arcpy.GetParameterAsText(0)

#establish a list of feature classes
fcList = arcpy.ListFeatureClasses()


#Describe the feature classes in the list
for fc in fcList:
    arcpy.AddMessage(fc)

```
