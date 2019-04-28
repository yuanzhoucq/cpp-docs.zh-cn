---
title: 构造输入流对象
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: 89d681f1a092957bc966d2ec788a0f9aa2261ada
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211983"
---
# <a name="constructing-input-stream-objects"></a>构造输入流对象

如果只使用 `cin` 对象，则无需构造输入流。 如果使用以下对象，则必须构造输入流：

- [输入文件流构造函数](#vclrfinputfilestreamconstructorsanchor8)

- [输入字符串流构造函数](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a>输入文件流构造函数

有两种创建输入文件流的方法：

- 使用**void**参数的构造函数，然后调用`open`成员函数：

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- 在构造函数调用期间指定文件名和模式标志，从而在构造过程中打开文件：

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a>输入字符串流构造函数

输入字符串流构造函数需要预分配、预初始化存储的地址：

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>请参阅

[输入流](../standard-library/input-streams.md)<br/>
