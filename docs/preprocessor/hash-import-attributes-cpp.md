---
title: "#import 特性 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#import 指令, 特性"
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #import 特性 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供指向用于 \#import 指令的特性的链接。  
  
 **Microsoft 专用**  
  
 以下特性可供 \#import 指令使用。  
  
|特性|说明|  
|--------|--------|  
|[auto\_rename](../preprocessor/auto-rename.md)|通过将两个下划线 \(\_\_\) 追加到变量名称来重命名 C\+\+ 保留字，从而解决可能的名称冲突。|  
|[auto\_search](../preprocessor/auto-search.md)|指定当使用 \#import 引用了类型库，并且它本身引用了另一个类型库时，编译器可以为其他类型库执行隐式 \#import。|  
|[embedded\_idl](../preprocessor/embedded-idl.md)|指定将类型库写入保留了特性生成的代码的 .tlh 文件。|  
|[exclude](../preprocessor/exclude-hash-import.md)|从要生成的类型库标头文件中排除项。|  
|[high\_method\_prefix](../preprocessor/high-method-prefix.md)|指定用于命名高级属性和方法的前缀。|  
|[high\_property\_prefixes](../preprocessor/high-property-prefixes.md)|指定用于三个属性方法的备用前缀。|  
|[implementation\_only](../preprocessor/implementation-only.md)|取消生成 .tlh 头文件（主要头文件）。|  
|[include\(\)](../preprocessor/include-parens.md)|禁用自动排除。|  
|[inject\_statement](../preprocessor/inject-statement.md)|将其参数作为源文本插入类型库标头。|  
|[named\_guids](../preprocessor/named-guids.md)|告知编译器定义和初始化旧样式或 **LIBID\_MyLib**、**CLSID\_MyCoClass**、**IID\_MyInterface** 和 **DIID\_MyDispInterface** 形式的 GUID 变量。|  
|[no\_auto\_exclude](../preprocessor/no-auto-exclude.md)|禁用自动排除。|  
|[no\_dual\_interfaces](../preprocessor/no-dual-interfaces.md)|更改编译器为双重接口方法生成包装器函数的方式。|  
|[no\_implementation](../preprocessor/no-implementation.md)|取消生成 .tli 标头，它包含包装器成员函数的实现。|  
|[no\_namespace](../preprocessor/no-namespace.md)|指定命名空间的名称不由编译器生成。|  
|[no\_registry](../preprocessor/no-registry.md)|告知编译器不在注册表中搜索类型库。|  
|[no\_search\_namespace](../preprocessor/no-search-namespace.md)|与 [no\_namespace](../preprocessor/no-namespace.md) 特性的功能相同，但在类型库中使用时，可以将 \#import 指令与 [auto\_search](../preprocessor/auto-search.md) 特性结合使用。|  
|[no\_smart\_pointers](../preprocessor/no-smart-pointers.md)|取消对类型库中所有接口的智能指针的创建。|  
|[raw\_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|告知编译器生成低级别的调度接口方法的包装器函数和调用 **IDispatch::Invoke** 并返回 `HRESULT` 错误代码的属性。|  
|[raw\_interfaces\_only](../preprocessor/raw-interfaces-only.md)|取消错误处理的包装器函数的生成以及使用那些包装器函数的 [属性](../cpp/property-cpp.md) 声明。|  
|[raw\_method\_prefix](../preprocessor/raw-method-prefix.md)|指定不同的前缀以避免名称冲突。|  
|[raw\_native\_types](../preprocessor/raw-native-types.md)|禁止在高级包装器函数中使用 COM 支持类，并强制改用低级数据类型。|  
|[raw\_property\_prefixes](../preprocessor/raw-property-prefixes.md)|指定用于三个属性方法的备用前缀。|  
|[重命名](../preprocessor/rename-hash-import.md)|解决名称冲突问题。|  
|[rename\_namespace](../preprocessor/rename-namespace.md)|重命名包含类型库内容的命名空间。|  
|[rename\_search\_namespace](../preprocessor/rename-search-namespace.md)|与 [rename\_namespace](../preprocessor/rename-namespace.md) 特性的功能相同，但在类型库中使用时，可以将 \#import 指令与 [auto\_search](../preprocessor/auto-search.md) 特性结合使用。|  
|[tlbid](../preprocessor/tlbid.md)|允许加载主类型库之外的库。|  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)