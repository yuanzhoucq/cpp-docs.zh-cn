---
title: 定义和声明 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 742270c77d47c178d0254ca9b9882f73fe3b8293
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="definitions-and-declarations-c"></a>定义和声明 (C++)
## <a name="microsoft-specific"></a>Microsoft 专用
 DLL 接口引用已知由此系统; 中的某个程序导出的所有项 （函数和数据）即，声明为的所有项`dllimport`或`dllexport`。 DLL 接口中包含的所有声明必须都指定`dllimport`或`dllexport`属性。 但是，该定义仅必须指定 `dllexport` 特性。 例如，以下函数定义产生了一个编译器错误：

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;  
}
```

 以下代码也会产生错误：

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

 但是，这是正确的语法：

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

 使用`dllexport`表示定义，尽管`dllimport`表示声明。 必须使用带 `extern` 的 `dllexport` 关键字来强制进行声明；否则，会进行隐式定义。 因此，以下示例是正确的：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

 以下示例阐明了前面的示例：

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)
