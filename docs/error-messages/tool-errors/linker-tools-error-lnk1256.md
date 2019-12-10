---
title: 链接器工具错误 LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: bedf96262944d59737a39a942021cdec9445f3b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990944"
---
# <a name="linker-tools-error-lnk1256"></a>链接器工具错误 LNK1256

ALINK 操作失败：原因

LNK1256 的一个常见原因是程序集的版本号出错。 程序集版本号的任何部分均不允许值 65535。 程序集版本的有效范围是 0-65534。

如果 ALINK 找不到已命名的密钥容器，也可能导致 LNK1256。 删除密钥容器，并使用[sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)将其重新添加到强名称 CSP。

LNK1256 的另一个原因是链接器和 Alink.dll 之间的版本不匹配。 原因可能是安装了损坏的 Visual Studio。 使用 Windows 控制面板中的 "**程序和功能**" 修复或重新安装 Visual Studio。

以下示例生成 LNK1256：

```cpp
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```
