---
title: 运行时对象模型服务 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6fb948efd63a8392661cc38a80393bc90d5e694
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396438"
---
# <a name="run-time-object-model-services"></a>运行时对象模型服务

类[CObject](../../mfc/reference/cobject-class.md)并[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封装多个对象服务，包括对运行时类信息、 序列化和动态对象创建的访问。 所有派生自 `CObject` 的类都继承此功能。

能够访问运行时类信息可让您在运行时确定有关对象的类的信息。 当需要对函数自变量进行额外的类型检查以及必须基于对象的类编写专用代码时很有用，能够在运行时确定对象的类很有用。 C++ 语言不直接支持运行时类信息。

序列化是在文件中写入或读取对象内容的过程。 当应用程序退出后，可以使用序列化来存储对象的内容。 对象随后可在应用程序重新启动时从文件中读取。 此类数据对象被称为“永久对象”。

动态对象创建支持在运行时创建指定类的对象。 例如，文档、视图和框架对象必须支持动态创建，因为框架需要以动态方式创建这些内容。

下表列出了支持运行时类信息、序列化和动态创建的 MFC 宏。

这些运行时对象服务和序列化的详细信息，请参阅文章[CObject 类： 访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。

### <a name="run-time-object-model-services-macros"></a>运行时对象模型服务宏



|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|支持访问运行时类信息（必须在类声明中使用）。|
|[DECLARE_DYNCREATE](#declare_dyncreate)|支持动态创建和访问运行时类信息（必须在类声明中使用）。|
|[DECLARE_SERIAL](#declare_serial)|支持序列化和访问运行时类信息（必须在类声明中使用）。|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|支持访问运行时类信息（必须在类实现中使用）。|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|支持动态创建和访问运行时类信息（必须在类实现中使用）。|
|[IMPLEMENT_SERIAL](#implement_serial)|允许序列化和访问运行时类信息（必须在类实现中使用）。|
|[RUNTIME_CLASS](#runtime_class)|返回与命名类对应的 `CRuntimeClass` 结构。|


OLE 通常要求在运行时动态创建对象。 例如，OLE 服务器应用程序必须能够动态创建 OLE 项以响应来自客户端的请求。 同样，自动化服务器必须能够创建项以响应来自自动化客户端的请求。

Microsoft 基础类库提供了两个特定于 OLE 的宏。

### <a name="dynamic-creation-of-ole-objects"></a>OLE 对象的动态创建








|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|确定公共控件库是否实现了指定的 API。|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|确定公共控件库是否实现了指定的 API。|
|[DECLARE_OLECREATE](#declare_olecreate)|支持通过 OLE 自动化创建对象。|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|声明`GetUserTypeNameID`和`GetMiscStatus`控件类的成员函数。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|声明 OLE 控件提供了一系列属性页以显示其属性。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|支持由 OLE 系统创建对象。|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|实现`GetUserTypeNameID`和`GetMiscStatus`控件类的成员函数。|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|任一此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)使用任何类在实现文件中必须出现`DECLARE_OLECREATE`。 |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

确定公共控件库是否实现了指定的 API。

### <a name="syntax"></a>语法

  ```
AFX_COMCTL32_IF_EXISTS(  proc );
```
### <a name="parameters"></a>参数

*进程内*<br/>
指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。

### <a name="remarks"></a>备注

使用此宏可确定公共控件库函数指定是否*proc* (而不是调用[GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212)。

### <a name="requirements"></a>要求

afxcomctl32.h，afxcomctl32.inl

### <a name="see-also"></a>请参阅

[隔离 MFC 公用控件库](../isolation-of-the-mfc-common-controls-library.md)<br/>
[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)

## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2

确定公共控件库是否实现指定的 API (这是 Unicode 版本[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists))。

### <a name="syntax"></a>语法

```
AFX_COMCTL32_IF_EXISTS2( proc );
```
### <a name="parameters"></a>参数

*进程内*<br/>
指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。

### <a name="remarks"></a>备注

使用此宏可确定公共控件库函数指定是否*proc* (而不是调用[GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212)。 此宏是 AFX_COMCTL32_IF_EXISTS 的 Unicode 版本。

### <a name="requirements"></a>要求

afxcomctl32.h，afxcomctl32.inl

### <a name="see-also"></a>请参阅

[隔离 MFC 公用控件库](../isolation-of-the-mfc-common-controls-library.md)<br/>
[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC

添加了派生的类从时访问有关对象的类的运行时信息的功能`CObject`。

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

将 DECLARE_DYNAMIC 宏添加到的标头 (.h) 模块的类，然后在需要访问此类的对象的所有.cpp 模块中包含该模块。

如果您使用 DECLARE_ 动态和 IMPLEMENT_DYNAMIC 宏，如所述，您可以使用 RUNTIME_CLASS 宏和`CObject::IsKindOf`函数，用于在运行时确定对象的类。

如果 DECLARE_DYNAMIC 包含在类声明，则必须在类实现中包含 IMPLEMENT_DYNAMIC。

DECLARE_DYNAMIC 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

有关示例，请参阅[IMPLEMENT_DYNAMIC](#implement_dynamic)。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE

使对象的`CObject`的派生类，以在运行时动态创建。

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

框架使用此功能来动态创建新对象。 例如，新创建的视图时打开一个新文档。 文档、 视图和框架类应支持动态创建，因为框架需要动态地创建它们。

对于类，.h 模块中添加 DECLARE_DYNCREATE 宏，然后在需要访问此类的对象的所有.cpp 模块中包含该模块。

如果 DECLARE_DYNCREATE 包含在类声明，则必须在类实现中包含 IMPLEMENT_DYNCREATE。

DECLARE_DYNCREATE 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

> [!NOTE]
>  DECLARE_DYNCREATE 宏包括 DECLARE_DYNAMIC 的所有功能。

### <a name="example"></a>示例

有关示例，请参阅[IMPLEMENT_DYNCREATE](#implement_dyncreate)。

### <a name="requirements"></a>要求

**标头：** afx.h


## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE

声明`GetUserTypeNameID`和`GetMiscStatus`控件类的成员函数。

### <a name="syntax"></a>语法

```
DECLARE_OLECTLTYPE( class_name )
```
### <a name="parameters"></a>参数

*class_name*<br/>
控件类的名称。

### <a name="remarks"></a>备注

`GetUserTypeNameID` 并`GetMiscStatus`是纯虚拟函数，在声明`COleControl`。 因为这些函数是纯虚拟的必须重写这些控件类中。 除了 DECLARE_OLECTLTYPE，您必须将 IMPLEMENT_OLECTLTYPE 宏添加到控件类声明中。

### <a name="requirements"></a>要求

**标头：** afxctl.h

### <a name="see-also"></a>请参阅

[IMPLEMENT_OLECTLTYPE](#implement_olectltype)


## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS

声明 OLE 控件提供了一系列属性页以显示其属性。

### <a name="syntax"></a>语法

```
DECLARE_PROPPAGEIDS( class_name )
```
### <a name="parameters"></a>参数

*class_name*<br/>
拥有属性页的控件类的名称。

### <a name="remarks"></a>备注

使用`DECLARE_PROPPAGEIDS`宏在类声明的末尾。 然后，在.cpp 文件中定义类的成员函数，使用`BEGIN_PROPPAGEIDS`宏，宏项为每个控件的属性页和`END_PROPPAGEIDS`宏声明属性页列表的末尾。

属性页的详细信息，请参阅文章[ActiveX 控件： 属性页](../mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>要求

**标头：** afxctl.h

### <a name="see-also"></a>请参阅

[BEGIN_PROPPAGEIDS](#begin_proppageids)<br/>
[END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>  DECLARE_SERIAL

生成所需的 c + + 标头代码`CObject`-派生可序列化的类。

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

序列化是从文件写入或读取与对象的内容的过程。

在.h 模块中使用 DECLARE_SERIAL 宏，然后将该模块包含在需要访问此类的对象的所有.cpp 模块。

如果 DECLARE_SERIAL 包含在类声明，则必须在类实现中包含 IMPLEMENT_SERIAL。

DECLARE_SERIAL 宏包括 DECLARE_DYNAMIC 和 DECLARE_DYNCREATE 的所有功能。

您可以使用 AFX_API 宏自动导出`CArchive`提取运算符使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类。 方括号用下面的代码的类声明 （位于.h 文件）：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

DECLARE_SERIAL 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC

生成为动态所必需的 c + + 代码`CObject`-派生的类名称和位置在层次结构中的类的运行时访问。

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的名称。

### <a name="remarks"></a>备注

在.cpp 模块中，使用 IMPLEMENT_DYNAMIC 宏，然后仅一次链接生成的对象代码。

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE

使对象的`CObject`的派生类，以在运行时动态创建与 DECLARE_DYNCREATE 宏一起使用时的时间。

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的实际名称。

### <a name="remarks"></a>备注

框架使用此功能来创建新对象动态，例如，当在序列化期间从磁盘读取的对象。 类实现文件中添加 IMPLEMENT_DYNCREATE 宏。 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

如果使用 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE 宏，则可以使用 RUNTIME_CLASS 宏和`CObject::IsKindOf`成员函数以在运行时确定对象的类。

如果 DECLARE_DYNCREATE 包含在类声明，则必须在类实现中包含 IMPLEMENT_DYNCREATE。

请注意，此宏的定义将调用您的类的默认构造函数。 如果由类显式实现重要的构造函数，它必须显式实现的默认构造函数。 默认构造函数可以添加到类的**私有**或**保护**成员部分，以防止它从外部类实现中调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS

任一此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必须出现的任何类都使用 DECLARE_OLECREATE 在实现文件中。

### <a name="syntax"></a>语法

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)

```
### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

*external_name*<br/>
对其他应用程序 （用引号引起来） 公开的对象名称。

*nFlags*<br/>
包含一个或多个下列标志：

   - `afxRegInsertable` 允许要在 OLE 对象的插入对象对话框中显示的控件。
   - `afxRegApartmentThreading` ThreadingModel 注册表中设置线程模型 = 单元。
   - `afxRegFreeThreading` ThreadingModel 注册表中设置线程模型 = 免费。

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/desktop/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4**b5*， *b6*， *b7*， *b8*类的 CLSID 的组件。

### <a name="remarks"></a>备注

> [!NOTE]
>  如果使用 IMPLEMENT_OLECREATE_FLAGS，则可以指定通过使用支持您的对象的线程模型*nFlags*参数。 如果你想要支持仅单线程模型，使用 IMPLEMENT_OLECREATE。

外部名称是向其他应用程序公开的标识符。 客户端应用程序使用的外部名称请求自动化服务器中的此类的对象。

OLE 类 ID 是对象的唯一 128 位标识符。 它包含一个**长**、 两个**WORD**s 和八个**字节**s，由表示*l*， *w1*， *w2*，并*b1*通过*b8*语法说明中。 应用程序向导和代码向导根据需要为你创建唯一 OLE 类 Id。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

### <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)<br/>
[DECLARE_OLECREATE](#declare_olecreate)<br/>
[CLSID 项](/windows/desktop/com/clsid-key-hklm)


## <a name="implement_olecreate"></a> IMPLEMENT_OLECTLTYPE

实现`GetUserTypeNameID`和`GetMiscStatus`控件类的成员函数。

### <a name="syntax"></a>语法

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```
### <a name="parameters"></a>参数

*class_name*<br/>
控件类的名称。

*idsUserTypeName*<br/>
包含控件的外部名称的字符串资源 ID。

*dwOleMisc*<br/>
一个枚举，包含一个或多个标志。 此枚举的详细信息，请参阅[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) Windows SDK 中。

### <a name="remarks"></a>备注

除了 IMPLEMENT_OLECTLTYPE，您必须将 DECLARE_OLECTLTYPE 宏添加到控件类声明中。

`GetUserTypeNameID`成员函数将返回用于标识你的控件类的资源字符串。 `GetMiscStatus` 返回控件的 OLEMISC 位。 此枚举指定描述控件的其他特征的设置的集合。 OLEMISC 设置的完整说明，请参阅[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) Windows SDK 中。

> [!NOTE]
>  使用 ActiveX 控件向导的默认设置是： OLEMISC_ACTIVATEWHENVISIBLE、 OLEMISC_SETCLIENTSITEFIRST、 OLEMISC_INSIDEOUT、 OLEMISC_CANTLINKINSIDE 和 OLEMISC_RECOMPOSEONRESIZE。

### <a name="requirements"></a>要求

**标头：** afxctl.h

### <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)<br/>
[DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL

生成为动态所必需的 c + + 代码`CObject`-派生的类名称和位置在层次结构中的类的运行时访问。

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的名称。

*wSchema*<br/>
一个 UINT"版本号"，将存档后，若要启用的反序列化程序，确定并处理所创建的数据中编码前面程序版本。 类架构数字不能为-1。

### <a name="remarks"></a>备注

在.cpp 模块; 中使用 IMPLEMENT_SERIAL 宏然后仅一次链接生成的对象代码。

您可以使用 AFX_API 宏自动导出`CArchive`提取运算符使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类。 方括号用下面的代码的类声明 （位于.h 文件）：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="runtime_class"></a>  RUNTIME_CLASS

获取运行时类结构从 c + + 类的名称。

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
（未用引号括起来） 类的实际名称。

### <a name="remarks"></a>备注

RUNTIME_CLASS 返回一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)指定的类结构*class_name*。 仅`CObject`-使用 DECLARE_DYNAMIC、 DECLARE_DYNCREATE 或 DECLARE_SERIAL 声明派生的类将返回指向`CRuntimeClass`结构。

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE

使对象的`CCmdTarget`的派生类，以通过 OLE 自动化创建。

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

此宏使其他 OLE 启用应用程序创建此类型的对象。

对于类，.h 模块中添加 DECLARE_OLECREATE 宏，然后将该模块包含在需要访问此类的对象的所有.cpp 模块。

如果 DECLARE_OLECREATE 包含在类声明，则必须在类实现中包含 IMPLEMENT_OLECREATE。 DECLARE_DYNCREATE 或 DECLARE_SERIAL，还必须使用使用 DECLARE_OLECREATE 类声明。

### <a name="requirements"></a>要求

**标头**: afxdisp.h

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE

任一此宏或[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)使用任何类在实现文件中必须出现`DECLARE_OLECREATE`。

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类的实际名称。

*external_name*<br/>
对其他应用程序 （用引号引起来） 公开的对象名称。

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4**b5*， *b6*， *b7*， *b8*类的 CLSID 的组件。

### <a name="remarks"></a>备注

> [!NOTE]
>  如果您使用 IMPLEMENT_OLECREATE，默认情况下，您将支持单线程模型。 如果使用 IMPLEMENT_OLECREATE_FLAGS，则可以指定通过使用支持您的对象的线程模型*nFlags*参数。

外部名称是向其他应用程序公开的标识符。 客户端应用程序使用的外部名称请求自动化服务器中的此类的对象。

OLE 类 ID 是对象的唯一 128 位标识符。 它包含一个**长**、 两个**WORD**s 和八个**字节**s，由表示*l*， *w1*， *w2*，并*b1*通过*b8*语法说明中。 应用程序向导和代码向导根据需要为你创建唯一 OLE 类 Id。

### <a name="requirements"></a>要求

**标头**: afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

