<!doctype html>
<html lang="zh-cn">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1,shrink-to-fit=no">
    <title>{{ .Site.Title }}</title>
    <link rel="stylesheet" href="/main.css">
    <style>
        body { margin:0; padding:0; min-height:100vh; display:flex; flex-direction:column; font-family:-apple-system,sans-serif; }
        header { position:fixed; top:0; left:0; right:0; height:80px; z-index:9999; border-bottom:1px solid rgba(0,0,0,6%); background-color:rgba(255,255,255,.9); backdrop-filter:blur(10px); }
        .nav-container { max-width:720px; height:100%; margin:0 auto; display:flex; align-items:center; justify-content:space-between; padding:0 24px; box-sizing:border-box; }
        
        /* 1. 搜索框：直接显示在导航栏 */
        .search-wrapper { display: flex; align-items: center; background: rgba(0,0,0,0.05); border-radius: 20px; padding: 5px 12px; }
        .search-box { background: transparent; border: none; font-size: 13px; width: 120px; outline: none; }

        /* 2. Timeline：在大屏显示，手机端隐藏以防乱跳 */
        .sidebar-archive { position:absolute; left:calc(100% + 50px); top:0; width:120px; }
        @media(max-width: 1150px) { .sidebar-archive { display: none !important; } }

        /* 3. 文章摘要：点击折叠效果 */
        .post-item { margin-bottom: 3rem; }
        details { border: 1px solid rgba(0,0,0,0.05); padding: 12px; border-radius: 8px; }
        summary { cursor: pointer; color: #007aff; font-size: 14px; font-weight: 500; list-style: none; }
        summary::-webkit-details-marker { display: none; }
        .post-summary { margin-top: 10px; line-height: 1.6; opacity: 0.8; }
    </style>
</head>

<body class="dark:bg-black dark:text-white">
    <header class="dark:bg-black/90 dark:border-white/10">
        <div class="nav-container">
            <a href="/" style="text-decoration:none;color:inherit;font-weight:700;font-size:1.1rem;">Ben Thinking</a>
            <nav style="display:flex;gap:15px;align-items:center">
                <div class="search-wrapper">
                    <input type="text" id="search-input" class="search-box" placeholder="搜索...">
                </div>
                <a href="/wiki" style="text-decoration:none;color:inherit;font-size:14px;opacity:.6">Wiki</a>
                <a href="/about" style="text-decoration:none;color:inherit;font-size:14px;opacity:.6">关于</a>
            </nav>
        </div>
    </header>

    <main style="flex:1;width:100%;max-width:720px;margin:120px auto 0;padding:0 24px;position:relative;box-sizing:border-box">
        <aside class="sidebar-archive">
            <h3 style="font-size:11px;opacity:.3;text-transform:uppercase;margin-bottom:16px;letter-spacing:1.5px">Timeline</h3>
            <ul style="list-style:none;padding:0;margin:0;font-size:13px;opacity:.5">
                <li><a href="/" style="text-decoration:none;color:inherit">2026</a></li>
                <li><a href="/" style="text-decoration:none;color:inherit">2025</a></li>
                <li><a href="/" style="text-decoration:none;color:inherit">2024</a></li>
            </ul>
        </aside>

        <div class="post-list">
            {{ range .Paginator.Pages }}
            <div class="post-item">
                <h2 style="margin-bottom:.5rem;font-size:1.5rem">
                    <a href="{{ .Permalink }}" style="text-decoration:none;color:inherit">{{ .Title }}</a>
                </h2>
                <div style="opacity:.5;font-size:.9rem;margin-bottom:1rem">{{ .Date.Format "2006-01-02" }}</div>
                
                <details>
                    <summary>▶ 展开阅读摘要</summary>
                    <div class="post-summary">
                        {{ .Summary }}
                        <p><a href="{{ .Permalink }}" style="color:#007aff;text-decoration:none;">查看全文 →</a></p>
                    </div>
                </details>
            </div>
            {{ end }}
        </div>
    </main>
</body>
</html>