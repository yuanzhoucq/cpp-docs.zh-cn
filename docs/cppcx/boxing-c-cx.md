---
title: 装箱 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e47313f65c4129bbc6fbf0a7bfbf698eb092f9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086494"
---
# <a name="boxing-ccx"></a>装箱 (C++/CX)
 装箱就是当一个值类型变量（如 [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)）或基础标量类型（如 `int`）传递给以 [Platform::Object^](../cppcx/platform-object-class.md) 作为其输入类型的方法时，将该变量或类型包装在一个 ref 类中的过程。  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>将值类型传递给 Object^ 参数  
 虽然无需显式装箱变量以将该其传递给类型 [Platform::Object^](../cppcx/platform-object-class.md)的方法参数，但当你检索之前已装箱的值时，必须显式转换回原始类型。  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>使用 platform:: ibox\<T > 以支持可以为 null 的值类型  
 C# 和 Visual Basic 支持可以为 null 的值类型的概念。 在 C + + /CX 中，你可以使用`Platform::IBox<T>`类型以公开支持可以为 null 的值类型参数的公共方法。 下面的示例演示 C + + /cli CX 公共方法，它在 C# 调用方传递的自变量之一为 null 时返回 null。  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 在 C# XAML 客户端中，可按以下方式使用它：  
  
```  
  
// C# client code  
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();  
    int? a = null;  
    int? b = 5;  
    var result = obj.Multiply(a,b); //result = null  
  
```  
  
## <a name="see-also"></a>请参阅  
 [类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [强制转换 (C + + /cli CX)](../cppcx/casting-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)