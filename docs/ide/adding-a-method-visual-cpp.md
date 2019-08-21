---
title: 添加方法
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: b0c8ddabc4ed08fd217545bad269f0b2e48dd49e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509536"
---
# <a name="add-a-method"></a>添加方法

可以使用[添加方法向导](#add-method-wizard)，向项目中的接口添加方法。 如果项目包含与接口有关的类，向导也会修改此类。

**向对象添加方法：**

1. 在“类视图”中，展开项目节点，显示想要向其添加方法的接口  。

   > [!NOTE]
   > 也可以向位于库节点下的调度接口添加方法（除非该项目已特性化）。

1. 右键单击接口的名称。

1. 在快捷菜单中，选择“添加”，然后选择“添加方法”   。

1. 在添加方法向导中，提供创建方法的信息。

1. 在向导的 [IDL 特性](#idl-attributes-add-method-wizard)页中，为此方法指定任何接口定义语言设置。

1. 选择“完成”以添加方法  。

## <a name="in-this-section"></a>本节内容

- [添加方法向导](#add-method-wizard)
- [IDL 特性，添加方法向导](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>添加方法向导

使用此向导可将方法添加到接口。 根据要添加方法的项目类型或接口类型，向导显示不同的选项。

### <a name="names"></a>名称

- **返回类型**

  该方法返回的数据类型。 建议将 `HRESULT` 用于所有接口类型，因为它提供返回错误的标准方式。

  |接口类型|说明|
  |--------------------|-----------------|
  |双重接口|`HRESULT`。 不可更改。|
  |自定义接口|`HRESULT`。 不可更改。|
  |本地自定义接口|提供自己的返回类型或从列表中选择。|
  |调度接口|提供自己的返回类型或从列表中选择。|
  |MFC ActiveX 控件调度接口|如果实现常用方法，则返回类型将设置为适当的值且不可更改。 如果从“方法名”列表中选择方法，并选择了“选择方法类型”下的“自定义”，请从列表中选择返回类型    。|

- **方法名**

  设置方法的名称。

  |接口类型|说明|
  |--------------------|-----------------|
  |ATL 双重接口、自定义接口和本地自定义接口|提供自己的方法名。|
  |MFC 调度接口|提供自己的方法名或从列表中选择建议的方法名。 如果从列表中选择名称，则相应的值将显示在“返回类型”框中，并且不可更改  。|
  |MFC ActiveX 控件调度接口|提供自己的方法或选择 [DoClick](../mfc/reference/colecontrol-class.md#doclick) 和 [Refresh](../mfc/reference/colecontrol-class.md#refresh) 常用方法中的任意一种。 有关详细信息，请参阅 [MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。|

- **方法类型**

  仅适用于 MFC ActiveX 控件。 如果在“方法名”框中提供方法名，而不是从列表中选择方法，则此框不可用  。

  如果在“方法名”列表中选择其中一种方法，请选择常用实现或自定义实现  。

  |方法类型|说明|
  |-----------------|-----------------|
  |**常用**|默认值。 插入在“方法名”列表中所选方法的常用实现  。 如果选择“常用”，则“返回类型”不可更改   。|
  |**自定义**|插入在“方法名”列表中所选方法的存根实现  。 对于自定义方法类型，可提供自己的返回类型，也可从“返回类型”列表中选择一种类型  。|

- **内部名称**

  仅适用于添加到 MFC 调度接口的自定义方法。 设置用于调度映射、头 (.h) 文件和实现 (.cpp) 文件的名称。 默认情况下，此名称与“方法名”相同  。 如果正在使用 MFC 调度接口或正在将自定义方法添加到 MFC ActiveX 控件调度接口，则可更改方法名。

  |接口类型|说明|
  |--------------------|-----------------|
  |ATL 双重接口、自定义接口和本地自定义接口|不可用。|
  |MFC 调度接口|默认设置为方法名。 可编辑内部名称。|
  |MFC ActiveX 控件调度接口|仅能为自定义方法设置内部名称。 常用方法不使用内部名称。|

- **参数属性**

  为“参数名称”中指定的参数设置任何其他属性  。

  |参数属性|说明|允许的组合|
  |-------------------------|-----------------|--------------------------|
  |**In**|指示参数将从调用过程传递到被调用过程。|仅 `in`<br /><br /> `in` 和 `out`|
  |**Out**|指示从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|仅 `out`<br /><br /> `in` 和 `out`<br /><br /> `out` 和 `retval`|
  |**Retval**|指示接收该成员的返回值的参数。|`retval` 和 `out`|

- **参数类型**

  设置参数的数据类型。 从列表中选择类型。

- **参数名称**

  设置要通过方法传递的参数名称。 键入名称后，选择“添加”以将其添加到参数列表（参数通过方法进行传递）  。 如果未提供参数名称，向导会忽略任何参数属性（仅限 ATL）或“参数类型”选项  。

  选择“添加”后，参数名称随即显示在“参数列表”中   。

  > [!NOTE]
  > 如果提供参数名称，且随后在选择“添加”前先选择“完成”，则不会将该参数添加到方法中   。 必须找到该方法并手动插入参数。

- **添加**

  将在“参数名称”中指定的参数及其类型和参数属性添加到“参数列表”中   。 选择“添加”可向列表添加参数  。

- **移除**

  从列表中删除在“参数列表”中选择的参数  。

- **参数列表**

  显示当前为该方法添加的所有参数及其修饰符和类型。 添加参数时，向导更新“参数列表”以显示每个参数及其修饰符和类型  。

## <a name="idl-attributes-add-method-wizard"></a>IDL 特性，添加方法向导

使用“添加方法向导”的此页为方法指定任何接口定义语言 (IDL) 设置。

- `id`

  设置标识方法的数字 ID。 有关详细信息，请参阅 MIDL 参考中的 [ID](/windows/win32/Midl/id)  。

  此框不可用于自定义接口和 MFC 调度接口。

- `call_as`

  指定此本地方法可映射到的远程方法的名称。 有关详细信息，请参阅 MIDL 参考中的 [call_as](/windows/win32/Midl/call-as)  。

  不可用于 MFC 调度接口。

- `helpcontext`

  指定一个上下文 ID，让用户可以在帮助文件中查看此方法的相关信息。 有关详细信息，请参阅 MIDL 参考中的 [helpcontext](/windows/win32/Midl/helpcontext)  。

  不可用于 MFC 调度接口。

- `helpstring`

  指定一个字符串，用于描述该字符串适用的元素。 该字符串默认设置为“method Method name”  。 有关详细信息，请参阅 MIDL 参考中的 [helpstring](/windows/win32/Midl/helpstring)  。

  不可用于 MFC 调度接口。

- **附加特性**

  不可用于 MFC 调度接口。

  |特性|说明|
  |---------------|-----------------|
  |`hidden`|指示该方法虽然存在，但不应在面向用户的浏览器中显示。 有关详细信息，请参阅 MIDL 参考中的 [hidden](/windows/win32/Midl/hidden)  。|
  |`source`|指示方法的一个成员是事件源。 有关详细信息，请参阅 MIDL 参考中的 [source](/windows/win32/Midl/source)  。|
  |`local`|向 MIDL 编译器指出该方法不是远程的。 有关详细信息，请参阅 MIDL 参考中的 [local](/windows/win32/Midl/local)  。|
  |`restricted`|指定此方法不能任意调用。 有关详细信息，请参阅 MIDL 参考中的 [restricted](/windows/win32/Midl/restricted)  。|
  |`vararg`|指定方法采用的参数数目可变。 为了实现这一点，最后一个参数必须是包含其余参数的 `VARIANT` 类型的安全数组。 有关详细信息，请参阅 MIDL 参考中的 [vararg](/windows/win32/Midl/vararg)  。|
