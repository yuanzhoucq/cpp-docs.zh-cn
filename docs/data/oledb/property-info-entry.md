---
title: PROPERTY_INFO_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROPERTY_INFO_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d660a969937e3e75784516e3b50fbfe2690f9d3c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
表示属性集中的特定属性。  
  
## <a name="syntax"></a>语法  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropID*  
 [in] 一个 [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，该值可与属性集 GUID 一起使用以标识属性。  
  
## <a name="remarks"></a>备注  
 此宏将 `DWORD` 类型的属性值设置为 ATLDB.H 中定义的默认值。 若要将属性设置为所选的值，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。 若要同时为属性设置 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) 和 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) ，请使用 [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)