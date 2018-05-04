---
title: _com_ptr_t::Attach |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7341695ad0cbc8384da859b80a72a63d8d52215f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Microsoft 专用**  
  
 封装此智能指针的类型的原始接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `pInterface`  
 原始接口指针。  
  
 `fAddRef`  
 如果它是**true**，然后`AddRef`调用。 如果它是**false**、`_com_ptr_t`对象将获得而不调用原始接口指针的所有权`AddRef`。  
  
## <a name="remarks"></a>备注  
  
-   **附加 (**`pInterface`**)** `AddRef`不调用。     将接口的所有权传递给此 `_com_ptr_t` 对象。 **版本**调用以减少前面封装的指针的引用计数。  
  
-   **附加 (** `pInterface` **，**`fAddRef`**)** 如果`fAddRef`是**true**，`AddRef`调用以递增引用封装的接口指针的计数。       如果`fAddRef`是**false**，则此`_com_ptr_t`对象将获得而不调用原始接口指针的所有权`AddRef`。 **版本**调用以减少前面封装的指针的引用计数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)