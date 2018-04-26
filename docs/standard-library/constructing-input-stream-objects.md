---
title: 构造输入流对象 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a63ba3d8e54e416313ec24d7455ca4cf70979b9f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="constructing-input-stream-objects"></a>构造输入流对象

如果只使用 `cin` 对象，则无需构造输入流。 如果使用以下对象，则必须构造输入流：

- [输入文件流构造函数](#vclrfinputfilestreamconstructorsanchor8)

- [输入字符串流构造函数](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a>输入文件流构造函数

有两种创建输入文件流的方法：

- 使用 `void` 参数构造函数，然后调用 `open` 成员函数：

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
