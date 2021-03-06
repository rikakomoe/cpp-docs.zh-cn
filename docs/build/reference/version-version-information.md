---
title: /VERSION（版本信息）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 3e24a5307b8c4f60f29de390d38d9694f1cacf29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529679"
---
# <a name="version-version-information"></a>/VERSION（版本信息）

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>自变量

*主要*和*次要*<br/>
所需的.exe 或.dll 文件的标头中的版本号。

## <a name="remarks"></a>备注

/VERSION 选项告知链接器将版本号置于.exe 或.dll 文件的标头中。 使用 DUMPBIN [/HEADERS](../../build/reference/headers.md)若要查看的映像版本字段的可选的标头值，若要查看 /VERSION 的效果。

*主要*并*次要*参数是十进制数字 0 到 65,535 范围内的。 默认值为版本 0.0。

使用 /VERSION 指定的信息不影响您在文件资源管理器中查看应用程序属性时为应用程序显示的版本信息。 该版本信息来自用于生成应用程序的资源文件。 请参阅[版本信息编辑器](../../windows/version-information-editor.md)有关详细信息。

要插入的版本号的另一种方法是使用[版本](../../build/reference/version-c-cpp.md)模块定义语句。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**常规**属性页。

1. 修改**版本**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)