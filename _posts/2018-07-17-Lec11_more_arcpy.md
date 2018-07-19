---
title: "0110. More arcpy"
layout: page
collection: sections
excerpt:  "Non-tool arcpy functions exist to help ease script creation."

---

>Objectives:
>
>Students will be able to:
>- Use non-tool arcpy functions in Python scripts.

## Non-tool `arcpy` functions

Here are scripts using non-tool `arcpy` functions:

```python
#list feature classes

#import arcpy, set environments
import arcpy
arcpy.env.workspace = r"C:\TEMP\Demo11.gdb"

#establish variables
featureClassList = arcpy.ListFeatureClasses()

#print the feature class list
print featureClassList

```

Describe a feature class:

```python
#Describe a feature class

#import arcpy, set up environments
import arcpy
arcpy.env.workspace = r"C:\TEMP\Demo11.gdb"

#establish which feature class

fc = "Cemeteries"

#establish describe object
fcDescription = arcpy.Describe(fc)

#print the describe properties
print fcDescription.dataType, fcDescription.shapeType
print fcDescription.shapeType
print fcDescription.spatialReference.Name

print
print fc + " contains shapes of type " + fcDescription.shapeType

```

Describe the properties of feature classes in a workspace:

```python
Describe a feature class

#import arcpy, set up environments
import arcpy
arcpy.env.workspace = r"C:\TEMP\Demo11.gdb"

#establish a list of feature classes
fcList = arcpy.ListFeatureClasses()

#Describe the feature classes in the list
for fc in fcList:
    fcDescription = arcpy.Describe(fc)
    print fc + " contains " + fcDescription.shapeType

```

More describing feature classes:

```python
#Describe a feature class

#import arcpy, set up environments
import arcpy
arcpy.env.workspace = r"C:\TEMP\Demo11.gdb"

#establish a list of feature classes
fcList = arcpy.ListFeatureClasses()

#Describe the feature classes in the list
for fc in fcList:
    print fc

```
