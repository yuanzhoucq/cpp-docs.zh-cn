---
title: 标记粘贴运算符 （#） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '##'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dee802a09fd3ade03ac18cac8556d8073b19eb94
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538584"
---
# <a name="token-pasting-operator-"></a>标记粘贴运算符 (##)
双数字符号或"token-pasting"运算符 (**##**)，有时称为"合并"运算符，可在类似于对象的和类似函数的宏。 它允许将不同的标记加入到单个标记中，因此不能是宏定义中的第一个或最后一个标记。  
  
如果宏定义中的形式参数的前面或后面带有 token-pasting 运算符，则会立即将形式参数替换为未展开的实际自变量。 在替换前将不会对自变量执行宏扩展。  
  
然后，每个匹配项中的标记粘贴运算符*令牌字符串*被删除，以及令牌之前和之后它被连接在一起。 生成的标记必须是有效的标记。 如果标记有效，则在它表示宏名称时扫描其中可能的替换。 标识符表示连接在一起的标记在替换前在程序中已知的名称。 每个标记表示在别处（在程序中或在编译器命令行上）定义的标记。 运算符前后的空白是可选的。  
  
此示例演示了在指定程序输出时对 stringizing 和 token-pasting 运算符的使用：  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
如果使用类似如下的数值自变量调用一个宏  
  
```  
paster( 9 );  
```  
  
宏将生成  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
它将变为  
  
```  
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