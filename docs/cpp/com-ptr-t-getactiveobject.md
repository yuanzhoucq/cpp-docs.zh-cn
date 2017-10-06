---
title: "_com_ptr_t::GetActiveObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 9
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a61e41c750fdf5865a475d92ba9e1def0aefd748
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Microsoft 专用**  
  
 将附加到给定的对象的现有实例**CLSID**或**ProgID**。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `rclsid`  
 **CLSID**的对象。  
  
 `clsidString`  
 由 Unicode 字符串，包含**CLSID** (从"**{**") 或**ProgID**。  
  
 `clsidStringA`  
 使用 ANSI 代码页，包含的多字节字符串**CLSID** (从"**{**") 或**ProgID**。  
  
## <a name="remarks"></a>备注  
 这些成员函数调用 `GetActiveObject` 来检索指向已向 OLE 注册的正在运行对象的指针，然后查询此智能指针的接口类型。 生成的指针随后将封装在此 `_com_ptr_t` 对象内。 **版本**调用以减少前面封装的指针的引用计数。 此例程返回 `HRESULT` 以指示成功或失败。  
  
-   **GetActiveObject (**`rclsid`**)**将附加到给定的对象的现有实例**CLSID**。      
  
-   **GetActiveObject (**`clsidString`**)**将附加到给定的 Unicode 字符串，包含的对象的现有实例**CLSID** (从"**{**") 或**ProgID**。      
  
-   **GetActiveObject (**`clsidStringA`**)**将附加到给定的多字节字符字符串，包含的对象的现有实例**CLSID** (从"**{**") 或**ProgID**。     调用[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，这假定字符串是在 ANSI 代码页中而不是 OEM 代码页。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)
