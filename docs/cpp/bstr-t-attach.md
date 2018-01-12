---
title: "_bstr_t::Attach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::Attach
dev_langs: C++
helpviewer_keywords: Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c6d60347b9b5be10923e23e839d99ddd0f1cee4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtattach"></a>_bstr_t::Attach
**Microsoft 专用**  
  
 将 `_bstr_t` 包装器链接到 `BSTR`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### <a name="parameters"></a>参数  
 *s*  
 要与之关联或分配到的 `BSTR`，即 `_bstr_t` 变量。  
  
## <a name="remarks"></a>备注  
 如果 `_bstr_t` 以前被附加到了另一个 `BSTR`，并且没有其他 `_bstr_t` 变量使用 `BSTR`，`_bstr_t` 将清理 `BSTR` 资源。  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用示例**附加**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)