---
title: 资源编译器错误 RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: d4a06f88e4a73da6b711d108a1f79c14fae0907c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191634"
---
# <a name="resource-compiler-error-rc2104"></a>资源编译器错误 RC2104

未定义的关键字或键名： key

未定义指定的关键字或密钥名称。

此错误通常是由资源定义或附带的头文件中的拼写错误造成的。 也可能由头文件缺失造成。

若要解决此问题，请找到应包含已定义关键字或密钥名称的头文件，并验证其是否已包含在资源文件中以及关键字或密钥名称是否拼写正确。 如果你的项目是用预编译头创建的且随后将其删除，请确保该资源文件仍包含所有所需标头。

若要验证资源文件中的已定义关键字和密钥名称，请在 Visual Studio 中打开 "**资源视图**" 窗口-在菜单栏上，依次选择 "**查看**"、"**资源视图**"，然后打开 .rc 文件的快捷菜单，然后选择 "**资源符号**" 以查看定义的符号列表。 若要修改包含的标头，请打开 .rc 文件的快捷菜单，然后选择 "**资源包括**"。

如果遇到以下消息：

```
undefined keyword or key name: MFT_STRING
```

打开 \MCL\MFC\Include\AfxRes.h 并添加此 Include 指令：

```
#include <winresrc.h>
```
