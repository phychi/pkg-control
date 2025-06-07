# 如何贡献

## 贡献方式

有多种方式可以帮助改进GNU Octave的**control**扩展包。

### 完善文档

如果您发现某个函数或功能的帮助文本存在缺失、错误、不完整或难以理解的情况，可以通过提交修改来帮助我们解决问题。关于使用[Texinfo](https://www.gnu.org/software/texinfo/)格式编写帮助文本，请参阅[许可与文档](#许可与文档)部分。

### 报告与修复错误

GNU Octave及其扩展包的缺陷和功能请求都在[Github](https://github.com/gnu-octave/pkg-control/issues)上跟踪。欢迎您着手修复问题或协助测试。修复补丁可以附加在问题评论中，或者更推荐的方式是在扩展包仓库中发起拉取请求（参见[贡献流程](#贡献流程)）。如需报告新错误，请先查阅现有问题以避免重复提交。

### 参与讨论

如有任何关于扩展包改进或扩展的问题建议，欢迎加入[GNU Octave社区论坛](https://octave.discourse.group/)的讨论。

## 许可与文档

**control**扩展包遵循[GNU General Public License (GPL)](https://www.gnu.org/licenses/gpl-3.0.en.html)分发（使用的SLICOT文件除外）。提交新函数时需包含以下GPLv3+许可声明（请替换具体年份、姓名等信息）：

```bash
## Copyright (C) YEAR NAME <E-MAIL>
##
## This file is part of the statistics package for GNU Octave.
##
## Octave is free software; you can redistribute it and/or modify it
## under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 3 of the License, or
## (at your option) any later version.
##
## Octave is distributed in the hope that it will be useful, but
## WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License
## along with Octave; see the file COPYING.  If not,
## see <http://www.gnu.org/licenses/>.

```

新函数或功能应使用[Texinfo](https://www.gnu.org/software/texinfo/)格式编写嵌入式帮助文档。该部分应置于函数主体之外（之前），且位于许可声明之后。Texinfo手册可参考[此处](https://www.gnu.org/software/texinfo/manual/texinfo/)，但阅读现有函数文件也能快速掌握格式要求。

```bash
## -*- texinfo -*-
## @deftypefn {Function File} {} pzmap (@var{sys})
##
## Help file goes here.
##
## @end deftypefn
```

Texinfo内容不会直接显示在命令窗口中。

## 编码规范

### 通用规则

应遵循[GNU OctaveWiki](https://wiki.octave.org/Octave_style_guide)中的通用编码规范，并补充以下要求：
- 单行长度不超过80个字符
- 使用`LF`（Unix）换行符，而非`CRLF`（Windows）

### 测试

建议在函数文件末尾添加测试用例，测试行以`%!`开头。以下是`pzmap()`的测试示例：

```
%!test
%! s = tf('s');
%! g = (s-1)/(s-2)/(s-3);
%! [pol zer] = pzmap(g);
%! assert(sort(pol), [2 3]', 2*eps);
%! assert(zer, 1, eps);
```

### 演示案例

虽然函数文档中应包含使用示例，但嵌入可交互的演示案例也很有价值，用户可通过`demo`命令调用：

```
>> demo pzmap
```

演示代码同样置于文件末尾，以下是`pzmap()`的演示示例：

```
%!demo
%! s = tf('s');
%! g = (s-1)/(s-2)/(s-3);
%! pzmap(g);
```

## 贡献流程

与其他开源项目类似，贡献control扩展包的常规流程为：
1. 复刻代码仓库（fork the repository）
2. 在复刻的仓库中进行修改（如修复错误或添加新功能）
3. 向原始仓库发起拉取请求

具体操作可参考[Github协作指南](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests)。

### 复刻与构建

首先[复刻](https://github.com/gnu-octave/pkg-control/fork)pkg-control仓库到您的账户，然后克隆该仓库。构建可安装扩展包的方法请参考[README](README.md)文件。

### 发起拉取请求（Pull request）

完成修改后，将变更提交并推送到您复刻的Github仓库（确保复刻仓库是最新状态），然后创建拉取请求。

### 小修改的快捷方式

若变更较小且仅涉及单个文件，可直接在Github网页界面编辑文件，选择"提交更改"并"为此提交创建新分支以发起拉取请求"。

Your contribution must be an independent work or derived from code that may be released under the terms of the GPL. **Under no circumstances may it be based on code from Matlab or other non-free code that you may have access to view**.

### Fork and build

[Fork](https://github.com/gnu-octave/pkg-control/fork) the pkg-control repository to your own account and clone the resulting repository. Refer to the [README](README.md) file for information about how to build the package archive which can be installed in GNU Octave.

### Pull request

When your changes are finished, commit and push the change to your forked repository on Github (make sure your fork is up to date) and create a pull request.

### Option for very small changes

If the changes are small and only affect one file, you can make the changes directly in the web interface of Github, select *Commit changes* and *Create a new branch for this commit and start a pull request*.
