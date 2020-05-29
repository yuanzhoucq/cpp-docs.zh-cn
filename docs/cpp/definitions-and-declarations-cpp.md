---
title: 定义和声明 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 20683f3d2e12f7ffead573cbac46fdd4e106c383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189372"
---
# <a name="definitions-and-declarations-c"></a>定义和声明 (C++)

**Microsoft 专用**

DLL 接口引用已知由系统中的某个程序导出的所有项（函数和数据）;也就是说，声明为**dllimport**或**dllexport**的所有项。 DLL 接口中包含的所有声明必须指定**dllimport**或**dllexport**特性。 但是，定义必须仅指定**dllexport**特性。 例如，以下函数定义产生了一个编译器错误：

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

使用**dllexport**隐含定义，而**dllimport**表示声明。 必须将**extern**关键字与**dllexport**结合使用才能强制声明;否则，定义是隐含的。 因此，以下示例是正确的：

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

## <a name="see-also"></a>另请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
