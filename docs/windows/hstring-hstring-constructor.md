---
title: "Hstring:: Hstring 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs: C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d13f532484cc071744b9b823546052d92c6f6b78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hstringhstring-constructor"></a>HString::HString 构造函数
初始化 HString 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `hstr`  
 HSTRING 句柄。  
  
 `other`  
 现有 HString 对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数初始化为空的新 HString 对象。  
  
 第二个构造函数初始化的现有值将新 HString 对象`other`参数，然后销毁`other`参数。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)