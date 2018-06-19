---
title: 编译器 COM 支持类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fe4e7c26d1b32f16d524407279e5e71534d00c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411229"
---
# <a name="compiler-com-support-classes"></a>编译器 COM 支持类
**Microsoft 专用**  
  
 标准类用于支持某些 COM 类型。 在定义这些类\<comdef.h > 和从类型库生成的标头文件。  
  
|类|目标|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|包装 `BSTR` 类型，以提供有用的运算符和方法。|  
|[_com_error](../cpp/com-error-class.md)|定义引发的错误对象[_com_raise_error](../cpp/com-raise-error.md)在大多数失败中。|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封装 COM 接口指针，并自动执行对所需的调用`AddRef`，**版本**，和`QueryInterface`。|  
|[_variant_t](../cpp/variant-t-class.md)|包装**VARIANT**类型，以提供有用的运算符和方法。|  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 支持](../cpp/compiler-com-support.md)   
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)