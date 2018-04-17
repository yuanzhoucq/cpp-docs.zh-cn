---
title: 编译器 COM 支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05fdff690f8693e926011c3bc7d1738ee9be66c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-com-support"></a>编译器 COM 支持
## <a name="microsoft-specific"></a>Microsoft 专用  
 Visual C++ 编译器可以直接读取组件对象模型 (COM) 类型库并将内容转换为可包含在编译中的 C++ 源代码。 提供了语言扩展来帮助在客户端上进行 COM 编程。  
  
 通过使用[#import 预处理器指令](../preprocessor/hash-import-directive-cpp.md)，编译器可以读取类型库和转换到 C++ 标头文件，用于描述 COM 接口标记为类。 提供了一组 `#import` 特性来实现对生成的类型库头文件的内容的用户控制。  
  
 你可以使用[__declspec](../cpp/declspec.md)扩展的特性[uuid](../cpp/uuid-cpp.md)要分配给 COM 对象的全局唯一标识符 (GUID)。 关键字[__uuidof](../cpp/uuidof-operator.md)可用于提取与 COM 对象关联的 GUID。 另一个`__declspec`属性，[属性](../cpp/property-cpp.md)，可以用于指定**获取**和**设置**COM 对象的数据成员的方法。  
  
 提供一组 COM 支持全局函数和类是为了支持**VARIANT**和`BSTR`类型实现智能指针和封装引发的错误对象`_com_raise_error`:  
  
-   [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)   
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)