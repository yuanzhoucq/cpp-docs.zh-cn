---
title: "运行时对象模型服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8739201489644b0f1695a70d0dc12d04ca47aa68
ms.lasthandoff: 02/24/2017

---
# <a name="run-time-object-model-services"></a>运行时对象模型服务
这些类[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封装几个对象服务，包括对运行时类信息、 序列化和动态对象创建的访问。 所有派生自 `CObject` 的类都继承此功能。  
  
 能够访问运行时类信息可让您在运行时确定有关对象的类的信息。 当需要对函数参数进行额外的类型检查以及必须基于对象的类编写专用代码时很有用，能够在运行时确定对象的类很有用。 C++ 语言不直接支持运行时类信息。  
  
 序列化是在文件中写入或读取对象内容的过程。 当应用程序退出后，可以使用序列化来存储对象的内容。 对象随后可在应用程序重新启动时从文件中读取。 此类数据对象被称为“永久对象”。  
  
 动态对象创建支持在运行时创建指定类的对象。 例如，文档、视图和框架对象必须支持动态创建，因为框架需要以动态方式创建这些内容。  
  
 下表列出了支持运行时类信息、序列化和动态创建的 MFC 宏。  
  
 这些运行时对象服务和序列化的详细信息，请参阅文章[CObject 类︰ 访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。  
  
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
|[DECLARE_OLECREATE](#declare_olecreate)|支持通过 OLE 自动化创建对象。|  
|[IMPLEMENT_OLECREATE](#implement_olecreate)|支持由 OLE 系统创建对象。|  
  
##  <a name="a-namedeclaredynamica--declaredynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC  
 添加了能够访问的对象类相关的运行时信息，当从派生类`CObject`。  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 添加`DECLARE_DYNAMIC`宏到标头 (.h) 模块的类，然后将该模块包含在需要访问此类的对象的所有.cpp 模块。  
  
 如果您使用**DECLARE**_**动态**和`IMPLEMENT_DYNAMIC`宏所述，然后，可以使用`RUNTIME_CLASS`宏和`CObject::IsKindOf`函数来在运行时确定对象的类。  
  
 如果`DECLARE_DYNAMIC`包含在类声明中，然后`IMPLEMENT_DYNAMIC`必须包含在类实现。  
  
 有关详细信息`DECLARE_DYNAMIC`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[IMPLEMENT_DYNAMIC](#implement_dynamic)。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-namedeclaredyncreatea--declaredyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE  
 支持的对象`CObject`的派生类，以在运行时动态创建。  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 框架将使用此功能以动态方式创建新对象。 例如，新创建的视图时打开一个新文档。 文档、 视图和框架类应支持动态创建，因为框架需要以动态方式创建它们。  
  
 添加`DECLARE_DYNCREATE`宏在.h 模块中的类，然后将该模块包含在需要访问此类的对象的所有.cpp 模块。  
  
 如果`DECLARE_DYNCREATE`包含在类声明中，然后`IMPLEMENT_DYNCREATE`必须包含在类实现。  
  
 有关详细信息`DECLARE_DYNCREATE`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
> [!NOTE]
>  `DECLARE_DYNCREATE`宏包含的所有功能`DECLARE_DYNAMIC`。  
  
### <a name="example"></a>示例  
 请参阅示例[IMPLEMENT_DYNCREATE](#implement_dyncreate)。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-namedeclareseriala--declareserial"></a><a name="declare_serial"></a>DECLARE_SERIAL  
 生成所需的 c + + 标头代码`CObject`-派生可序列化的类。  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 序列化是一个文件中写入或读取与对象的内容的过程。  
  
 使用`DECLARE_SERIAL`宏在.h 模块，然后将该模块包含需要访问此类的对象的所有.cpp 模块中。  
  
 如果`DECLARE_SERIAL`包含在类声明中，然后`IMPLEMENT_SERIAL`必须包含在类实现。  
  
 `DECLARE_SERIAL`宏包含的所有功能`DECLARE_DYNAMIC`和`DECLARE_DYNCREATE`。  
  
 您可以使用**AFX_API**宏来自动导出`CArchive`提取运算符的类使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏。 方括号 （位于.h 文件） 替换为以下代码的类声明︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 有关详细信息`DECLARE_SERIAL`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&21;](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameimplementdynamica--implementdynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC  
 生成为动态所必需的 c + + 代码`CObject`的派生类的运行时访问的类名称和层次结构中的位置。  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的名称。  
  
### <a name="remarks"></a>备注  
 使用`IMPLEMENT_DYNAMIC`a.cpp 模块，然后链接只有一次代码生成的对象中的宏。  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&2;](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample #&3;](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameimplementdyncreatea--implementdyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE  
 支持的对象`CObject`的派生类，以在运行时动态创建时间与一起使用时`DECLARE_DYNCREATE`宏。  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的实际名称。  
  
### <a name="remarks"></a>备注  
 框架将使用此功能以动态方式创建新对象，例如，在序列化期间从磁盘读取某个对象时。 添加`IMPLEMENT_DYNCREATE`类实现文件中的宏。 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
 如果您使用`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`宏，然后，可以使用`RUNTIME_CLASS`宏和`CObject::IsKindOf`成员函数以在运行时确定对象的类。  
  
 如果`DECLARE_DYNCREATE`包含在类声明中，然后`IMPLEMENT_DYNCREATE`必须包含在类实现。  
  
 请注意，此宏的定义将调用您的类的默认构造函数。 如果由类显式实现非普通构造函数，它还可以显式必须实现的默认构造函数。 默认构造函数可以添加到类的**专用**或**保护**成员部分，以防止它被从外部类实现调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&22;](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample 第&23;](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameimplementseriala--implementserial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL  
 生成为动态所必需的 c + + 代码`CObject`的派生类的运行时访问的类名称和层次结构中的位置。  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的名称。  
  
 *wSchema*  
 一个**UINT** "版本号"将在启用反序列化程序用于标识和处理所创建的数据的存档中编码前面程序版本。 类架构数字不能 â €"1。  
  
### <a name="remarks"></a>备注  
 使用`IMPLEMENT_SERIAL`.cpp 模块; 中的宏然后一次只能将链接生成的对象代码。  
  
 您可以使用**AFX_API**宏来自动导出`CArchive`提取运算符的类使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏。 方括号 （位于.h 文件） 替换为以下代码的类声明︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&24;](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameruntimeclassa--runtimeclass"></a><a name="runtime_class"></a>RUNTIME_CLASS  
 获取运行时类结构从 c + + 类的名称。  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 （未用引号引起来） 类的实际名称。  
  
### <a name="remarks"></a>备注  
 `RUNTIME_CLASS`返回一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)指定的类结构*class_name*。 仅`CObject`的派生类用声明`DECLARE_DYNAMIC`， `DECLARE_DYNCREATE`，或`DECLARE_SERIAL`将返回指向`CRuntimeClass`结构。  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&25;](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 
   
##  <a name="a-namedeclareolecreatea--declareolecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE  
 支持的对象`CCmdTarget`的派生类，以通过 OLE 自动化创建。  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 此宏使其他 OLE 启用应用程序创建此类型的对象。  
  
 添加`DECLARE_OLECREATE`宏在.h 模块中的类，然后将该模块包含需要访问此类的对象的所有.cpp 模块中。  
  
 如果`DECLARE_OLECREATE`包含在类声明中，然后`IMPLEMENT_OLECREATE`必须包含在类实现。 类声明使用`DECLARE_OLECREATE`还必须使用`DECLARE_DYNCREATE`或`DECLARE_SERIAL`。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h  

##  <a name="a-nameimplementolecreatea--implementolecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE  
 任一此宏或[IMPLEMENT_OLECREATE_FLAGS](http://msdn.microsoft.com/library/d1589f6a-5a69-4742-b07c-4c621cfd040d)必须出现在使用任何类的实现文件`DECLARE_OLECREATE`。  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 *external_name*  
 向其他应用程序 （用引号引起来） 公开的对象名称。  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 类的组件**CLSID**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果您使用`IMPLEMENT_OLECREATE`，默认情况下，支持单线程模型。 如果您使用`IMPLEMENT_OLECREATE_FLAGS`，您可以指定通过使用支持您的对象的线程模型`nFlags`参数。  
  
 外部名称是向其他应用程序公开的标识符。 客户端应用程序使用的外部名称从自动化服务器请求此类的一个对象。  
  
 OLE 类 ID 是该对象的唯一 128 位标识符。 它包含一个**长**，两个**WORD**s 和八个**字节**s，由表示*l*， *w1*， *w2*，和*b1*通过*b8*语法说明中。 应用程序向导和代码向导根据需要为你创建唯一的 OLE 类 Id。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h 

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

