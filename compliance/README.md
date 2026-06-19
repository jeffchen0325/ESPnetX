# Compliance / Third-Party Licenses

## ⚠️ 核心原则
- `third-party-licenses/` 目录内容由 `copy_license.sh` **自动生成**。
- **禁止手动修改**归档内容（包括 LICENSE 文件和 provenance.txt）。
- 所有依赖的新增、更新、删除必须通过修改脚本配置并重新执行来完成。

## 🛠️ 新增/更新依赖标准操作流程 (SOP)

### 1. 修改依赖配置
编辑 `copy_license.sh` 中的 `DEPENDENCIES` 数组，按 `"name|version|tag|url"` 格式添加或修改条目：
```bash
DEPENDENCIES=(
  "espnet|202604|v.202604|https://github.com/espnet/espnet"
  "new-package|1.0.0|v1.0.0|https://github.com/org/new-package"  # 新增示例
)
```

### 2. 执行归档脚本
```bash
bash compliance/copy_license.sh
```

### 3. 验证与提交
- 检查终端输出的 Summary 确认无失败项。
- 使用 `git diff compliance/third-party-licenses/` 审查变更是否符合预期。
- 将 `copy_license.sh` 与 `third-party-licenses/` 的变更在**同一个 commit** 中提交，确保配置与产物始终同步。