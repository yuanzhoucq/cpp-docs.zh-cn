---
title: 链接器工具错误 LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: 47c20f24a2fe26cc96d5efcf359652a40af508ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811532"
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