<!doctype html>
<html lang="zh-cn">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1,shrink-to-fit=no">
    <title>{{ .Site.Title }}</title>
    <link rel="stylesheet" href="/main.css">
    <style>
        body { margin:0; padding:0; min-height:100vh; display:flex; flex-direction:column; font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif; transition: background 0.3s; }
        header { position:fixed; top:0; left:0; right:0; height:80px; z-index:9999; border-bottom:1px solid rgba(0,0,0,6%); background-color:rgba(255,255,255,.9); backdrop-filter:blur(10px); }
        .nav-container { max-width:720px; height:100%; margin:0 auto; display:flex; align-items:center; justify-content:space-between; padding:0 24px; box-sizing:border-box; }
        
        /* 搜索框样式 */
        .search-wrapper { position: relative; display: flex; align-items: center; }
        .search-box { background: rgba(0,0,0,0.05); border: none; padding: 7px 15px; border-radius: 20px; font-size: 13px; width: 140px; outline: none; transition: all 0.3s; }
        .search-box:focus { width: 200px; background: rgba(0,0,0,0.08); box-shadow: 0 0 0 2px rgba(0,122,255,0.1); }

        /* Timeline 侧边栏：大屏显示，手机隐藏 */
        .sidebar-archive { position:absolute; left:calc(100% + 50px); top:0; width:120px; }
        @media(max-width: 1150px) { .sidebar-archive { display: none !important; } }

        /* 文章摘要折叠样式 */
        .post-item { margin-bottom: 3.5rem; }
        .post-item h2 { margin-bottom: 0.5rem; font-size: 1.6rem; font-weight: 700; }
        details { border: 1px solid rgba(0,0,0,0.05); padding: 15px; border-radius: 12px; transition: all 0.2s; }
        details[open] { background: rgba(0,0,0,0.02); }
        summary { cursor: pointer; color: #007aff; font-size: 14px; font-weight: 500; outline: none; list-style: none; }
        summary::-webkit-details-marker { display: none; }
        .post-summary { margin-top: 12px; line-height: 1.7; opacity: 0.85; font-size: 15px; }
    </style>
</head>

<body class="dark:bg-black dark:text-white">
    <header class="dark:bg-black/90 dark:border-white/10">
        <div class="nav-container">
            <a href="/" style="text-decoration:none;color:inherit;font-weight:800;font-size:1.2rem;">Ben Thinking</a>
            <nav style="display:flex;gap:20px;align-items:center">
                <div class="search-wrapper">
                    <input type="text" id="search-input" class="search-box" placeholder="搜索文章...">
                </div>
                <a href="/wiki" style="text-decoration:none;color:inherit;font-size:14px;opacity:.7">Wiki</a>
                <a href="/about" style="text-decoration:none;color:inherit;font-size:14px;opacity:.7">关于</a>
            </nav>
        </div>
    </header>

    <main style="flex:1;width:100%;max-width:720px;margin:120px auto 0;padding:0 24px;position:relative;box-sizing:border-box">
        <aside class="sidebar-archive">
            <h3 style="font-size:11px;opacity:.3;text-transform:uppercase;margin-bottom:16px;letter-spacing:1.5px">Timeline</h3>
            <ul style="list-style:none;padding:0;margin:0;font-size:13px;opacity:.5;line-height:2">
                <li><a href="/" style="text-decoration:none;color:inherit">2026</a></li>
                <li><a href="/" style="text-decoration:none;color:inherit">2025</a></li>
                <li><a href="/" style="text-decoration:none;color:inherit">2024</a></li>
            </ul>
        </aside>

        <div class="post-list">
            {{ range .Paginator.Pages }}
            <div class="post-item">
                <h2><a href="{{ .Permalink }}" style="text-decoration:none;color:inherit">{{ .Title }}</a></h2>
                <div style="opacity:.4;font-size:0.85rem;margin-bottom:1.2rem">{{ .Date.Format "2006-01-02" }}</div>
                
                <details>
                    <summary>展开摘要 (查看5句话简介) ↓</summary>
                    <div class="post-summary">
                        {{ .Summary }}
                        <p style="margin-top:15px;"><a href="{{ .Permalink }}" style="color:#007aff;text-decoration:none;font-weight:600;">阅读全文 →</a></p>
                    </div>
                </details>
            </div>
            {{ end }}
        </div>
    </main>

    <footer style="width:100%;margin-top:80px;padding:60px 0;opacity:.3;font-size:12px;text-align:center;border-top:1px solid rgba(0,0,0,0.05);">
        &copy; 2026 Ben Thinking
    </footer>
</body>
</html>