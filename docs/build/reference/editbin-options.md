---
title: EDITBIN 选项
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820099"
---
# <a name="editbin-options"></a>EDITBIN 选项

可以使用 EDITBIN 来修改对象文件、 可执行文件或动态链接库 (Dll)。 选项指定 EDITBIN 做的更改。

选项包括选项说明符，短划线 （-） 或正斜杠 （/） 后, 跟的选项的名称。 不能缩写选项名称。 某些选项带参数，参数在冒号 (:) 后指定。 中的选项规范允许空格或制表符。 使用一个或多个空格或制表符分隔命令行上的选项规范。 选项名及其关键字自变量或文件名自变量不区分大小写。 例如，-bind 和 /BIND 意义完全相同。

EDITBIN 提供以下选项：

|选项|目标|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|指定一个 DLL 是否可以绑定。|
|[/ALLOWISOLATION](allowisolation.md)|指定 DLL 或可执行文件清单查找行为。|
|[/APPCONTAINER](appcontainer.md)|指定应用是否必须在 AppContainer 内运行 — 例如，UWP 应用。|
|[/BIND](bind.md)|将指定对象中的入口点地址设为速度加载时间。|
|[/DYNAMICBASE](dynamicbase.md)|使用地址空间布局随机化 (ASLR) 功能，指定是否可在加载时随机重新设定 DLL 或可执行图像的基址。|
|[/ERRORREPORT](errorreport-editbin-exe.md)|向 Microsoft 报告内部错误。|
|[/HEAP](heap.md)|以字节设置可执行映像堆的大小。|
|[/HIGHENTROPYVA](highentropyva.md)|指定 DLL 或可执行映像是否支持高熵（64 位）地址空间布局随机化 (ASLR)。|
|[/INTEGRITYCHECK](integritycheck.md)|指定是否在加载时检查数字签名。|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|指定对象是否支持大于 2 GB 的地址。|
|[/NOLOGO](nologo-editbin.md)|取消显示 EDITBIN 启动横幅。|
|[/NXCOMPAT](nxcompat.md)|指定可执行映像是否与 Windows 数据执行保护兼容。|
|[/REBASE](rebase.md)|设置指定对象的基址。|
|[/RELEASE](release.md)|在标头中设置校验和。|
|[/SECTION](section-editbin.md)|重写节的特性。|
|[/STACK](stack.md)|以字节设置可执行映像栈的大小。|
|[/SUBSYSTEM](subsystem.md)|指定执行环境。|
|[/SWAPRUN](swaprun.md)|指定可执行图像必须复制到交换文件，然后从其中运行。|
|[/TSAWARE](tsaware.md)|指定应用可在多用户环境中运行。|
|[/VERSION](version.md)|在标头中设置版本号。|

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
[EDITBIN 参考](editbin-reference.md)
