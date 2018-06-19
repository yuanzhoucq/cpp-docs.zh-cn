---
title: _bstr_t::GetBSTR |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2c9903170f62652357264a3ea2de0839496e9e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409093"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft 专用**  
  
 指向 `BSTR` 包装的 `_bstr_t` 的开头。  
  
## <a name="syntax"></a>语法  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>返回值  
 `BSTR` 包装的 `_bstr_t` 的开头。  
  
## <a name="remarks"></a>备注  
 `GetBSTR` 影响所有共享 `_bstr_t` 的 `BSTR` 对象。 多个 `_bstr_t` 可以通过使用复制构造函数和 `BSTR` 共享 `operator=`。  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用示例`GetBSTR`。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)