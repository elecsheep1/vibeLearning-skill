# 知识框架图 / 思维导图

---

## 输出格式

思维导图默认生成 **XMind 格式**（`.xmind`），使用 Python 脚本打包：
- `content.json`：topic 节点树，每个节点包含 `id`, `class: "topic"`, `title`, 可选 `children.attached`
- `metadata.json`：创建者与创建日期
- `manifest.json`：文件清单
- 以上三个文件打包为 ZIP，后缀名 `.xmind`

生成脚本需输出到 `$CLAUDE_JOB_DIR/tmp/generate_xmind.py` 并执行。

---

## XMind content.json 节点结构

```json
{
  "id": "unique-id",
  "class": "topic",
  "title": "节点标题",
  "children": {
    "attached": [
      { "id": "...", "class": "topic", "title": "子节点1" },
      { "id": "...", "class": "topic", "title": "子节点2" }
    ]
  }
}
```

根 sheet 结构：
```json
[{
  "id": "sheet-id",
  "class": "sheet",
  "title": "Sheet 标题",
  "rootTopic": { ... }
}]
```

---

## 辅助函数模板（Python）

```python
import json, zipfile, os, uuid

def make_topic(title, children=None):
    topic = {"id": uuid.uuid4().hex[:10], "class": "topic", "title": title}
    if children:
        topic["children"] = {"attached": children}
    return topic

def generate_xmind(output_path, root_title, build_tree_fn):
    root_topic = build_tree_fn()
    sheet = [{"id": uuid.uuid4().hex[:10], "class": "sheet", "title": root_title, "rootTopic": root_topic}]
    metadata = {"creator": {"name": "Claude Code", "version": "1.0"}, "created": "YYYY-MM-DD"}
    manifest = {"file-entries": {"content.json": {}, "metadata.json": {}}}
    with zipfile.ZipFile(output_path, 'w', zipfile.ZIP_DEFLATED) as zf:
        zf.writestr('content.json', json.dumps(sheet, ensure_ascii=False, indent=2))
        zf.writestr('metadata.json', json.dumps(metadata, ensure_ascii=False, indent=2))
        zf.writestr('manifest.json', json.dumps(manifest, ensure_ascii=False, indent=2))
```

---

## 配套 markdown 大纲

`.xmind` 用于可视化浏览，同时生成 markdown 结构化大纲（嵌套列表）作为文本版，方便 grep/搜索/版本控制。
