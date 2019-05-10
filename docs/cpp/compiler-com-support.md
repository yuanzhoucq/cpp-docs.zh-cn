---
title: 编译器 COM 支持
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: e13874bad44610821bed9c588af6bd9124162116
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222209"
---
# <a name="compiler-com-support"></a>编译器 COM 支持

## <a name="microsoft-specific"></a>Microsoft 专用

MicrosoftC++编译器可以直接读取组件对象模型 (COM) 类型库并转换到的内容C++可以包含在编译的源代码。 提供了语言扩展来帮助在客户端上进行 COM 编程。

通过使用[#import 预处理器指令](../preprocessor/hash-import-directive-cpp.md)，编译器可以读取类型库和转换到 C++ 标头文件，用于描述 COM 接口标记为类。 提供了一组 `#import` 特性来实现对生成的类型库头文件的内容的用户控制。

可以使用[__declspec](../cpp/declspec.md)扩展的特性[uuid](../cpp/uuid-cpp.md)要分配给 COM 对象的全局唯一标识符 (GUID)。 关键字[__uuidof](../cpp/uuidof-operator.md)可用于提取与 COM 对象关联的 GUID。 另一个 **__declspec**属性中，[属性](../cpp/property-cpp.md)，可用于指定`get`和`set`COM 对象的数据成员的方法。

提供了一组 COM 支持全局函数和类以支持`VARIANT`并`BSTR`类型，实现智能指针和封装引发的错误对象`_com_raise_error`:

- [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)<br/>
[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)