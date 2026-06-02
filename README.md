# 满班名额图片生成工具

这是一个可部署到 Netlify 的静态网页版本。

## 更新数据

修改 `teacher-team.xlsx` 或 `满班名额模板1.pptx` 后，运行：

```powershell
python scripts/build_static_site.py
```

脚本会生成：

- `static_site/assets/teachers.json`
- `static_site/assets/avatars/*.png`
- `static_site/assets/template-bg.png`
- `static_site/index.html`

## 本地预览

可以用任意静态服务器打开 `static_site`，例如：

```powershell
python -m http.server 8765 -d static_site
```

然后访问：

```text
http://127.0.0.1:8765
```

## Netlify

项目根目录已有 `netlify.toml`：

```toml
[build]
  publish = "static_site"
```

提交到 GitHub 后，在 Netlify 连接仓库即可。构建命令可留空，发布目录为 `static_site`。

## 说明

Netlify 不能运行 Windows PowerPoint COM，所以此版本只保留 PNG 图片导出，不再生成 PPTX。图片由浏览器 Canvas 合成。
