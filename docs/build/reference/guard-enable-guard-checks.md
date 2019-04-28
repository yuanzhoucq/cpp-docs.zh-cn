---
title: /GUARD（启用防护检查）
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: e48921e57977cc7a1ca6a580fed78a6a2a960a02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292245"
---
# <a name="guard-enable-guard-checks"></a>/GUARD（启用防护检查）

在可执行映像中，为控制流防护检查指定支持。

## <a name="syntax"></a>语法

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>备注

当指定 /GUARD:CF 时，链接器将修改 .dll 或 .exe 的标头，以指示支持控制流防护 (CFG) 运行时检查。 链接器还会将所需的控制流目标地址数据添加到标头。 默认情况下，禁用 /GUARD:CF。 可以通过使用 /GUARD:NO 显式禁用。 为提高效率，/guard: cf 还需要[/DYNAMICBASE （使用地址空间布局随机化）](dynamicbase-use-address-space-layout-randomization.md)链接器选项，默认情况下。

通过使用编译源代码时[/guard: cf](guard-enable-control-flow-guard.md)选项，该编译器可以分析通过检查对可能目标地址的所有间接调用的控制流。 编译器将插入代码，以验证间接调用指令的目标地址在运行时是否处于已知的目标地址列表中。 支持 CFG 的操作系统将停止未能通过 CFG 运行时检查的程序。 这提高了攻击者使用数据损坏来更改调用目标，以执行恶意代码的难度。

必须对编译器和链接器指定 /GUARD:CF 选项，以创建支持 CFG 的可执行映像。 编译但未使用 /GUARD:CF 链接的代码会产生运行时检查开销，但不会启用 CFG 保护。 如果为指定 /guard: cf 选项`cl`命令来编译和链接在一个步骤中，编译器将标志传递给链接器。 当**控制流防护**属性设置在 Visual Studio 中，对编译器和链接器传递 /guard: cf 选项。 该选项时单独编译对象文件或库，必须显式指定在`link`命令。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 展开**配置属性**，**链接器**，**命令行**。

1. 在中**其他选项**，输入`/GUARD:CF`。

## <a name="see-also"></a>请参阅

[/guard（启用控制流保护）](guard-enable-control-flow-guard.md)<br/>
[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
