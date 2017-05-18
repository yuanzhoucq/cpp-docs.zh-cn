---
title: "类型库访问 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries, accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8a3fbcf66036ef3df3bd34b5182dac8af3dfccef
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="type-library-access"></a>类型库访问
类型库向其他 OLE 感知的应用程序公开 OLE 控件的接口。 如果将公开一个或多个接口，则每个 OLE 控件都必须具有类型库。  
  
 下列宏允许 OLE 控件提供对其自己的类型库的访问：  
  
### <a name="type-library-access"></a>类型库访问  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB](#declare_oletypelib)|声明 OLE 控件（必须用于类声明中）的 `GetTypeLib` 成员函数。|  
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|实现 OLE 控件（必须用于类实现中）的 `GetTypeLib` 成员函数。|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB  
 声明`GetTypeLib`控件类的成员函数。  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 与类型库相关的控件类的名称。  
  
### <a name="remarks"></a>备注  
 在控件类头文件中使用此宏。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB  
 实现控件的`GetTypeLib`成员函数。  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 与类型库相关的控件类的名称。  
  
 *tlid*  
 类型库 ID 号。  
  
 `wVerMajor`  
 类型库主版本号。  
  
 `wVerMinor`  
 类型库次版本号。  
  
### <a name="remarks"></a>备注  
 此宏必须出现在使用任何控件类的实现文件`DECLARE_OLETYPELIB`宏。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
   
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

