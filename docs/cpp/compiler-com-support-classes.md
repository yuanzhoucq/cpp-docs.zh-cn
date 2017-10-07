---
title: "编译器 COM 支持类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 48540910db97e7662eeaa7e8a7febf7e44df653b
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="compiler-com-support-classes"></a>编译器 COM 支持类
**Microsoft 专用**  
  
 标准类用于支持某些 COM 类型。 这些类是在从类型库生成的 comdef.h 文件和头文件中定义的。  
  
|类|用途|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|包装 `BSTR` 类型，以提供有用的运算符和方法。|  
|[_com_error](../cpp/com-error-class.md)|定义引发的错误对象[_com_raise_error](../cpp/com-raise-error.md)在大多数失败中。|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封装 COM 接口指针，并自动执行对所需的调用`AddRef`，**版本**，和`QueryInterface`。|  
|[_variant_t](../cpp/variant-t-class.md)|包装**VARIANT**类型，以提供有用的运算符和方法。|  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器 COM 支持](../cpp/compiler-com-support.md)   
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)
