---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

The latest version of this topic can be found at [IDiaPropertyStorage::ReadMultiple](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-readmultiple).  
  
Reads specified properties from the current property set.  
  
## Syntax  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Parameters  
 `cpspec`  
 [in] Count of properties specified in the `rgpspec` array. If zero, the method returns no properties but does return `S_OK` as a success code.  
  
 `rgpspec`  
 [in] An array of properties to be read. Properties can be specified either by a property ID or by an optional string name. It is not necessary to specify properties in any particular order in the array. The array can contain duplicate properties, resulting in duplicate property values on return for simple properties. Non-simple properties should return access denied on an attempt to open them a second time. The array can contain a mixture of property IDs and string IDs. This array must have at least `cpspec` number of property values.  
  
 `rgvar`  
 [in, out] An array of `PROPVARIANT` structures (in the Microsoft.VisualStudio.OLE.Interop namespace) to be filled in with values for each property. The array must be at least `cpspec` elements in size. The caller does not need to initialize the values in the array.  
  
## Return Value  
 If successful, returns `S_OK`. Returns `S_FALSE` if one or more of the properties was not found. Otherwise returns an error code.  
  
## Remarks  
 If a property was not found, the corresponding entry in the `rgvar` array contains a `VARIANT` with the type of `VT_EMPTY`.  
  
## See Also  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



