# Octave 控制系统工具箱

这是GNU Octave官方控制系统工具箱的代码仓库，本人汉化。
## 项目简介

**控制系统工具箱**是用于控制系统设计与分析的函数集合。

自2023年3月24日起，该工具箱的开发已从[SourceForge](https://sourceforge.net/p/octave/control/ci/default/tree/)平台和[Mercurial](https://en.wikipedia.org/wiki/Mercurial) 迁移至 [GitHub](https://github.com/gnu-octave/pkg-control)和[Git](https://en.wikipedia.org/wiki/Git)。

相关链接：
- [版权许可信息](https://github.com/gnu-octave/pkg-control/blob/main/COPYING)
- [版本发布](https://github.com/gnu-octave/pkg-control/releases)
- [文档](https://gnu-octave.github.io/pkg-control)

## SLICOT库的使用

本工具箱使用了[SLICOT-Reference库](https://github.com/SLICOT/SLICOT-Reference)（版权所有 (c) 2020, SLICOT）中的部分例程。这些例程的源代码已包含在发布的`control-x.y.z.tar.gz`压缩包的`src/slicot-src`目录中，在安装过程中会针对目标系统进行编译。

SLICOT文件遵循*BSD 3-Clause License*，您可以通过以下方式查看：

- 在`control-x.y.z.tar.gz`压缩包的`src/slicot-src/LICENSE`文件中（附有README说明）
- 在安装目录的`doc/SLICOT/LICENSE`文件中（附有README说明）
- 或在 [SLICOT-Reference代码库](https://github.com/SLICOT/SLICOT-Reference/blob/main/LICENSE)中查看。

## 安装控制系统工具箱

###安装正式发布版本

最简单的安装方式是执行命令：

  `pkg install -forge control`

您也可以从[发布页面](https://github.com/gnu-octave/pkg-control/releases)下载`control-x.y.z.tar.gz`压缩包后执行：

  `pkg install control-x.y.z.tar.gz`

### 手动构建安装包

您也可以克隆此代码库（由于包含SLICOT作为git子模块，需使用`--recurse-submodules`选项），然后自行构建软件包归档文件。具体可使用以下命令：
- `make dist`<br>
  在`target`目录下创建可供Octave后续安装的软件包归档文件
- `make install`<br>
  安装该软件包
- `make help`<br>
  显示`make`的所有可用目标

## 参与贡献

关于如何参与control软件包开发的贡献指南，请参阅[文档](CONTRIBUTING.md)。