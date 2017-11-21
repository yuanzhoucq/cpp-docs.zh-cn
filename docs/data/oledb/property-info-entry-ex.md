---
title: "PROPERTY_INFO_ENTRY_EX |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY_EX
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY_EX macro
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 61842dc963ae442d23f802c1fd64c037f4a882e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentryex"></a>PROPERTY_INFO_ENTRY_EX
表示属性集中的特定属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
PROPERTY_INFO_ENTRY_EX(  
dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropID*  
 [in] 一个 [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，该值可与属性集 GUID 一起使用以标识属性。  
  
 *vt*  
 [in] 此属性项的 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) 。  
  
 `dwFlags`  
 [in] 一个描述此属性项的 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) 值。  
  
 *值*  
 [in] `DWORD`类型的属性值。  
  
 `options`  
 **DBPROPOPTIONS_REQUIRED** 或 **DBPROPOPTIONS_SETIFCHEAP**。 通常情况下，提供程序不需要设置 `options` ，因为这是由用户设置。  
  
## <a name="remarks"></a>备注  
 使用此宏，你可以直接指定 `DWORD` 类型的属性值以及选项和标记。 若要仅将属性设置为 ATLDB.H 中指定的默认值，请使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要将属性设置为你选择的值且不要设置其上的选项或标记，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。  
  
## <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)