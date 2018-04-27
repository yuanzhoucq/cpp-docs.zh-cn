---
title: 自行编写无参数的操控器 | Microsoft Docs
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
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7661e8df55f8b7de0cac546c15369247cc6bf2c8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="writing-your-own-manipulators-without-arguments"></a>自行编写无自变量的操控器

编写不使用参数的操控器既不需要类派生，也不需要使用复杂宏。 假设你的打印机需要使用对 \<ESC>[ 才能进入粗体模式。 可直接将此对插入到流中：

```cpp
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;
```

或者，可定义 `bold` 操控器，这样可插入字符：

```cpp
ostream& bold(ostream& os) {
    return os <<'\033' <<'[';
}
cout <<"regular " <<bold <<"boldface" <<endl;
```

全局定义的 `bold` 函数将采用 `ostream` 引用参数并返回 `ostream` 引用。 因为它不需要访问任何私有类元素，所以它不是成员函数或友元。 `bold` 函数将连接到流，因为此流的 `<<` 运算符将重载以接受该函数类型，其中使用的声明如下所示：

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{     // call ios_base manipulator
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}
```

可使用此功能扩展其他重载运算符。 在这种情况下，`bold` 可能会将字符插入到流中。 函数插入到流中时，将调用此函数，而打印相邻字符时则无需调用函数。 因此，由于流的缓冲，打印可能会延迟。

## <a name="see-also"></a>请参阅

[输出流](../standard-library/output-streams.md)<br/>
