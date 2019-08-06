---
title: 带有一个自变量（int 或 long）的输出流操控器
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452999"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>带有一个自变量（int 或 long）的输出流操控器

iostream 类库提供用于创建参数化操控器的一组宏。 使用单个**int**或**long**参数的操控器是一种特殊情况。 若要创建接受单个**int**或**long**参数 (如`setw`) 的输出流操控器, 必须使用 iomanip > 中\<定义的 _Smanip 宏。 此示例定义了向流中插入指定数量的空格的 `fillblank` 操控器：

## <a name="example"></a>示例

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>请参阅

[带自变量的自定义操控器](../standard-library/custom-manipulators-with-arguments.md)
