# SCBL Hooks build

SCBL 的 Windows x86 Hooks DLL 与 Linux dedicated server 均由本仓库统一编译。

`Build SCBL 5th binaries` 工作流在 `main` 的 Hooks、dedicated server 或相关依赖发生变化时执行，并将校验后的滚动二进制发布到 `scbl-public-stable-latest`。

SCBL 客户端仓库不再保存 Hooks 源码或预编译 DLL；构建时从本仓库 Release 或指定分支的 GitHub Actions Artifact 下载并校验。
