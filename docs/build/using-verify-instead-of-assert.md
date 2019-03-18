---
title: 使用 VERIFY 代替 ASSERT
ms.date: 11/04/2016
f1_keywords:
- assert
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: e6903616f8b4250b3d67db333be4fc17e8328952
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824457"
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 代替 ASSERT

假设当您运行 MFC 应用程序的调试版本，没有任何问题。 但是，同一应用程序的发行版本崩溃、 返回不正确的结果，和/或表现出某些其他异常行为。

如果将重要的代码放在一个断言语句以验证正确执行，则会导致此问题。 ASSERT 语句在发布版本的 MFC 程序中注释掉，因为该代码不运行在发布版本中。

如果使用断言来确认函数调用已成功，请考虑使用[验证](../mfc/reference/diagnostic-services.md#verify)相反。 VERIFY 宏计算结果自己的自变量在这两个调试和发布版本的应用程序。

另一种首选方法是将函数的返回值分配给临时变量，然后在 ASSERT 语句中测试该变量。

检查下面的代码段：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

此代码在 MFC 应用程序的调试版本中完全运行。 如果在调用`calloc( )`失败，将显示一条诊断消息包含的文件和行号。 但是，在零售版本的 MFC 应用程序：

- 在调用`calloc( )`永远不会发生，从而使`buf`未初始化，或

- `strcpy_s( )` 副本"`Hello, World`"到内存、 可能损坏应用程序或导致系统停止响应，一个随机的或

- `free()` 尝试释放永远不会分配的内存。

若要正确使用断言，应与以下更改的代码示例：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

或者，可以改为使用验证：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>请参阅

[修复发行版本问题](fixing-release-build-problems.md)
