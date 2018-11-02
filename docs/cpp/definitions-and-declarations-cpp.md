---
title: 定义和声明 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628938"
---
# <a name="definitions-and-declarations-c"></a>定义和声明 (C++)

**Microsoft 专用**

DLL 接口引用已知由此系统; 中的某个程序导出的所有项 （函数和数据）也就是说，声明为的所有项**dllimport**或**dllexport**。 DLL 接口中包含的所有声明必须都指定**dllimport**或**dllexport**属性。 但是，定义必须仅指定**dllexport**属性。 例如，以下函数定义产生了一个编译器错误：

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

利用**dllexport**表示定义，而**dllimport**表示声明。 必须使用**extern**关键字**dllexport**来强制进行声明; 否则，为隐式定义。 因此，以下示例是正确的：

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