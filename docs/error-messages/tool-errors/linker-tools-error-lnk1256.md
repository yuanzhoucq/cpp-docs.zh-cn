---
title: 链接器工具错误 LNK1256 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a711343eaf64a9ef1c46a5044cb3d6a2f84c5f7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050640"
---
# <a name="linker-tools-error-lnk1256"></a>链接器工具错误 LNK1256

ALINK 操作失败： 原因

LNK1256 的一个常见原因是程序集的版本号出错。 程序集版本号的任何部分均不允许值 65535。 程序集版本的有效范围是 0-65534。

如果 ALINK 找不到已命名的密钥容器，也可能导致 LNK1256。 删除密钥容器并使用强名称 CSP 到再次添加它[Sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)。

LNK1256 的另一个原因是链接器和 Alink.dll 之间的版本不匹配。 原因可能是安装了损坏的 Visual Studio。 使用**程序和功能**Windows 控制面板来修复或重新安装 Visual Studio 中。

以下示例生成 LNK1256：

```
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```