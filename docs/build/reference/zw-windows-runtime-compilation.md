---
title: /ZW（Windows 运行时编译）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: 297697d215a78cbf1aefef30df53f6956c4e16b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629757"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW（Windows 运行时编译）

编译源代码以支持 Visual c + + 组件扩展 C + + /cli CX 用于创建通用 Windows 平台 (UWP) 应用程序。

当你使用 **/ZW**进行编译，始终指定 **/EHsc**也。

## <a name="syntax"></a>语法

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>自变量

**nostdlib**<br/>
指示 Platform.winmd、Windows.Foundation.winmd 以及其他默认 Windows 元数据 (.winmd) 文件未自动包含在该编译中。 相反，必须使用[/FU (命名强制 #using 文件)](../../build/reference/fu-name-forced-hash-using-file.md)编译器选项显式指定 Windows 元数据文件。

## <a name="remarks"></a>备注

当指定 **/ZW**选项，编译器支持以下功能：

- 必需的元数据文件、 命名空间、 数据类型和您的应用程序所需的用于 Windows 运行时中执行的函数。

- Windows 运行时对象的引用计数和自动丢弃该对象，其引用计数归零时自动。

由于增量链接器不支持通过使用包含在.obj 文件中的 Windows 元数据 **/ZW**选项， [/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)选项与不兼容 **/ZW**.

有关详细信息，请参阅[Visual c + + 语言参考](../../cppcx/visual-c-language-reference-c-cx.md)。

## <a name="requirements"></a>要求

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)