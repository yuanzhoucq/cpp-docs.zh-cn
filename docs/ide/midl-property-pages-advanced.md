---
title: MIDL 属性页：高级
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 86152dd1ac0bb079a841efa2d27109ee92d48ea7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440867"
---
# <a name="midl-property-pages-advanced"></a>MIDL 属性页：高级

MIDL 文件夹中的“高级”属性页指定以下 MIDL 编译器选项：

- 启用错误检查 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 检查分配 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 检查界限 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 检查枚举范围 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 检查引用指针 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 检查存根(Stub)数据 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 验证参数 ([/robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- 结构成员对齐 ([/Zp](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- 重定向输出 ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- C 预处理选项 ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- 取消定义预处理器定义 ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* /robust 仅适用于生成 Windows 2000 或更高版本计算机。 如果生成 ATL 项目并想使用 /robust，请在 dlldatax.c 文件中更改此行：

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

有关如何访问 MIDL 文件夹中“高级”属性页的信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

有关如何以编程方式访问 C++ 项目的 MIDL 选项的详细信息，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。

## <a name="see-also"></a>请参阅

[“MIDL”属性页](../ide/midl-property-pages.md)