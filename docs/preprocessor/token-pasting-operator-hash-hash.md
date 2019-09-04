---
title: '标记粘贴运算符 (# #)'
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 4bf1b8c8f56ab9375503c9e8fb6a906706fc70bb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218102"
---
# <a name="token-pasting-operator-"></a>标记粘贴运算符 (# #)

双号符号或*标记粘贴*运算符 () ( **##** 有时称为*合并*运算符或*组合*运算符) 用于类似于对象的宏和类似于函数的宏。 它允许将单独的令牌加入单个令牌, 因此, 不能是宏定义中的第一个或最后一个令牌。

如果宏定义中的形参的前面或后面带有 token-pasting 运算符，则会立即将形参替换为未扩展的实参。 在替换前将不会对自变量执行宏扩展。

然后, 将删除标记*字符串*中出现的每个标记粘贴运算符, 并连接它前面和后面的标记。 生成的标记必须是有效的标记。 如果标记有效，则在它表示宏名称时扫描其中可能的替换。 标识符表示连接在一起的标记在替换前在程序中已知的名称。 每个标记表示在别处（在程序中或在编译器命令行上）定义的标记。 运算符前后的空白是可选的。

此示例演示了在指定程序输出时对 stringizing 和 token-pasting 运算符的使用：

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

如果使用类似如下的数值自变量调用一个宏

```cpp
paster( 9 );
```

宏将生成

```cpp
printf_s( "token" "9" " = %d", token9 );
```

它将变为

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>示例

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>请参阅

[预处理器运算符](../preprocessor/preprocessor-operators.md)
