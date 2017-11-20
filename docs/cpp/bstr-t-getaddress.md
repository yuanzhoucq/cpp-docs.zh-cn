---
title: "_bstr_t::GetAddress |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::GetAddress
dev_langs: C++
helpviewer_keywords: GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5921b3091532c63e3ba92d6e6e74f29a85123ac1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft 专用**  
  
 释放所有现有字符串并返回一个新分配的字符串的地址。  
  
## <a name="syntax"></a>语法  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>返回值  
 指向由 `BSTR` 包装的 `_bstr_t` 的指针。  
  
## <a name="remarks"></a>备注  
 `GetAddress` 影响所有共享 `_bstr_t` 的 `BSTR` 对象。 多个 `_bstr_t` 可以通过使用复制构造函数和 `BSTR` 共享 `operator=`。  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)示例使用`GetAddress`。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)