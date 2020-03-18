---
title: 使用 VERIFY 代替 ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: bfc0847677ae232fef67ab6200c626472f042bdb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438620"
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 代替 ASSERT

假设在运行 MFC 应用程序的调试版本时，没有任何问题。 但是，同一应用程序的发布版本崩溃，返回不正确的结果，并/或表现出其他一些异常行为。

当你将重要代码放在 ASSERT 语句中以验证它是否正确执行时，可能会导致此问题。 由于断言语句在 MFC 程序的发布版本中被注释掉，因此代码不会在发布版本中运行。

如果使用 ASSERT 确认函数调用成功，请考虑改用[VERIFY](../mfc/reference/diagnostic-services.md#verify) 。 VERIFY 宏在应用程序的调试版本和发布版本中计算自己的参数。

另一种首选方法是将函数的返回值分配给临时变量，然后在 ASSERT 语句中测试变量。

检查以下代码片段：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

此代码可在 MFC 应用程序的调试版本中顺利运行。 如果对 `calloc( )` 的调用失败，则会显示包含文件和行号的诊断消息。 但在 MFC 应用程序的零售版本中：

- 调用 `calloc( )` 永远不会发生，`buf` 未初始化，或

- `strcpy_s( )` 将 "`Hello, World`" 复制到随机内存块中，这可能导致应用程序崩溃或导致系统停止响应，或

- `free()` 尝试释放从未分配的内存。

若要正确使用 ASSERT，应将代码示例更改为以下内容：

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

或者，您可以改用 VERIFY：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>另请参阅

[修复发行版本问题](fixing-release-build-problems.md)
